---
title: jekyll-admin is pretty convenient
layout: post
tags:
- jekyll
- reviews
- webdesign
date: '2018-08-09 11:00:00'
---

[Jekyll](https://jekyllrb.com/) has been my go-to tool for all my websites for a few years now. From a technical perspective, it's ideal: 

* The server requirements are minimal (because it's all statically generated).
* Hosting is relatively risk-free (because it's all statically generated).
* It's highly customizable and flexible.
* Jekyll plays nice with various front-end frameworks. 

I could go on.

The two major downsides are deployment and creating content. The former because you'll have to manually generate and deploy your site after each change. I'm aware that there are ways to improve this, but haven't seriously tried any yet. Creating content is cumbersome because you'll have to create a new file (or rather copy an existing post or page) and edit its content in your prefered Markdown editor. I enjoy writing pots in Vim, but having to manually create a file, add the proper metatags etc. keeps me from adding quick entries.

Today I came across [jekyll-admin](https://github.com/jekyll/jekyll-admin).
> A Jekyll plugin that provides users with a traditional CMS-style graphical interface to author content and administer Jekyll sites.

![The jekyll-admin post editing interface](/assets/blog/jekyll-admin-screenshot.jpg)

### Benefits

It takes away many of the manual labor involved in creating a new post and introduces an easy to use interface to write content. I'm using it to jot down this entry and I could easily get used to this.

* The WYSIWYG editor is nice, eventhough I've used the Markdown tags enough to not depend on the buttons provided.
* Adding a new post is accomplished by pressing a single button.
* Previewing is another press of a button.

Small improvements, but I welcome anything that lowers the threshold to start writing. The installation takes about ten seconds:

### Installation

1. Add the following to your site's `Gemfile`:

		gem 'jekyll-admin', group: :jekyll_plugins

2. Run `bundle install`

### Downsides

Vim shortcuts are not available, obviously. Maybe I'll end up just using the UI to create posts, then do the writing in a terminal window. 

~~Another thing – that honestly feels like a bug – is that the metatags have to be entered from scratch, for each post. It's worth the effort to go in and see if I can add my prefered behavior to the project.~~

_Update: The admin interface automatically picks up on the front matter defaults. Simply adding the following few lines to the `_config.yml` file will prefill the corresponding fields in the content management system._

```yaml
defaults:
  - scope:
      path: ''
      type: posts
    values:
      layout: 'post'
      tags: []
  - scope:
      path: ''
      type: pages
    values:
      layout: 'page'
      menu: true
      menu_title: ''
```

![jekyll-admin does not automatically set the proper metatags](/assets/blog/jekyll-admin-metatags.jpg)

### Conclusion

This is hardly a thorough review; all I did is write this signle post. The added convenience is undeniable, though. I'm positive jekyll-admin will help me to post more often. *Famous last words.*
