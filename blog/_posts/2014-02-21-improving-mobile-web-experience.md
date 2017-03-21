---
layout: post
title: Improving Mobile Web Experience (A Case Study)
---

{{ page.title }}
================

A few days ago, I was looking at job boards and came across a web developer job ads which leaded me to its company's (Teapot Digital) [website](http://www.teapotdigital.com.au/). Upon further researching the company, I liked what I find and thought it has a solid [porfolio](https://www.facebook.com/TeapotDigital) of websites all built with the latest design trends which draws me wanting to work with them. The company website itself is minimalist and responsive. Being curious, I fire up Chrome's Developer Tools to see how it is done and find myself coming up with ideas of improving the website [[demo](http://jhkueh.github.io/teapot_digital_CI/)]. So, I am going to discuss them in this post.

### HTML5 Rocks  ###

Really? Yes really. HTML5 is the future of the web. Even Steve Jobs [agreed](http://www.apple.com/hotnews/thoughts-on-flash/). Although some of its specifications have yet to be finalised, we can already ultilise some of its functionalities to make the web having a better and richer user experience. The [website](http://www.teapotdigital.com.au/), I noticed, is still using XHTML for whatever reasons. Perhaps for supporting Internet Explorer (IE) 6 or 7 users. Those users should be rare by now in 2014. At least in Australia, Kogan implemented the world's first "[Internet Explorer 7 Tax](http://www.kogan.com/au/blog/new-internet-explorer-7-tax/)" which would incentivise customers to upgrade their IE 7. Since IE 8 is almost [5 years old](http://en.wikipedia.org/wiki/Internet_Explorer_8), when are you going to introduce the IE 8 tax, Kogan?

Next, I am going to show how HTML5 rocks in a minute, but first, I want to explain the mobile web.

### Why care about mobile web users? ###

Mobile web users are on the rise. Over 1.2 billion people access the web from their mobile devices, according to this [infographic](http://www.trinitydigitalmarketing.com/mobile-on-the-rise-infographic) by Trinity Digital Marketing.

In an article by [Mashable](http://mashable.com/2010/04/13/mobile-web-stats/) (April 2010), based on Morgan Stanley's research:
> _Morgan Stanley's analysts believe that, based on the current rate of change and adoption, the mobile web will be bigger than desktop Internet use by 2015._

Then, we have headlines from [Business Insider](http://www.businessinsider.com/mobile-will-eclipse-desktop-by-2014-2012-6) (Jun 2012) which reads:
> _ComScore: Mobile Will Force Desktop Into Its Twilight In 2014_

Next, the description from a SlideShare titled [Thinking Mobile First](http://www.slideshare.net/jordanharper/thinking-mobile-first-27889681) by Jordan Harper writes:
> "In 2014, more users will access the web on mobile devices (smartphones + tablets) than with 'desktop' machines."

Highlights of the presentation include:

+ More people use Twitter on mobile than on the web ([71% vs 64%](http://www.strategyanalytics.com/default.aspx?mod=pressreleaseviewer&a0=5350))
+ [71%](http://www.prnewswire.com/news-releases/facebook-reports-fourth-quarter-and-full-year-2012-results-189078621.html) of Facebook's Monthly Active Users are on mobile
+ [48%](http://emailclientmarketshare.com/) of e-mails are opened on mobile devices

In a world where we see massive adoption in mobile devices, ignoring mobile web users is no longer an option anymore. Businesses who do, will lose out because "61% of people have a better opinion of brands when they offer a good mobile experience" according to [Latitude](http://files.latd.com/Latitude-Next-Gen-Retail-Study.pdf).

### How HTML5 rocks mobile web ###

In this section, I am going to show how HTML5 give mobile web users a better User Experience (UX).

Below is the UX of the original email field:

![original email UX](https://www.dropbox.com/s/ep48om2r7e8cjmh/input-email-UX-bad.png?raw=1 "original email UX")

With HTML5, noticed the '@' besides the spacebar:

![improved email UX](https://www.dropbox.com/s/c8mefvhb95hq4ut/input-email-UX-good.png?raw=1 "improved email UX")

The above example may not seem like a big improvement if you have [TouchPal](www.touchpal.com/) installed. But what if you need to enter in a telephone number? This is what we have in the original.

![original phone UX](https://www.dropbox.com/s/8vnlt6fslw551wk/input-phone-UX-bad.png?raw=1 "original phone UX")

With HTML5, users are presented with the keypad right away when selecting the phone field, which makes a better UX.

![improved phone UX](https://www.dropbox.com/s/i19u6ji6y859kb2/input-phone-UX-good.png?raw=1 "improved phone UX")

### How's it done ###
HTML5 introduces a few <code>[input](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input)</code> 'type'. So just change the input type to <code>email</code> or <code>tel</code>, instead of <code>text</code>, like so:

{% highlight html %}
<input name="form_67_email" type="email" ...... required="">
<input name="form_67_phone" type="tel"   ...... required="">
{% endhighlight %}

While there is no discernible difference for non-mobile browsers, these properties provides a better UX on mobile web browsers. As for older mobile web browsers that didn't support HTML5, they will just appear as a normal input field.

### How does AngularJS fit in? ###

Why AngularJS? First of all, I choose [AngularJS](http://angularjs.org/) for its two-way data-binding, one of its most notable features. See it in action below:

![two-way data-binding at work](https://www.dropbox.com/s/odtxu5wj9s6r173/angularJS-magic.gif?raw=1 "two-way data-binding at work")

Second of all, it comes with client-side form validation built into the framework itself. Try out the form validation for yourself on the improved page [here](http://jhkueh.github.io/teapot_digital_CI/).

Last of all, it was designed from the start to be easily testable. All of these can be easily implemented, just see the [source code](https://github.com/jhkueh/teapot_digital_CI) to see how easy it is.

Although jQuery can be used here, I find that angularJS give me a little bit more flexibility because of its declarative style of doing things, as opposed to jQuery's DOM manipulation. However, it is worth noting that angularJS is geared more toward building web applications and it should be used with caution when building content sites that depends on SEO.

### Before and after comparison with PageSpeed Insights ###

Here's the results from the [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/) tool ([original](https://developers.google.com/speed/pagespeed/insights/?url=http%3A%2F%2Fwww.teapotdigital.com.au%2F) at the top and [improved](https://developers.google.com/speed/pagespeed/insights/?url=http%3A%2F%2Fjhkueh.github.io%2Fteapot_digital_CI%2F&tab=mobile) at the bottom):
![PageSpeed Comparison](https://www.dropbox.com/s/7vsv3dcdqxaefbn/PageSpeed-comparison.png?raw=1 "PageSpeed Comparison")

The improved page can be viewed [here](http://jhkueh.github.io/teapot_digital_CI/).

Here are some examples of things we do open source and why:

Suggestions for further improvements:

+ Optimise css, javascript and image file size
+ Enable gzip on server-side
+ Refer to [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/?url=http%3A%2F%2Fwww.teapotdigital.com.au%2F) for further suggestions

### Conclusion ###

I hope that everyone who has read this far has learned a thing or two. Again, [here](http://jhkueh.github.io/teapot_digital_CI/) is the improved demo page, in case anyone missed it. One piece of final advice I can give is to always keep on learning. HTML5 will be finalised at the end of this year and there is bound to be richer web experience, be it mobile or desktop, that is being explored. It will certainly open up new possibilities never thought of before as technologies advance. What I have showcase here is the fruit of my learning at Udacity's [Mobile Web Development](https://www.udacity.com/course/cs256) course. Stay Udacious!

### Additional resources ###

+ [HTML5rocks.com](http://www.html5rocks.com/) has some excellent articles on improving site performance and mobile experience
+ Follow [#perfmatters](https://plus.google.com/explore/perfmatters) on Google+
+ Use the [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/) tool
+ [Egghead.io](http://egghead.io) for excellent bite-size AngularJS tutorial videos

--
<p class="meta">25 February 2014</p>