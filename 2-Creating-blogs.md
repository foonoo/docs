# A simple Blog Example
Let's work through a simple blog example to better understand the inner workings of foonoo. Since we're still introducing foonoo, a blogging example seems like a good start. Afterall, static site generators have always been staple of the personal blogging community&mdash;and if you've read this far, you're may most likely be blogging with foonoo anyway.

## Initializing a Blog Directory
By default, blogs created with foonoo are processed by the `blog` generator. If we want to create a blog, the first step will be to initialize the directory with the file structure required by the `blog` generator. To do this, we can switch to an empty directory where we want our blog and execute the following command:

	foonoo create blog

Once executed, this command creates a `site.yml` file, which is meant to contain the the configuration details of the site, and four other directories: `assets`, `media`,  `posts`, and `pages`. 

The `assets` directory and the `media` directory are required by the foonoo core; and are used to store site assets (like stylesheets and icons), and site media like images and videos respectively. The `posts` and `pages` directories, on the other hand, are required by the `blog` generator, and they're used to hold the raw text files for individual posts and stand alone pages respectively.


 