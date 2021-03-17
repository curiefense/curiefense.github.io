---
layout: default
title: 'Curiefense Blog'
description: 'News and information about Curiefense, the security extension for Envoy'
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
            <a href="{{post.url}}" class="w-inline-block" style="background-image: url({{post.MainImage | default: post.thumbnail}}); background-size: cover; background-repeat: no-repeat; height: 100%; display: block;">
            </a>
          </div>
          <div class="blog-box-sepparator"></div>
          <div class="w-row">
            <div class="w-col w-col-6">
              <div class="blog-box-date">{{post.createdOn | date_to_string: "ordinal", "US"}}</div>
            </div>
            <div class="w-col w-col-6">
              <div class="blog-box-date">{{post.author}}</div>
            </div>
          </div>
          <a href="{{post.url}}" class="w-inline-block">
            <div class="blog-box-name">{{post.title}}</div>
          </a>
          <p class="paragraph blog-box-summary">
            {{post.excerpt}}
          </p>
          <a href="{{post.url}}" class="button blog-box-button w-inline-block">
            <div class="text-block">Read more</div>
          </a>
        </div>
      {% endfor %}
      </div>
      <!-- <div class="w-dyn-empty">
        <div>No items found.</div>
      </div> -->
      <!-- <div class="w-pagination-wrapper blog-posts-pagination">
        <a href="#" class="w-pagination-previous"><svg class="w-pagination-previous-icon" height="12px" width="12px" xmlns="http://www.w3.org/2000/svg" viewbox="0 0 12 12" transform="translate(0, 1)">
            <path fill="none" stroke="currentColor" fill-rule="evenodd" d="M8 10L4 6l4-4"></path>
          </svg>
          <div class="w-inline-block">Previous</div>
        </a>
        <a href="#" class="w-pagination-next">
          <div class="w-inline-block">Next</div>
          <svg class="w-pagination-next-icon" height="12px" width="12px" xmlns="http://www.w3.org/2000/svg" viewbox="0 0 12 12" transform="translate(0, 1)">
            <path fill="none" stroke="currentColor" fill-rule="evenodd" d="M4 2l4 4-4 4"></path>
          </svg>
        </a>
      </div> -->
    </div>
  </div>
</div>
