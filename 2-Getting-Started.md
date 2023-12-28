---
title: "Getting Started: A Simple Blog"
---
# Getting Started: A simple Blog Example
For a primer on how to use foonoo, let's work through building a simple blog. In addition to being an introduction, this tutorial will also going to provide some useful information about the internal workings of foonoo. Consider this as a hands-on lesson on how foonoo works.

Interestingly, a blogging example is also a good start for anyone interested in working with foonoo. After all, static site generators have always been staple of the personal blogging community&mdash;and if you've read this far, you're most likely interested in blogging with foonoo.

## Initializing a Blog Directory
As already stated, foonoo builds sites by relying on dedicated site builders. When it comes to blogs, foonoo can rely on its in-built `blog` builder. This builder reads its input from a specially formatted source directory and writes its outputs as a static blog website.

The requirement of a specially formatted source directory means the first step in creating a blog is to initialize a "source" directory with the required structure. To do this, switch to an empty directory on the terminal and execute:

```text
foonoo create blog
```

Once executed, this command creates a `site.yml` file, which contains the the configuration details of the site and three other directories: `_foonoo`,  `posts`, and `pages`. These files are structured as follows.

```text
 .
├──  _foonoo
├──  pages
├──  posts
└──  site.yml
```

As its name suggests, the `_foonoo` directory is required by the foonoo core, and it's used internally by foonoo as a source for shared resources, like themes, images and custom scripts, and it also doubles as a space for foonoo to write other build specific information like caches.

The `posts` and `pages` directories, on the other hand, are required by the `blog` builder. Those directories are used to hold the raw text files for individual blog posts and any additional standalone pages you may create.

In foonoo, the `site.yml` file is used to store a site's configuration. This file tells foonoo what builder to use, defines which plugins to load, which assets to inject, and it essentially provides details that help foonoo determine exactly how to build a site. For this example, the `site.yml` file will contain the following:

```yml
# Default configuration 

type: blog
title: 'A foonoo blog site'
description: 'This is a foonoo blog site.'
# plugins:
#   - contrib/highlight
#   - contrib/responsive_images
```

## Testing your blog
With the initial directory structure in place, we can generate the HTML code for our first blog by executing `foonoo generate`	in the blog's source directory.

This command should create an `output_site` directory containing the HTML code for your blog site. If successful, it should produce output similar to what is below:

````text
Found 1 site in "/home/ekow/blog/"
Writing all outputs to "/home/ekow/blog/output_site/"

Generating blog site from "/home/ekow/blog/"
- Rendering content for /home/ekow/blog/output_site/index.html 
- Rendering content for /home/ekow/blog/output_site/posts.html 
- Writing content to /home/ekow/blog/output_site/index.html 
- Writing content to /home/ekow/blog/output_site/posts.html 
- Copying images from /home/ekow/blog/_foonoo/images to /home/ekow/blog/output_site/images
Total build time: 0.13s
````

And your overall directory structure should look like below:

```text
 .
├──  _foonoo
│   └──  cache
├──  output_site
│   ├──  assets
│   │   └──  css
│   │       └──  bundle-default.css
│   ├──  index.html
│   └──  posts.html
├──  pages
├──  posts
└──  site.yml
```

At this point, you can open the `output_site` directory and manually view the `index.html` file, or you can additionally execute `foonoo serve` on the command line to start a web server on [[http://localhost:7000]], through which you could access your blog.

## Customizing Your Blog
You may have noticed that your blog currently has a default foonoo title. To change this, open the generated `site.yml` file and modify the title to whatever you want. For the purposes of this tutorial, we can choose a title "My First Foonoo Blog". When it comes to changing your title, remember to keep your title text in quotes and escape any special characters in the configuration file appropriately (as per the requirements of the YAML standards).

## Writing Content
Now that your blog is named, you can start adding content. There are two main types of content you can add to blogs: `pages` and `posts`. For blogs, you must put periodic posts in the `posts` directory, and fixed pages must be placed in the `pages` directory. In the next few sections we'll look at how to create pages and posts.

### Pages
Let's start with adding pages to out blog. Assuming we wanted to create an "About" page to tell visitors what our blog contains, we can create an `about.md` file in our `pages` directory. In this file we can put the following content:

````markdown
# About this Blog

Hello everyone! Welcome to our lovely little website. This is just an 
example to show how pages can be incorporated to foonoo blogs. 

````

After this page is added, we should have an `about.html` file generated in our `output_site` directory. 

You can use pages to store anything from lists of projects to privacy policies and resumes. 


### Posts
For posts, we can follow the same approach for pages as described in the previous section. This time however, instead of the `pages` directory, we'll use the `posts` directory. Also, post files must have a name that conforms with the format `YYYY-MM-DD-post-id.ext`. Here, `YYYY` corresponds to the year,  `MM` corresponds to the month, `DD` corresponds to the day, and the `post-id` can be a unique ID for the post (typically the title of the post, containing only underscores and hyphens). The `.ext` represents the extension of the post's content file.

To illustrate this, let's create a simple welcome post for our blog. We can name this file as `2022-12-07-welcome-to-my-blog.md` and place it in the `posts` directory. The content of this file could look something as shown below:

```Markdown
---
title: Welcome To My Blog
---

# Welcome!
Welcome to my little blog. If you are seeing this post, then my 
installation of foonoo was succesful. Hopefully, we can progress to 
learn more about how foonoo works.

```

## Next steps
This short example was meant to provide a feel of how foonoo could be used. In the next sections, we'll look at the specific way in which content can be written for foonoo, and we'll look deeper at the two bundled site builders in more detail.

