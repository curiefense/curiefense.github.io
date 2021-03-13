---
layout: default
title: "About Us | The team behind Curiefense"
description: "Curiefense is an open source project that adds web security to Envoy Proxy. Here is its mission and the people behind it."
---

  <div class="wrapper">
    <div class="section product-team">
      <div class="container w-container">
        <div class="row flex-vertical w-row">
          <div class="row w-col w-col-11">
            <div class="item-vertical level-one">
              <h3 class="heading-2">Our Story</h3>
              <h1 class="heading-3">Our Mission</h1>
              <p class="paragraph hero-paragraph">We live in a world where the range of cyberattacks is ever expanding, and the severity escalates exponentially with the sheer volume of data processed daily across the Internet. <br><br>Attackers evolve rapidly, perfecting their tools and techniques, and demonstrating unprecedented capabilities; thus, collaboration is the most promising way to build a better, more comprehensive, simpler, transparent and scalable security solution.<br><br>Our mission is to provide the ultimate cloud-native application security: a platform that is open, extensible, adaptive and evolving, while maintaining total privacy.<a href="manifesto"> read our manifesto &gt;&gt;</a><br></p>
            </div>
          </div>
          <div class="no-paddings w-col w-col-1">
            <div class="hero-image"></div>****
          </div>
        </div>
        <div class="item-vertical">
          <div class="item-vertical">
            <h1 class="heading-3">The Team</h1>
          </div>
          <div class="w-layout-grid people-grid smaller">
          {% for member in site.data.team-members %}
            <div id="w-node-_2e17a88a-a2a7-9ea3-09b8-78a22d8b9580-31274adf" class="person-box">
              <div class="person-box-image smaller">
                <img src="{{member.imageSrc}}" loading="lazy" width="146" sizes="(max-width: 479px) 85vw, (max-width: 767px) 86vw, 90vw" srcset="{{member.imageSrcSet}}" alt="" class="person-img" />
              </div>
              <div class="person-box-name">{{member.name}}<br>{{member.company}}</div>
              <div class="person-box-title">{{member.title}}</div>
              {% if member.linkedInProfileLink != "" and member.linkedInProfileLink != nil %}
                <p class="paragraph person-bio">
                  <a href="{{member.linkedInProfileLink}}" target="_blank">LinkedIn</a>
                </p>
              {% endif %}
            </div>
          {% endfor %}
          </div>
        </div>
      </div>
    </div>
    <div class="section footer">
      <div class="container w-container">
        <div class="w-row">
          <div class="w-col w-col-4"><img src="images/curie-01.svg" width="147" alt="">
            <div class="footer-description">
              <p class="paragraph">Curiefense is named in honor of the famous scientist <a href="marie-curie" target="_blank">Marie Curie</a>. The first version was developed in Malakoff, France, a few hundred meters from her home and laboratory. Curiefense was originally created by <a href="https://www.reblaze.com/" target="_blank">Reblaze</a>.<br></p>
            </div>
            <div class="footer-copyright">© Curiefense Contributors 2020-2021</div>
            <div class="columns w-row">
              <div class="w-col w-col-2 w-col-small-3 w-col-tiny-3">
                <a href="https://github.com/curiefense" target="_blank" class="w-inline-block"><img src="images/github.svg" loading="lazy" width="30" alt=""></a>
              </div>
              <div class="w-col w-col-2 w-col-small-3 w-col-tiny-3">
                <a href="https://twitter.com/curiefense" target="_blank" class="w-inline-block"><img src="images/twitter.svg" loading="lazy" width="35" alt=""></a>
              </div>
              <div class="w-col w-col-2 w-col-small-3 w-col-tiny-3">
                <a href="https://join.slack.com/t/curiefense/shared_invite/zt-nc8lyrjo-JJoY2mwrqNOfkmoA6ycTHg" target="_blank" class="w-inline-block"><img src="images/slack.svg" loading="lazy" width="30" alt=""></a>
              </div>
              <div class="w-col w-col-6 w-col-small-3 w-col-tiny-3">
                <a href="https://www.linkedin.com/company/curiefense" target="_blank" class="w-inline-block"><img src="images/linkedin.svg" loading="lazy" width="30" alt=""></a>
              </div>
            </div>
          </div>
          <div class="w-col w-col-2"></div>
          <div class="w-col w-col-2">
            <ul role="list" class="footer-list">
              <li class="footer-list-item">
                <a href="features" class="footer-list-item-link">Features</a>
              </li>
              <li class="footer-list-item">
                <a href="manifesto" class="footer-list-item-link">Manifesto</a>
              </li>
              <li class="footer-list-item">
                <a href="https://github.com/curiefense/curiefense/blob/master/ROADMAP.md" target="_blank" class="footer-list-item-link">Roadmap</a>
              </li>
              <li class="footer-list-item">
                <a href="https://github.com/curiefense/curiefense/blob/master/CODE_OF_CONDUCT.md" target="_blank" class="footer-list-item-link">Code of Conduct</a>
              </li>
            </ul>
          </div>
          <div class="w-col w-col-2">
            <ul role="list" class="footer-list second">
              <li class="footer-list-item">
                <a href="https://github.com/cncf/artwork/blob/master/examples/sandbox.md#curiefense-logos" target="_blank" class="footer-list-item-link">Logos</a>
              </li>
              <li class="footer-list-item">
                <a href="contact-us" class="footer-list-item-link">Contact Us</a>
              </li>
              <li class="footer-list-item">
                <a href="blog" class="footer-list-item-link">Blog</a>
              </li>
              <li class="footer-list-item">
                <a href="faq" class="footer-list-item-link">FAQ</a>
              </li>
            </ul>
          </div>
          <div class="w-col w-col-2">
            <ul role="list" class="footer-list second">
              <li class="footer-list-item">
                <a href="https://twitter.com/curiefense" target="_blank" class="footer-list-item-link">Twitter</a>
              </li>
              <li class="footer-list-item">
                <a href="https://github.com/curiefense/curiefense" target="_blank" class="footer-list-item-link">GitHub</a>
              </li>
              <li class="footer-list-item">
                <a href="https://stackshare.io/curiefense/curiefense" target="_blank" class="footer-list-item-link">StackShare</a>
              </li>
              <li class="footer-list-item">
                <a href="https://www.katacoda.com/curiefense" target="_blank" class="footer-list-item-link">Katacoda</a>
              </li>
            </ul>
          </div>
        </div>
      </div>
      <div class="container-2 w-container">
        <a href="https://www.cncf.io/sandbox-projects/" target="_blank" class="w-inline-block"><img src="images/cncf-sandbox-horizontal-color.svg" loading="lazy" width="150" alt="" class="image-8"></a>
      </div>
      <div class="w-container">
        <div class="text-block-4">© 2021 The Linux Foundation. All rights reserved. The Linux Foundation has registered trademarks and uses trademarks. <br>For a list of trademarks of The Linux Foundation, please see our <a href="https://www.linuxfoundation.org/en/trademark-usage/" target="_blank">Trademark Usage</a> page.</div>
      </div>
    </div>
  </div>
  <script src="https://d3e54v103j8qbb.cloudfront.net/js/jquery-3.5.1.min.dc5e7f18c8.js?site=5f906e60f009d620eb2024dd" type="text/javascript" integrity="sha256-9/aliU8dGd2tb6OSsuzixeV4y/faTqgFtohetphbbj0=" crossorigin="anonymous"></script>
  <script src="js/curiefense.js" type="text/javascript"></script>
  <!-- [if lte IE 9]><script src="https://cdnjs.cloudflare.com/ajax/libs/placeholders/3.0.2/placeholders.min.js"></script><![endif] -->
