---
layout: default
title: "Curiefense Blog"
description: "News and information about Curiefense, the security extension for Envoy"
---

<div class="hero-nohome blog-posts">
  <div class="container w-container">
    <div class="row flex-vertical w-row">
      <div class="w-col w-col-9 w-col-stack">
        <div class="item-vertical first">
          <h3 class="heading-2">Blog</h3>
        </div>
      </div>
      <div class="no-paddings w-col w-col-3 w-col-stack">
        <div class="hero-image"></div>
      </div>
    </div>
  </div>
</div>
<div class="section blog-posts">
  <div class="container w-container">
    <div class="blog-box-first-wrapper w-dyn-list">
      <div role="list" class="blog-box-first w-dyn-items">
        <div role="listitem" class="blog-box w-dyn-item">
          <div class="blog-box-image"><img src="" loading="lazy" width="146" alt="" class="blog-box-img"></div>
          <div class="blog-box-sepparator"></div>
          <div class="blog-box-date"></div>
          <div class="blog-box-name"></div>
          <p class="paragraph blog-box-summary"></p>
        </div>
      </div>
      <div class="w-dyn-empty">
        <div>No items found.</div>
      </div>
    </div>
    <div class="w-dyn-list">
      <div role="list" class="blog-grid w-dyn-items">
      {% for post in site.posts %}
        <div role="listitem" class="blog-box w-dyn-item">
          <div class="blog-box-image">
            <a href="{{post.url}}">
              <img src="{{post.mainImage | default: post.thumbnail}}">
            </a>
          </div>
          <div class="blog-intro">
            <div class="w-row">
            </div>
            <a href="{{post.url}}" class="w-inline-block">
              <div class="blog-box-name">{{post.title}}</div>
            </a>
            <p class="paragraph blog-box-summary">
              {{post.description}}
            </p>
            <div class="card-author">
              {% assign author = site.data.team-members | find: "name", post.author %}
              <img src='{{ author.imageSrc }}' />
              <div class="author-date">
              {{post.author}}
              <br/>
              {{post.createdOn | date_to_string: "ordinal", "US"}}
              </div>
            </div>
          </div>
        </div>
      {% endfor %}
      </div>
    </div>
  </div>
</div>
