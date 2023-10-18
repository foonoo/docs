---
title: Building Blogs of sites with sites with serial content
---

# Building Blogs

By default, foonoo ships with two site generators: the default site generator and a blog generator. Previous sections have already covered the default generator in quite some detail, and we merely scratched the surface on blog creation in an earlier chapter. For the rest of this chapter we will be going into a lot of detail on blog creation.

## Continuing from a simple blog
Unlike plain foonoo sites, blogs require a directory structure, albeit a rather simple one. Specifically, in addition to the `_foonoo` directory, blogs must have a `posts` directory to hold all blog posts and optionally, a `pages` directory to hold any static pages. Both of these can be created for you when you execute the command:

    foono blogs init

in any target directory.

## Writing Content for Blogs
All posts for blogs go directly into the `posts` directory. Post files are required to be 
1. The blog directory structure.
1. Writing content for blogs.
1. Blog specific front matter.
1. Taxonmies.
1. Archives
1. Comments and feeds