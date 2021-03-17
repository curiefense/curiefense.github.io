---
layout: default
title: "About Us | The team behind Curiefense"
description: "Curiefense is an open source project that adds web security to Envoy Proxy. Here is its mission and the people behind it."
---

<div class="section product-team">
  <div class="container w-container">
    <div class="row flex-vertical w-row">
      <div class="row w-col w-col-11">
        <div class="item-vertical level-one">
          <h3 class="heading-2">Our Story</h3>
          <h1 class="heading-3">Our Mission</h1>
          <p class="paragraph hero-paragraph">We live in a world where the range of cyberattacks is ever expanding, and the severity escalates exponentially with the sheer volume of data processed daily across the Internet. <br><br>Attackers evolve rapidly, perfecting their tools and techniques, and demonstrating unprecedented capabilities; thus, collaboration is the most promising way to build a better, more comprehensive, simpler, transparent and scalable security solution.<br><br>Our mission is to provide the ultimate cloud-native application security: a platform that is open, extensible, adaptive and evolving, while maintaining total privacy.<a href="/manifesto"> read our manifesto &gt;&gt;</a><br></p>
        </div>
      </div>
      <div class="no-paddings w-col w-col-1">
        <div class="hero-image"></div>
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
            <!-- <img src="{{member.imageSrc}}" loading="lazy" width="146" sizes="(max-width: 479px) 85vw, (max-width: 767px) 86vw, 90vw" srcset="{{member.imageSrcSet}}" alt="" class="person-img" /> -->
            <img width="206" height="230" src="{{member.imageSrc}}" loading="lazy" width="146" sizes="(max-width: 479px) 85vw, (max-width: 767px) 86vw, 90vw" srcset="{{member.imageSrcSet}}" alt="" class="person-img" />
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
