---
layout: post
title:  "What is this responsive web you speak of?"
date:   2016-06-23 00:04:56
permalink: /responsive-web/
categories: web
disqus: false
---

<p>As "<em>a guy who knows his way around computers</em>" I looked it up on this online encyclopedia called wikipedia:</p>

<blockquote class="quote">
	<p>A site designed with RWD adapts the layout to the viewing environment by using fluid, proportion-based grids, flexible images, and CSS3 media queries, an extension of the @media rule, in the following ways:</p>
	<ul type="disc">
		<li>The fluid grid concept calls for page element sizing to be in relative units like percentages, rather than absolute units like pixels or points.</li>
		<li>Flexible images are also sized in relative units, so as to prevent them from displaying outside their containing element.</li>
		<li>Media queries allow the page to use different CSS style rules based on characteristics of the device the site is being displayed on, most commonly the width of the browser.</li>
	</ul>
	<cite>
		&mdash; <a href="https://en.wikipedia.org/wiki/Responsive_web_design">Wikipedia</a>
	</cite>
</blockquote>

<p>As much as it is true, I can't agree with the fact that we need media queries, responsive images and a fluid grid concept to make a website responsive. </p>

<h3>Let me take you on a trip down memory lane</h3>

<p>
	<a href="http://info.cern.ch/hypertext/WWW/TheProject.html">The first website ever</a> was published by the World Wide Web’s creator Tim Berners-Lee on August 6, 1991. A simple page explaining the world wide web and how you could be a part of it by creating your own webpages. It didn't take long before all hell broke loose and we started seeing epileptic brainfarts like this:
</p>

<figure>
	<img src="/a/responsive-web/geocities.gif" alt="An old school geocities website with space backgrounds and animated gifs" />
	<figcaption><small>&mdash; Source: <a href="https://www.threadless.com/forum/post/1006139/the_best_website_in_all_of_geocities_/">https://www.threadless.com/forum/post/1006139/the_best_website_in_all_of_geocities_/</a></small></figcaption>
</figure>

<p>I have to admit, when playing around on the web mid 90's using <kbd>&lt;marquee&gt;</kbd> and <kbd>&lt;blink&gt;</kbd> tags, I've created some eyebleeding creatures. Luckily some smart people found out that <kbd>&lt;table&gt;</kbd> could be used to position elements on some kind of <em>grid</em>. All big players were doing it so it had to be good stuff!</p>

<p>So now we had the first <em>decent</em> layouts and shit got real! Browser vendors were implementing features at a rate that no one could follow just and it didn't take too long before they diverged. Different spec implementations combined with a jungle of screen ratios gave birth to buttons stating a webpage was best viewed in netscape 4.0 on a 480 x 640 screen etc...</p>

<p>And then some Norwegian guy came around and developed CSS, seperating content and layout. Mind was blown! The community started to adept and realised that using tables for layout was semantically not correct. A new era began: <kbd>&lt;div&gt;</kbd> to the rescue!</p> 

<p>As with the tabular mindset, fixed width of websites was still the way to go and we gradually moved up to 968 pixels as everybody had 1024px screens. I never really understood where those 968 pixels because scroll bars were 24 pixels wide... Anyway, we kept on getting new features in css, browsers became civilised again, internet connections became faster and boy, were we on a roll. It was until 2007 when apple launched their first iphone, then the internet shifted! Those fixed width websites were hardly readable on those tiny telephone screens so something had to be done.
</p>

<h3>Responsive web to the rescue!</h3>

<p>Media queries, viewport schmuck, touchevents, ... All need to build a responsive web? Not really... We, the developers, strive to build great experiences by creating boundaries for our own. We make function follow form instead of the other way around. Most, almost all of our problems are self created constraints. </p>

<blockquote>
	<p>The has always been responsive!</p>
</blockquote>

<p>
	<small><em>Disclaimer!<br />
		I'm aware that not everything is chronologically correct and that 've let out some stuff, like the rise of Macromedia Flash, flext, etc... But that's not the point of this article.
	</em></small>
</p>
