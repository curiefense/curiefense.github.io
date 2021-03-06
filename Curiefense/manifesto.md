---
layout: default
title: 'Curiefense Manifesto'
description: 'The goals and design principles behind Curiefense, the open-source security extension for Envoy.'
---

<div class="section manifesto">
  <div class="container w-container">
    <div class="row w-row">
      <div class="w-col w-col-8 w-col-stack">
        <div class="item-vertical level-one first">
          <h3>Manifesto</h3>
          <h2 class="heading-3">Curiefense Manifesto</h2>
          <div class="item-vertical">
            <p>We live in a world where the range of cyberattacks is ever expanding, and the threats&#x27; severity escalates exponentially with the sheer volume of data processed daily across the Internet. Attackers evolve rapidly, perfecting their tools and techniques, and demonstrating unprecedented capabilities; thus, collaboration is the most promising way to build a better, more comprehensive, simpler, transparent and scalable security solution.<br><br>Our goal is to provide the ultimate cloud-native application security: a platform that is open, extensible, adaptive and evolving, while maintaining total privacy.<br><br>Below are the main principles of Curiefense: our goals for its design, development, and maintenance.</p>
          </div>
          <div class="item-vertical">
            <h4 class="heading-4">Adaptive and evolving</h4>
            <p>A key foundational goal for the project is its ability to adapt to the threat environment, by combining external data sources and insights extracted from internal events. This requires a continuous feedback loop of data analysis at various levels, from models based on simple statistics to advanced detection models based on machine learning clustering and classification.</p>
          </div>
          <div class="item-vertical">
            <h4 class="heading-4">Cloud Native</h4>
            <p>The cloud-native compute movement is one of the most exciting and fast-moving communities in the tech industry. We want to ensure our project evolves with it, and remains fully compatible with new protocols and technologies as they are introduced. Modern cloud-native deployments face an ever escalating series of threats, and tight integration with other OSS projects such as Kubernetes and Envoy will lead to better security outcomes.</p>
          </div>
          <div class="item-vertical">
            <h4 class="heading-4">Collaboration (community driven)</h4>
            <p>Open source software and open standards have proven to surpass proprietary technology by all measures; they are the turbine behind the exponential growth of the Internet. Security is a critical aspect of running an online platform, and it deserves the best tools possible; therefore, open source is a better choice than a closed, proprietary &quot;patented&quot; one. Collaboration with the vast communities of Envoy, Kubernetes, and other cloud native products will bring in opinions and ideas from some of the brightest minds, and will improve the product and its performance.</p>
          </div>
          <div class="item-vertical">
            <h4 class="heading-4">Technology-First Governance</h4>
            <p>Curiefense takes a technology-first approach: we encourage individuals, teams, and companies to build, extend, improve, adjust, and alter the platform according to their needs and preferences. Every layer and every aspect of Curiefense, from connectivity and functionality to detection and management tools, is built with developers and engineers in mind, and therefore operates by API.Our API is simple to use and easy to understand. We want our users to be able to do things quickly and reliably, and we will maintain these principles as we continue to add new features and capabilities.<br></p>
          </div>
          <div class="item-vertical">
            <h4 class="heading-4">Transparency</h4>
            <p>For software and data, transparency is not merely good; it is a <em>must</em>. We believe you should be able to fully understand how things actually work, and where your data is stored. Your vendor should not be able to decide what you can know, and what you can???t; this is your decision alone.</p>
          </div>
          <div class="item-vertical">
            <h4 class="heading-4">Comprehensive</h4>
            <p>Since the foundation of Reblaze back in 2011, we have believed in building a complete solution that covers all sorts of threats in a single unified product. This ensures all mechanisms and engines are in sync across the board, from allow-listing and profiling to violations and anomalies. There is no single routine or mechanism that can solve all problems and protect against all threats; different threats require different protective mechanisms, and they must be able to share state and data, adjust together to changes in the threat environment, and so on. To be most effective, an application security product should incorporate all mechanisms: WAF, ACL, rate limiting, bot and human detection, and others.</p>
          </div>
          <div class="item-vertical">
            <h4 class="heading-4">Private</h4>
            <p>When using Curiefense, all data is processed, stored and analyzed inside your perimeter. You do not share private SSL keys with any third party, and requests &amp; responses to your platform are not saved by an external vendor (or even worse, processed in a shared environment). <br><br>It saddens us that some companies don???t mind having their data processed, decrypted, and logged by a third party in a shared environment???and that they are doing all this in the name of &quot;security&quot;. Imagine setting up a private, well-designed VPC with everything tightly secured (ports and security groups restricting access, etc.)... then in order to add a security mechanism, you must route your traffic through a third party that acts as a reverse proxy, and uses private keys to decrypt, process, and log your data in a shared infrastructure. <br><br>This makes no sense. With Curiefense, you get all those benefits and more, with zero compromises on privacy and security.</p>
          </div>
          <div class="item-vertical">
            <h4 class="heading-4">Fast</h4>
            <p>In security, speed matters: a system that detects a risk immediately can protect against it immediately. A traditional security solution includes an external resource (whether cloud or data center), which adds DNS routing and dozens or even hundreds of milliseconds of additional latency???plus the traffic decryption, inspection, analysis, and re-encryption time. <br><br>This overhead can lead to users who compromise on their level of security in order to retain performance. We believe that the best approach is to place security right after decryption takes place, inside your perimeter, which minimizes overhead latency to a matter of microseconds.</p>
          </div>
          <div class="item-vertical">
            <h4 class="heading-4">Scalable</h4>
            <p>Curiefense???s design and modularity takes scalability into account at all stages (systems, subsystems, ??and services). Its design is well-tested, and runs today in our clients&#x27; environments; these range from a few millions of requests per day to several billions. <br><br>Scalability works both ways, upwards and downwards: we scale ???upwards??? to ensure the system performs well and keeps its responsiveness, speed and stability, and then ???downwards??? when traffic volume goes down, to ensure there are no wasted resources.</p>
          </div>
          <div class="item-vertical">
            <h4 class="heading-4">Simple</h4>
            <p>Simplicity is a vital ingredient in security. Complex systems tend to be abandoned, and complicated processes tend to be avoided. Even worse, a complicated system can be misconfigured, leading to an illusion of security when in fact there are vulnerabilities. <br><br>Our goal is to keep Curiefense effective and simple to use, whether it is an API call, UI interaction, automation procedure, or a foundational concept. Simplicity boosts participation and promotes action. We will always choose to work harder to keep it as simple as possible, regardless of the complexity beneath the surface.</p>
          </div>
        </div>
      </div>
      <div class="w-col w-col-4 w-col-stack"></div>
    </div>
  </div>
</div>