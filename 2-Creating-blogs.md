# A simple Blog Example
For a proper primer on how to use foonoo, let's work through a simple blogging example. Not only is this example going to be a good introduction to foonoo, it's also going to provide some useful information about the internal workings of foonoo. Honestly, a blogging example is also a good start for anyone interested in working with foonoo. After all, static site generators have always been staple of the personal blogging community&mdash;and if you've read this far, you're may most likely interested in blogging with foonoo.

## Initializing a Blog Directory
As already stated, foonoo builds sites by relying on dedicated site generators. When it comes to blogs foonoo foonoo can rely on a built in `blog` generator. This generator reads input from a specially formatted source directory, and it writes its outputs as a static blog website.

The first step in creating a blog is to initialize a directory with the `blog` generator’s required file structure. This can be done by switching to an empty directory where we want the blog's sources to reside and executing the following command:

	foonoo create blog

Once executed, this command creates a `site.yml` file, which contains the the configuration details of the site and three other directories: `_foonoo`,  `posts`, and `pages`. 

As its name suggests, the `_foonoo` directory is required by the foonoo core; it is used internally by foonoo and it’s also where you can place your images, themes and other related assets. 

The `posts` and `pages` directories, on the other hand, are required by the `blog` generator, and they're used to hold the raw text files for individual blog posts and any additional stand alone pages you may create, respectively.

## Testing your blog
With the initial directory structure in place after the `create` command, we can generate the HTML code for our first blog by executing the following code in our blog directory:

	foonoo generate

This command should produce the following output on the console:

````
Found 1 site in "/home/ekow/examples/blog/"
Writing all outputs to "/home/ekow/examples/blog/output_site/"

Generating blog site from "/home/ekow/examples/blog/"
- Rendering content for /home/ekow/examples/blog/output_site/index.html 
- Rendering content for /home/ekow/examples/blog/output_site/posts.html 
- Writing content to /home/ekow/examples/blog/output_site/index.html 
- Writing content to /home/ekow/examples/blog/output_site/posts.html 
Total build time: 0.10s
````

And it should also create an `output_site` directory, which contains the HTML code for your blog site. At this point, you could open the `output_site` directory and manually view the `index.html` file, or you could additionally execute:

	foonoo serve

This would a web server on [[http://localhost:7000]], through which you could access your blog.

## Customizing Your Blog
You may have noticed that foonoo selected a default blog title for you. To change this, open the generated `site.yml` file and modify the title to whatever you want. Remeber to keep your title in quotes and escape special characters in the configuration file appropriately.

## Writing Content
Now that your blog's directory is setup, you can start adding content. For blogs, you must put periodic posts in the `posts` directory, and you must put fixed pages into the `pages` directory.

### Pages

Let's create a simple about page to tell our visitors about our blog. To do this, just go into the `pages` directory and create a file named `about.md`. In this file we can put the following content:

````
# About this Blog

Hello everyone! Welcome to our lovely little website. This is just an example to show how pages can be incorporated to foonoo blogs. 

After this, we'll take a look at how to actually create blog pages!
````

Now when we re-generate our blog, we should have an `about.html` file generated in our `output_site` directory. Notice that after adding this file and building the site again with `foonoo generate`, a menu bar with a link to the about page is added.


### Posts
For posts, you can follow the same approach for pages (as described above) and create a post's file in the `posts` directory. This time, however, you have to name the file with the format `YYYY-MM-DD-post-id.md`. Here, the `YYYY` section corresponds to the year, the `MM` section corresponds to the month, the `DD` section corresponds to the day, and the `post-id` section can be a unique ID for the post (which will typically be the title of the post, containing only underscores and hyphens).

In our running example, we can create a simple welcome post for our blog. We can title this file as `2022-12-07-welcome-to-my-blog.md` and place it in the `posts` directory. We can put to following in the contents of the post:

````

````

After this, when we regenerate the blog, we should have the welcome post listed.

## Customizing our blog
~~Talk about the types of customizations that can be performed. Start with information on how the blog's name and author information can be changed.~~
### Changing theme colors
~~Discuss how config files can be used to change theme parameters~~
### Switching themes
~~Discuss how a completely different theme can be selected~~
### Setting up permalinks
~~Discuss how permalinks can be setup~~


