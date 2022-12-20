# A simple Blog Example
As a proper primer on how to use foonpp, let's work through a simple example of building a blog. Not only will this example be a good introduction, it's also meant to provide some information about the internal workings of foonoo. We also feel that a blogging example is a good start for anyone interested in foonoo. After all, static site generators have always been staple of the personal blogging community&mdash;and if you've read this far, you're may most likely interested in blogging with foonoo.

## Initializing a Blog Directory
By default, blogs created with foonoo are processed by the `blog` generator. If we want to create a blog, the first step will be to initialize a directory with the file structure required by the `blog` generator. To do this, we can switch to an empty directory where we want our blog's sources to reside and execute the following command:

	foonoo create blog

Once executed, this command creates a `site.yml` file, which contains the the configuration details of the site and four other directories: `assets`, `media`,  `posts`, and `pages`. 

The `assets` directory and the `media` directory are required by the foonoo core; they are used to store site assets (like stylesheets and icons) and site media (like images and videos respectively). 

The `posts` and `pages` directories, on the other hand, are required by the `blog` generator, and they're used to hold the raw text files for individual posts and stand alone pages respectively.

## Testing your blog
With the initial directory structure in place, we can generate the HTML code for our first blog by executing the following code in our blog directory:

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

## Writing Content
Now that your blog's directory is setup, you can start adding content. For blogs, you must put periodic posts in the `posts` directory, and you must put fixed pages into the `pages` directory.

### Pages
To demonstrate page creation, let's create a simple page to tell our visitors about our blog. To do this, just go into the `pages` directory and create a file named `about.md`. In this file we can put the following content:

````
# About this Blog

Hello everyone! Welcome to our lovely little blog. This is just an example to show how pages can be incorporated to foonoo blogs.
````

Now when we re-generate our blog, we should have an `about.html` file generated in our `output_site` directory.

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

