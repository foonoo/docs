# A simple Blog Example
Let's work through a simple blog example to better understand the inner workings of foonoo. Since we're still introducing foonoo, a blogging example seems like a good start. After all, static site generators have always been staple of the personal blogging community&mdash;and if you've read this far, you're may most likely be blogging with foonoo anyway.

## Initializing a Blog Directory
By default, blogs created with foonoo are processed by the `blog` generator. If we want to create a blog, the first step will be to initialize the directory with the file structure required by the `blog` generator. To do this, we can switch to an empty directory where we want our blog and execute the following command:

	foonoo create blog

Once executed, this command creates a `site.yml` file, which is meant to contain the the configuration details of the site, and four other directories: `assets`, `media`,  `posts`, and `pages`. 

The `assets` directory and the `media` directory are required by the foonoo core; and are used to store site assets (like stylesheets and icons), and site media like images and videos respectively. The `posts` and `pages` directories, on the other hand, are required by the `blog` generator, and they're used to hold the raw text files for individual posts and stand alone pages respectively.

## Testing your blog
With the initial directory structure in place, we can generate our first blog by switching the current directory to our blog directory and executing:

	foonoo generate

This should produce the following output:

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

And an it should also create an `output_site` directory, which contains the actual site. At this point, you could open the `output_site` directory and manually view the `index.html` file, or you could additionally execute:

	foonoo serve

This should start a web server on [[http://localhost:7000]], through which you can access your blog.

## Writing Content
Now that your base directory is setup, you can start adding content. For blogs, you can put periodic posts in the `posts` directory, and you can put fixed pages into the `pages` directory.

### Pages
Let's create a simple about page to tell our visitors about our blog. To do this, just go into the `pages` directory and create a file named `about.md`. In this file we ca put the following content:

````
# About this Blog

Hello everyone! Welcome to our lovely little blog. This is just an example to show how pages can be incorporated to foonoo blogs.
````


 