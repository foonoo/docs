---
title: Building Blogs of sites with sites with serial content
---

# Building Blogs

By default, foonoo ships with two site generators: the default site generator and a blog generator. Previous sections have already covered the default generator in quite some detail, and we merely scratched the surface on blog creation in an earlier chapter. For the rest of this chapter we will be going into a lot of detail on blog creation.

## Continuing from a simple blog
Unlike plain foonoo sites, blogs require a directory structure, albeit a rather simple one. Specifically, in addition to the `_foonoo` directory, blogs must have a `posts` directory to hold all blog posts and, optionally, a `pages` directory to hold any static pages. Both of these would be created for you when you execute the command:

    foono create blog

## Writing Content for Blogs
All posts for blogs go directly into the `posts` directory. Post files are required to be named as follows `YYYY-MM-DD-Slug.ext`. Here the `YYYY` represents the year of the post, `MM` represents the time and `DD` represents the day. Similarly, the `.ext` represents the extension of the text markup in use. Currently, the extension can only be `.md` (but there are plans to support `.html` and other text markup formats, but you can always add your own as we'd see later).

Content that go into the `pages` directory is treated similarly to content for plain sites. They are simple static pages that are not serialized as part of the blog content. You can use this to hold content like an about page, a list of projects, terms and conditions, and anything that isn't a blog post.

## Taxonomies
Content for blogs are written similarly to all other foonoo content (see [[Writing with Foonoo]]). However, to help properly categorize blog content, foonoo provides a way to define dynamic front-matter tags. These tags, known as taxonomies, are used to define specific attributes you want posts in your blog to be categorized with.

For example, if you wanted to categorize your posts by topics, authors, and tags, you could define three taxonomy tags for that. These tags, which you could define as `topic`, `author`, and `tags`, would be explicitly specified in the site's `site.yml` configuration file. As such, if we continue with the earlier blog example from our [[Getting Started|Getting Started: A Simple Blog]] chapter, the `site.yml` file could look something like this.

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

With these taxonomies in place, it is now possible to tag each post with these taxonomies in the front matter. So, for example, going back to the earlier blog example, we can modify our welcome post to be as follows.


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

Notice that the taxonomies are used directly in the frontmatter, and they could take data in whatever form 


1. The blog directory structure.
1. Writing content for blogs.
1. Blog specific front matter.
1. Taxonmies.
1. Archives
1. Comments and feeds