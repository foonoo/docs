---
title: Introduction
---
# Introduction
Another static site generator? Yes! Foonoo is a static site generator that converts text files to websites. In fact, it doesn't claim to be any special when compared to others, so don't use it if you're not required to. Functionally, like other static site generators, foonoo reads in structured text files in popular formats like Markdown and converts them to HTML code that can be served directly from just about any web server or content delivery network.

The name foonoo comes from the Fante (Akan) word for an Oven. Just as an oven takes raw dough (or some other combination of preparatory ingredients) and permanently, as well as irreversibly converts them into bread (or some other fantastic baked treat); foonoo takes in your plain text files and images, and converts them into beautiful websites.

## Installing foonoo
The best way to install foonoo is to grab the latest pre-built PHAR archive and make it executable (provided you are on a system that supports that). In fact, any computer system with a modern PHP interpreter should be able to run this archive, if all the required extensions are also installed. You can download the most recent PHAR archive [here](https://github.com/foonoo/foonoo/releases).

To execute a phar archived version of foonoo, you can call:

	php /path/to/foonoo.phar

If the PHAR approach is not suitable for your situation, another alternative to installing can be to perform a composer install. This can be done globally, or in some cases locally to specific projects. To install globally:

	composer global require foonoo/foonoo

Once installed globally, foonoo can be executed from the `~/.config/composer/vendor/bin/foonoo` script, assuming you are on a UNIX-like system (such as a Linux or a Mac). You can even execute the `foonoo` script directly from your shell if you have `~/.config/composer/vendor/bin` in your shell's `PATH`.

For the rest of this document, we can assume that you have an executable `foonoo` script (including renamed PHAR archives) accessible through your `PATH`.


## Quick-start Tutorial
Before we get into the details of how foonoo works, let's go through a simple example. Of course, this example requires that you have a recent version of foonoo installed, and that you also have the ability to navigate the file system through the terminal of your chosen platform. 

First, create an empty directory (or folder) then copy any markdown file you may have lying around into the directory. Next, rename this markdown file to `index.md`, to make it the site's entry point. If you don't have a readily available markdown file you can copy the text below into a text file and name it as `index.md`.

````
# Hello World

I've always wondered why the phrase, "Hello World", is typically used for the output of the quintessential first program in most introductory programming content. 
````  

Once you have your `index.md` in place, you can switch your current directory to the location of the index file and execute:

	foonoo generate

Assuming your file is stored in a location, `/path/to/example`, you should see the following output:

	Writing all outputs to "/path/to/examples/output_site/"
	
	Generating default site from "/path/to/examples/"
	- Rendering content for /path/to/examples/output_site/index.html 
	- Writing content to /path/to/examples/output_site/index.html 
	Total build time: 0.04s

And in your current directory you should have a `_foonoo` directory that contains some foonoo specific data and an `output_site` directory, which contains your output site. Go ahead and with the browser of your choice, open the `index.html` file located in the `output_site` directory to preview your site. 

Additionally, if you want to see how your site behaves when served, you can spin up a simple test server by executing:

	foonoo serve

This server listens on port 7000 of the localhost, so putting `http://localhost:7000` into your browser should bring up a site that looks similar to the one below.

[[A screenshot of a browser serving the rendered hello world page|hello_screenshot.png|frame="figure"]]



## Architecture Overview

Before we go into the details of using foonoo, it is worth taking some time to get a high level understanding of its architecture. This brief explanation should make it easier to understand much of the rest of this document.

Although foonoo is built in the spirit of other static generators, it tries to differentiate itself by acting as a platform on which different site generators (referred to as site builders) run. At its core, foonoo is just a platform that coordinates the work of these other site builders. While these site builders are responsible for defining the structure of the inputs and the type of content contained, foonoo provides these builders with the following services:

   - A common interface through which site builders can access content for their site. 
   - An ecosystem for shared plugins and extensions that builders can use to enhance their sites.
   - A transparent and extensible markup conversion system, which provides conversions for different text formats. (Markdown, reStructured, etc.), 
   - A common theming and templating infrastructure for styling sites. 
   - An assets and media management system. 
   - And most importantly, a user interface through which end users can interact with the site builders. 

Currently, foonoo ships bundled with two builders: `default` and `blog`.

The `default` builder, which we already used in our earlier example, is loaded by default requires no file system structure. It simply works by converting all the files in the input directory into HTML files.

Blog provides an extension over the plain builder which is useful for building blogs, as its name suggests.

## Directory Structure and Site Nesting
Because of the free-form nature of foonoo, there really isn't a set directory structure. The exception to this, however, is that every site must have a `site.yaml` file in its root to hold information about the site, and a `_foonoo` directory to store other shared site resources like images, themes, plugins, and the like.

Another interesting feature foonoo has is its ability to support nested sites. For example, you could have a personal site directory in which you can hold a blog site in its own sub directory (with its own complete independent site) and maybe a projects site also with its own sub directory (and also with its own complete site.)

Although this feature may seem superficial, it provides the benefits of being able to build all sites in one go, and it allows sites to share resources. With a feature like this, a complex network of static sites can easily be maintained from a single root.