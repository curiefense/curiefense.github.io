---
layout: default
title: 'FAQ for Curiefense'
description: 'Frequently Asked Questions for Curiefense, the open-source security suite for Envoy Proxy'
---

<div class="hero-nohome faq">
	<div class="container w-container">
		<div class="hero-row nohome">
			<div class="row flex-vertical w-row">
				<div class="w-col w-col-9 w-col-stack">
					<div class="item-vertical level-one first">
						<div class="item-vertical first">
							<h3 class="heading-2">Questions answered</h3>
							<h1 class="hero-title nohome">FAQ</h1>
						</div>
					</div>
				</div>
				<div class="no-paddings w-col w-col-3 w-col-stack">
					<div class="hero-image"></div>
				</div>
			</div>
		</div>
	</div>
</div>
<div class="section faq">
	<div class="container w-container">
		<div class="row-section faq-header w-row">
			<div class="w-col w-col-8 w-col-stack">
				<div class="item-vertical faq">
          {% for faq in site.data.faq %}
					<h2 class="heading-3">{{faq.question}}</h2>
					<p class="paragraph manifesto-paragraph">{{faq.answer}}</p>
          {% endfor %}
				</div>
			</div>
			<div class="w-col w-col-4 w-col-stack"></div>
		</div>
	</div>
</div>