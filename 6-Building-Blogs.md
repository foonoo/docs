---
title: Building Blogs of sites with sites with serial content
---

# Building Blogs

By default, foonoo ships with two site generators: the default site generator and a blog generator. Previous sections have already covered the default generator in quite some detail, and we merely scratched the surface on blog creation in an earlier chapter. For the rest of this chapter we will be going into a lot of detail on blog creation.

## Continuing from a simple blog
Unlike plain foonoo sites, blogs require a directory structure, albeit a rather simple one. Specifically, in addition to the `_foonoo` directory, blogs must have a `posts` directory to hold all blog posts and, optionally, a `pages` directory to hold any static pages. Both of these would be created for you when you execute the command:

    foono blogs init

## Writing Content for Blogs
All posts for blogs go directly into the `posts` directory. Post files are required to be named as follows `YYYY-MM-DD-Slug.ext`. Here the `YYYY` represents the year of the post, `MM` represents the time and `DD` represents the day. Similarly, the `.ext` represents the extension of the text markup in use. Currently this can only be `.md` (but there are plans to support `.html` and other text markup formats, but you can always add your own as we'd see later).

Content that go into the `pages` directory is treated similarly to content for plain sites. They are simple static pages that are not serialized as part of the blog content. You can use this to hold content like an about page, a list of projects, terms and conditions, and anything that isn't a blog post.

### Blog post Specific Frontmatter
Content for blogs are written in the same way as all other foonoo content (see [[Writing with Foonoo]]). However, there are a few requirements with front matter entries when blog posts are considered. Additionally, there are other blogging specific front matter entries that provide access to some of foonoo


1. The blog directory structure.
1. Writing content for blogs.
1. Blog specific front matter.
1. Taxonmies.
1. Archives
1. Comments and feeds