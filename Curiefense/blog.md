---
layout: default
title: 'Curiefense Blog'
description: 'News and information about Curiefense, the security extension for Envoy'
---

<div class="wrapper">
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
                <a href="{{post.url}}" class="w-inline-block">
                  <img src="{{post.MainImage | default: post.thumbnail}}" loading="lazy" width="70" alt="" class="blog-box-img">
                </a>
              </div>
              <div class="blog-box-sepparator"></div>
              <div class="w-row">
                <div class="w-col w-col-6">
                  <div class="blog-box-date">{{post.publishedOn | date_to_string: "ordinal", "US"}}</div>
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
    <div class="section footer">
      <div class="container w-container">
        <div class="w-row">
          <div class="w-col w-col-4"><img src="/images/curie-01.svg" width="147" alt="">
            <div class="footer-description">
              <p class="paragraph">Curiefense is named in honor of the famous scientist <a href="marie-curie" target="_blank">Marie Curie</a>. The first version was developed in Malakoff, France, a few hundred meters from her home and laboratory. Curiefense was originally created by <a href="https://www.reblaze.com/" target="_blank">Reblaze</a>.<br></p>
            </div>
            <div class="footer-copyright">© Curiefense Contributors 2020-2021</div>
            <div class="columns w-row">
              <div class="w-col w-col-2 w-col-small-3 w-col-tiny-3">
                <a href="https://github.com/curiefense" target="_blank" class="w-inline-block"><img src="/images/github.svg" loading="lazy" width="30" alt=""></a>
              </div>
              <div class="w-col w-col-2 w-col-small-3 w-col-tiny-3">
                <a href="https://twitter.com/curiefense" target="_blank" class="w-inline-block"><img src="/images/twitter.svg" loading="lazy" width="35" alt=""></a>
              </div>
              <div class="w-col w-col-2 w-col-small-3 w-col-tiny-3">
                <a href="https://join.slack.com/t/curiefense/shared_invite/zt-nc8lyrjo-JJoY2mwrqNOfkmoA6ycTHg" target="_blank" class="w-inline-block"><img src="/images/slack.svg" loading="lazy" width="30" alt=""></a>
              </div>
              <div class="w-col w-col-6 w-col-small-3 w-col-tiny-3">
                <a href="https://www.linkedin.com/company/curiefense" target="_blank" class="w-inline-block"><img src="/images/linkedin.svg" loading="lazy" width="30" alt=""></a>
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
                <a href="blog" aria-current="page" class="footer-list-item-link w--current">Blog</a>
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
        <a href="https://www.cncf.io/sandbox-projects/" target="_blank" class="w-inline-block"><img src="/images/cncf-sandbox-horizontal-color.svg" loading="lazy" width="150" alt="" class="image-8"></a>
      </div>
      <div class="w-container">
        <div class="text-block-4">© 2021 The Linux Foundation. All rights reserved. The Linux Foundation has registered trademarks and uses trademarks. <br>For a list of trademarks of The Linux Foundation, please see our <a href="https://www.linuxfoundation.org/en/trademark-usage/" target="_blank">Trademark Usage</a> page.</div>
      </div>
    </div>
  </div>
  <script src="https://d3e54v103j8qbb.cloudfront.net/js/jquery-3.5.1.min.dc5e7f18c8.js?site=5f906e60f009d620eb2024dd" type="text/javascript" integrity="sha256-9/aliU8dGd2tb6OSsuzixeV4y/faTqgFtohetphbbj0=" crossorigin="anonymous"></script>
  <script src="/js/curiefense.js" type="text/javascript"></script>
  <!-- [if lte IE 9]><script src="https://cdnjs.cloudflare.com/ajax/libs/placeholders/3.0.2/placeholders.min.js"></script><![endif] -->