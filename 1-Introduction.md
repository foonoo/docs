# Introduction
Another static site generator? Yes, foonoo is a static site generator that converts text files to websites. In fact, it doesn't claim to be any special when compared to others, so don't use it if you're not required to. Functionally, like other static site generators, foonoo reads in structured text files in popular formats like Markdown and converts them to HTML code that can be served directly from just about any web server. 

The name foonoo comes from the Fante (Akan) word for Oven. Just as an oven takes raw dough (or some other combination of preparatory materials) and permanently, as well as irreversibly converts them into bread (or some other fantastic baked treat); foonoo takes in your plain text files and images, and converts them into beautiful websites.

## Installing foonoo
The best way to install foonoo is to grab the latest pre-built PHAR archive. Any computer system with a modern PHP interpreter should be able to run this archive (provided the required extensions are also installed). You can download the most recent PHAR archive [here](https://github.com/foonoo/foonoo/releases).

To execute a phar archived version of foonoo, you can call:

	php /path/to/foonoo.phar

Another alternative to installing from a PHAR archive will be to perform a composer install. This can be done globally, or in some cases locally to specific projects. To install globally:

	composer global require foonoo/foonoo

Once installed globally, foonoo can be executed from the `~/.config/composer/vendor/bin/foonoo` script. You can even call the `foonoo` script directly from your shell if you have `~/.config/composer/vendor/bin` in your `PATH`.

For the rest of this document, we can assume that you have an executable `foonoo` script (including renamed PHAR archives) accessible through your `PATH`.


## Quickstart Tutorial
Before we get into the details of how foonoo works, let's go through a simple example. Of course, this example requires that you have successfully installed foonoo, and you also have the ability to navigate the file system and terminals of your chosen platform. 

First, create an empty directory (or folder) through the terminal. Then copy any markdown file you may have lying around into the folder as `index.md`. If you don't have a readily available markdown file you can copy the text below into a text file and name it as `index.md`.

````
# Hello World

I've always wondered why the phrase, "Hello World", is typically used for the output of the quintessential first program in most introductory programming content. 
````  

Once you have your `index.md` in place, you can switch your current directory to its (`index.md`) location and execute.

	foonoo generate

Assuming your file is stored in a location, `/path/to/example`, you should see the following output:

	Writing all outputs to "/path/to/examples/output_site/"
	
	Generating default site from "/path/to/examples/"
	- Rendering content for /path/to/examples/output_site/index.html 
	- Writing content to /path/to/examples/output_site/index.html 
	Total build time: 0.24s

And in your current directory you should have a `_foonoo` directory, which

## Foonoo Architecture

Although it's built in the spirit of other static generators, foonoo tries to differentiate itself by acting as a platform on which different site generators run. At its core, foonoo is just a platform that coordinates the work of other smaller site generators. While these site generators are responsible for defining the structure of the websites and the type of content it can contain, foonoo provides these builders with the following:

   - A common interface through which site builders can access content for their site. 
   - An ecosystem for shared plugins that extend the sites.
   - A transparent and extensible markup conversion system, which provides conversions for different text formats. (Markdown, reStructured, etc.), 
   - A common theming and templating infrastructure. 
   - An assets and media management system. 
   - And most importantly, a user interface through which end users can interact with the site builders. 

By default foonoo ships with four different builders: `plain`, `blog`, `docs`, and `wiki`.

The plain builder, which we already used in our earlier example, is loaded by default requires no file system structure. It simply works by converting all the files in the input directory into html files.

Blog provides an extension over the plain builder which is useful for building blogs. Docs is well suited to books and documentation sites. And wiki works as a rendering engine for a git backed wiki.
