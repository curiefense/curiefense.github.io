---
layout: post
title: 'Evaluating logging tools, choosing rotatelogs'
canonical_url: 'https://www.reblaze.com/blog/evaluating-logging-tools-for-curiefense/'
description: As discussed previously, version 1.4 will include some changes to logging. Some of them created a file management problem. We evaluated several options for log file rotation; here’s what we chose, and why.
published: true
excerpt: As discussed previously, version 1.4 will include some changes to logging. Some of them created a file management problem. We evaluated several options for log file rotation; here’s what we chose, and why.
createdOn: Wed May 26 2021 03:48:00 GMT+0000 (Coordinated Universal Time)
author: Flavio Percoco
mainImage: "/images/Evaluating_logging_tools,_choosing_rotatelogs.png"
thumbnail: "/images/Evaluating_logging_tools,_choosing_rotatelogs.png"
permalink: /blog/:title/
---
A previous post discussed some [upcoming changes to logging in Curiefense version 1.4][1]. The **curielogger** service is being refactored; instead of sending log data directly to multiple collectors (logstash, fluentd, elasticsearch, etc.), it will be writing its data to stdout. Then users can select their preferred method of collecting the data and importing into their logging solution of choice.

We want to make this as easy as possible for users. So for example, to support elasticsearch, we added (into Curiefense’s Helm charts) the ability to deploy [filebeat][2] as a sidecar container in the curielogger pod. In an elasticsearch deployment, curielogger will write to a file, from which filebeat will gather the data and send it all to elasticsearch. 

However, this creates a file management problem. In a Kubernetes environment, or some other environment that doesn’t have proper log rotation, curielogger will always write its logs to the same file. This means the file will grow forever, until there’s no more space on the disk.

To solve this, we considered, and rejected, several options:

* Using logrotate (more on this below).
* [multilog][3] doesn’t do well with logs that are over 2kb (which ours are).
* svlogd could work, but it would require creating a configuration file in the log folder. An init script or entrypoint.sh would be needed.
* Feeding filebeat something other than files would prevent json parsing.

## Choosing, and then rejecting, logrotate 
Our initial approach was to try logrotate. At first, it seemed to work well. However, when a rotation occurs, logrotate removes the file that curielogger had been writing to. From that point forward, curielogger won’t log anything else, because its file descriptor would point to a name and location that are no longer valid. This breaks the workflow, obviously. 

We could have enabled logrotate’s truncate option, but that has the risk of losing (or duplicating) logs. This is discussed in detail in [Elastic’s documentation][4].

## Choosing, and then keeping, rotatelogs
To solve this problem, we switched to [rotatelogs][5], which handles these cases better. It gets all the logs from stdin, and then assumes all the responsibility for writing the logs to a file.

In this configuration, curielogger is not writing directly to a file anymore. It just pipes the data to rotatelogs, and then rotatelogs will write everything to the files that filebeat will read. This solves the problem, because rotatelogs is doing all the writing; it knows where the files are, it knows when the current file is going to be moved, and so on. So it takes care of this entire logic for us.

## Impact to Users
These changes will be part of version 1.4. The impact to users will be minimal: just a few additional steps in the deployment process, for which we will provide appropriate Helm charts.

And speaking of Curiefense’s Helm charts, a related change is that we have created a separate repository for them. There are several reasons for this, and several benefits for doing so; we’ll discuss them in an upcoming post.

[1]: https://www.curiefense.io/blog/changes-to-logging-in-version-1.4/
[2]: https://www.elastic.co/beats/filebeat
[3]: https://cr.yp.to/daemontools/multilog.html
[4]: https://www.elastic.co/guide/en/beats/filebeat/current/file-log-rotation.html
[5]: https://httpd.apache.org/docs/2.4/programs/rotatelogs.html

