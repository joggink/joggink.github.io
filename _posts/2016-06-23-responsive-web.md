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
		<li>The <strong>fluid grid concept</strong> calls for page element sizing to be in relative units like percentages, rather than absolute units like pixels or points.</li>
		<li><strong>Flexible images</strong> are also sized in relative units, so as to prevent them from displaying outside their containing element.</li>
		<li><strong>Media queries</strong> allow the page to use different CSS style rules based on characteristics of the device the site is being displayed on, most commonly the width of the browser.</li>
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

<p>And then some Norwegian guy (Håkon Wium Lie) came around and developed CSS, seperating content and layout. Mind was blown! The community started to adapt and realised that using tables for layout was semantically not correct. A new era began: <kbd>&lt;div&gt;</kbd> to the rescue!</p> 

<p>As with the tabular mindset, fixed width of websites was still the way to go and we gradually moved up to 968 pixels as everybody had 1024px screens. I never really understood where those 968 pixels came from because scrollbars were 24 pixels wide... Anyway, we kept on getting new features in css, browsers became civilised again, internet connections became faster and boy, were we on a roll. It was until 2007, when apple launched their first iphone, that the internet shifted! Those fixed width websites were hardly readable on those tiny telephone screens so something had to be done.
</p>

<h3>Responsive web to the rescue!</h3>

<p>Media queries, viewport schmuck, touchevents, etc... All needed to build a responsive web? Not really! We, the developers, strive to build great experiences by creating boundaries for our own. We make function follow form instead of the other way around. Most, almost all of our problems are self created constraints. Ever since </p>

<blockquote>
	<p>The web has always been responsive!</p>
</blockquote>

<p>So back to our initial 3 statements:</p>

<h4>Fluid grid concept</h4>
<p>So we need to size elements with relative units like percentages, rather than absolute units like pixels or points? By default everything is relative to the viewport. Even without grid concepts like <kbd>flexbox</kbd> or <kbd>grid</kbd> everything remains in the viewport. Why are we so desperate to put everything on a grid? Ever since we started using tables for layout we continued on this path of grid layouts, mirroring a print mindset to a different medium. We think we are pushing the web forward but we still have a long way to go. </p>

<h4>Flexible images</h4>
<p>As previous concept, these should be sized in relative units, so as to prevent them from displaying outside their containing element. I've had to use a little <kbd>max-width</kbd> trick to make the images on this page behave but other than that they're fine. I could have used responsive images but that's a road I'm not willing to take. The spec itself is utter crap. Having multiple image sources for all different viewports and screen densities? At the rate pixels per inch are evolving we will have a shitload of images to maintain. Compare it with the evolution of movie resolutions. I can view a full HD movie on my crappy screen and vice versa. Most important: the purpose of the web is  sharing content. </p>

<h4>Media queries</h4>
<p>Allowing the page to use different CSS style rules based on characteristics of the device the site is being displayed on, most commonly the width of the browser. These were actually proposed in 1994 by Håkon Wium Lie but didn't make in in the CSS1 spec. Since CSS2 we have media type support which makes sense: displaying content on a computer screen, projecting, braille, speech, print, etc...  By adding media features like device width, height, orientation, aspect ratio, resolution and so on we can create very powerful stylesheets but we're still not there. I'd love to have a media query to know my visitors connection speed and some element queries.</p>

<p>As much as I'm bashing on the whole responsive web design, I'm also loving it. My only fear is that the web development today is no better than the space-background / animted gif pages we created 20 years ago. We are still positioning elements on a grid, thinking we are creating beautiful <em>experiences</em> but I feel we're missing the true point of the web. To put things in context I want to compare the evolution of the web with the history of film. It all began in the 1890s, when motion picture cameras were invented but it took them 37 years until the first movie with sound was released. Our medium is still young and immature, let's try to raise our web and give it a prosperous future!</p>

<p><strong>We are exploring and learning new stuff for the web on a daily basis, but claiming responsive web is a couple of years old and is all about fluid grids and images using media queries? Naaaaah! </strong></p>