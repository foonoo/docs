---
title: Building Blogs of sites with sites with serial content
---

# Building Blogs

By default, foonoo ships with two site generators: the default site generator and a blog generator. Previous sections ([[of this documentation|Building Sites]]) have already covered the default generator in quite some detail, and we merely touched on blog creation in an earlier chapter. For the rest of this chapter we will be going into a lot of detail on blog creation.

## Continuing from a simple blog
Unlike plain foonoo sites, blogs require a directory structure, albeit a rather simple one. Specifically, in addition to the `_foonoo` directory, blogs must have a `posts` directory to hold all blog posts and, optionally, a `pages` directory to hold any static pages. Both of these directories would be created for you when you execute the command:

    foono create blog

## Writing Content for Blogs
All posts for blogs go directly into the `posts` directory. Post files are required to be named as follows: `YYYY-MM-DD-Slug.ext`. Here the `YYYY` represents the year of the post, `MM` represents the time and `DD` represents the day. Similarly, the `.ext` represents the extension of the text markup in use. Currently, the extension can only be `.md` (but there are plans to support `.html` and other text markup formats, and you can always add your own as we'd see later).

Content that goes into the `pages` directory is treated similarly to content for plain sites. They are simple static pages that are not serialized as part of the blog content. You can use this to hold content like an about page, a list of projects, terms and conditions, and any content that isn't a blog post.

## Taxonomies
Content for blogs are written similarly to all other foonoo content (see [[Writing with Foonoo]]). However, to help properly categorize blog content, foonoo provides features for defining dynamic front-matter tags. These tags, known as taxonomies, are used to define specific attributes you want posts in your blog to be categorized with.

For example, if you wanted to categorize your posts by topics, authors, and tags, you could define three taxonomy tags for that. These tags, which you could define as `topic`, `author`, and `tags`, must be explicitly specified in the site's `site.yml` configuration file. In continuing with the earlier blog example from our [[Getting Started|Getting Started: A Simple Blog]] chapter, the `site.yml` file could look something like this.

```yaml
# Default configuration 

type: blog
title: 'A foonoo blog site'
description: 'This is a foonoo blog site.'
taxonomies: ['topic', 'author', 'tags']
# plugins:
#   - contrib/highlight
#   - contrib/responsive_images

```

With these taxonomies placed in the `site.yml`, it is now possible to appropriately categorize each post through front matter entries. For example, going back to the earlier blog example, we can modify our welcome post to be as follows.


```Markdown
---
title: Welcome To My Blog
author: 
    name: Fire Man
    social_handle: @fireman
topic: pleasantries
tags:
    - message
    - welcome
---

# Welcome!
Welcome to my little blog. If you are seeing this post, then my 
installation of foonoo was succesful. Hopefully, we can progress to 
learn more about how foonoo works.

```

Notice how the taxonomies are used directly in the frontmatter, and also how taxonomies can take data in any type? Having the taxoniomies directly in the frontmatter makes it useful as metadata for the post. Anyone perusing the raw markdown files can easily get a sense of the post's calssification without digging any deeper. Also, by not restricting the data type on tag values, themes are able to use taxonomies anyhow they seem fit. It's just important to keep the values consistent across pages.

## Archives
The blog generator in foonoo automatically generates dated archive pages. This is done to ensure all paths in a post's URL resolve to some meaningful information. In this way, suppose we have a  page hosted at `/2022/02/13/a-sample-post.html`, and someone just visits `/2022/02/13`, the will receive a listing of all pages that were posted on that given date. Similarly, if you were to go a step lower and visit `2022/02`, you should receive a listing of all pages posted in February, and so on.

