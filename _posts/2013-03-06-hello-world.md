---
layout: post
title: Hello World!
---

{{ page.title }}
================

Hello World! This blog hosted is on [Github](https://github.com/). It is written in [Markdown](http://daringfireball.net/projects/markdown/), powered by [Jekyll](http://github.com/mojombo/jekyll). A cool new toy which I just discovered at [Github Pages](http://pages.github.com/). I had being playing with it for the last 2-3 hours.

Why is it cool? Firstly, it is hosted on Github. Secondly, whenever I push my blog's [repository](https://github.com/jhkueh/jhkueh.github.com) to GitHub, Jekyll will transforms it into a static site. Not just Markdown file, it supports [Textile](http://en.wikipedia.org/wiki/Textile_(markup_language)) too. No database needed.

Why avoid databases?

Scott Chacon ([@schacon](https://github.com/schacon)) of Github has this to say:
>In the past, I have had two catastrophic data losses from my hosting providers losing a good number of my posts. Each time I thought I would finally remember to setup something that would back them up, but I never did. [1]


According to Jekyll's creator Tom Preston-Werner ([@mojombo](https://github.com/mojombo)):
>I was tired of having my blog posts end up in a database off on some remote server. That is backwards. I’ve lost valuable posts that way. I want to author my posts locally in Textile or Markdown. My blog should be easily stylable and customizable any way I please. It should take care of creating a feed for me. And most of all, my site should be stored on GitHub so that I never lose data again. [2]

Using databases are fine for a couple of things. But for a blog, I think that it is diffucult to do backups or to migrate another host/platform. Heck, even Wordpress generates static html files of your blog post via caching plugins for faster page load, so why use a database at all?

Finally, this blog was setup with the help of:

* Github's [Automatic Page Generator](https://help.github.com/articles/creating-pages-with-the-automatic-generator)
* Jekyll's [README](https://github.com/mojombo/jekyll/blob/master/README.textile)
* @mojombo's blog [source](https://github.com/mojombo/mojombo.github.com) 
* and for post truncation: @MattHall's [plugin](https://github.com/MattHall/truncatehtml), [Richard Huang's](http://huangzhimin.com/) blog [index.html](https://github.com/flyerhzm/flyerhzm.github.com/blob/master/index.html) &amp; [_config.yml](https://github.com/flyerhzm/flyerhzm.github.com/blob/master/_config.yml)

> __Edited__: Plugins are disabled on Github pages due to security restrictions, according to [@mojombo](https://github.com/mojombo/jekyll/issues/325#issuecomment-1135567). So, the truncation plugin won't work on Github pages unless you generate your site locally and push the resulting HTML to a Git repo :/

### How do to get started? ###

Here's an [intro](https://github.com/blog/272-github-pages) to GitHub Pages.

--
<p class="meta">6 March 2013</p>

  [1]: http://schacon.github.com/2009/02/11/moved-to-github-pages.html
  [2]: https://github.com/mojombo/mojombo.github.com/blob/master/README.textile