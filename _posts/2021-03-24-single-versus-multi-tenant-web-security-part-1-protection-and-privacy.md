---
layout: post
title: 'Single- versus Multi-Tenant Web Security, Part 1: Protection and Privacy'
canonical_url: 'https://www.reblaze.com/blog/single-versus-multi-tenant-web-security-part-1-protection-and-privacy/'
description: Most commercial web security solutions are based on a multi-tenant architecture. Curiefense is single-tenant; here's why this is important, and the advantages that this architecture provides.
published: true
excerpt: Most commercial web security solutions are based on a multi-tenant architecture. Curiefense is single-tenant; here's why this is important, and the advantages that this architecture provides.
createdOn: Wed Mar 24 2021 18:42:00 GMT+0000 (Coordinated Universal Time)
author: Spiros Psarris
mainImage: "/images/multi-tenant-p-2000.jpg"
thumbnail: "/images/multi-tenant-p-2000.jpg"
redirect_from:
- "/post/single-versus-multi-tenant-web-security-part-1-protection-and-privacy"
---
Web application security continues to be challenging for many organizations today. According to [Edgescan][1]’s 2020 Vulnerability Statistics Report, 27% of internet-facing assets have at least one CVE (Common Vulnerability and Exposure) with a CVSS score of 7.0 or more. Meanwhile, the direct and indirect costs of successful exploits are high. In 2020, for example, the average cost to an enterprise of a data breach was [$3.92 million][2]. And the annual global cost of cybercrime is expected to reach [$6 trillion][3] in 2021. Organizations, therefore, must pay close attention to the security of their web applications and services.

A robust web security solution has to address many layers, from threat detection and access control to DDoS protection, API security, and bot detection. The architecture of the solution also has an impact on its effectiveness and performance.

Most commercial web security solutions are based on a multi-tenant architecture. This article is the first of a two-part series about the problems and challenges inherent in this approach, and how these issues are avoided by a single-tenant structure. In this article, we focus on the security and privacy advantages of the single-tenant model, while in the second part, we’ll look at its performance benefits.

## **Typical Multi-Tenant Web Security Architecture**
As shown in Figure 1, a typical web security architecture diverts user traffic to a multi-tenant scrubbing center, where data packets are decrypted in order to be checked for possible security threats. The scrubbed user traffic is then re-encrypted and routed to the origin server hosting the application. The external scrubbing center may be deployed in the cloud or in an on-premises data center.

<div align="center">
  <img width="80%" src="/images/multi-tenant-1-1024x576.jpg" /><br>
  <em>Figure 1: Typical multi-tenant web security architecture</em>
</div>

## **Multi-Tenant Web Security Challenges**
The multi-tenant web security architecture illustrated in Figure 1 exposes the web application owner to several security challenges, as described below.

### **Data Exposure**
In the multi-tenant web security model, data is decrypted and processed by the security solution vendor outside of the environment of the customer, i.e., the web application owner. Vendor software bugs or admin errors could open the door to unauthorized access to a fellow tenant’s data, or accidentally return data to the wrong tenant.

The months-long [Cloudbleed][4] incident in 2017 is a classic example. Cloudflare provides CDN and hosting services for internet sites. An error in Cloudflare’s code allowed sensitive user data from one website to be randomly inserted into pages served by other sites. This included highly sensitive information such as encryption keys, cookies, and passwords, much of which was publicly cached by search engines. The vulnerability was already five months old when discovered, and later estimates were that the bug was triggered 1.2 million times and affected thousands of websites. This highlights the risks incurred when data is processed by a multi-tenant solution.

### **Denial of Service**
[Reblaze][5], along with [other security companies][6], has seen an increase in the frequency and severity of DDoS attacks. With malicious traffic coming from multiple distributed sources around the globe, it’s almost impossible for regular firewalls and intrusion detection systems to thwart an attack.

Yet another risk of the multi-tenant security model is that a DDoS attack on one tenant can affect the other tenants sharing that infrastructure. This is exactly what happened to a certain high-profile ecommerce site when they were using a popular multi-tenant security solution. A massive DDoS attack on a fellow tenant’s website brought down their site as well, creating a terrible dilemma: to absorb significant financial losses from the downtime, or to disconnect temporarily from the third-party security service and come back online without protection. (After this incident, they sought a different provider, and they are now satisfied customers of a single-tenant solution.)

### **Compliance**
Data protection and data privacy regulations, such as the General Data Protection Regulations (GDPR) enacted by the European Union in May 2018, apply not only to the direct data controller but to all third-party service providers (known as data processors) that are given access to the data. In other words, not only does the organization collecting the data have to be GDPR-compliant, but also all of the suppliers and partners that store, process, or otherwise “touch” the data.

As you can see in Figure 1, a multi-tenant security solution routes user data through its external infrastructure before re-routing it back to the customer’s environment. Most industries and regulators allow a multi-tenant solution if the vendor can show compliance. However, for sectors where data privacy is paramount, such as banking, insurance, and healthcare to name just a few, the multi-tenant security solution could be considered a weak link in their data governance chain.

## **What a Single-Tenant Web Security Architecture Looks Like**
A single-tenant web security architecture ensures that an organization’s traffic is only filtered within the customer’s environment.

<div align="center">
  <img width="80%" src="/images/single-tenant-1024x576.jpg" /><br>
  <em>Figure 2: Single-tenant web security architecture </em>
</div>

For example, [Curiefense][7] runs within the customer’s service mesh. Data packets from users are decrypted once, and the scrubbed traffic goes directly to the destination within the same environment.

All processing takes place within the privacy of the customer’s perimeter. This ensures maximum protection, and avoids the disadvantages of a multi-tenant architecture:

* Sensitive data can never be served with that of other tenants, nor is it potentially vulnerable to exposure through shared infrastructure such as management or reporting consoles.
* The customer is never exposed to DDoS attacks directed at other organizations.
* There is no additional data governance, and therefore no potential compliance issues.

## **Conclusion**
In summary, a multi-tenant web security solution running outside of the customer’s environment can make web applications vulnerable to data exposure, downtime from DDoS attacks that target fellow tenants, and weak links in their data governance chain. These vulnerabilities are eliminated when the web security solution is single-tenant, running within the customer’s perimeter.

In the next article, we’ll compare other aspects of multi-tenant and single-tenant web security, including protection, performance, and cost.

[1]:	https://www.edgescan.com/
[2]:	https://www.csoonline.com/article/3153707/top-cybersecurity-facts-figures-and-statistics.html
[3]:	https://cybersecurityventures.com/top-5-cybersecurity-facts-figures-predictions-and-statistics-for-2019-to-2021/#:~:text=1%20cyber%2Dattacked%20industry%20%E2%80%94%20will,fastest%20growing%20type%20of%20cybercrime.
[4]:	https://www.reblaze.com/blog/important-lesson-cloudbleed/
[5]:	https://www.reblaze.com/
[6]:	https://securityintelligence.com/articles/avoid-ddos-attacks/
[7]:	https://curiefense.io/