# Introduction
Foonoo is a static site generator that converts text files to websites. Like other static site systems, foonoo reads in structured text files in popular formats like Markdown or reStructured and converts them to HTML code that can be served directly from a web server that supports serving HTML files. 

The name foonoo comes from the Fante (Akan) word for Oven. Just as an oven takes raw dough (or some other preparatory material) and permanently, as well as irreversably converts them into bread (or some other fantastic baked treat); foonoo takes in your plain text files and images, and converts them into beautiful websites.

## Installing foonoo
The best way to install foonoo is to grab the latest pre-built PHAR archive. Any computer system with a modern PHP interpreter should be able to run this PHAR archive, provided the required extensions are also installed. 

Another alternative to installing from a PHAR archive will be to perform a composer install. This can be done globally, or in some cases locally to specific projects.

## Quickstart Tutorial
Before we get into the details

## Foonoo Architecture

Although it's built in the spirit of other static generators, foonoo tries to differentiate itself by acting as a platform on which different site generators run. As such, at its core, foonoo is just a platform that coordinates the work of other smaller site generators. While these site generators are responsible for defining the structure of the websites and the type of content it can contain, foonoo provides these builders with the following:

   - A common interface through which site builders can access content for their site. 
   - An ecosystem for shared plugins that extend the sites.
   - A transparent and extensible markup conversion system, which provides conversions for different text formats. (Markdown, reStructured, etc.), 
   - A common theming and templating infrastructure. 
   - An assets and media management system. 
   - And most importantly, a user interface through which end users can interact with the site builders. 

By default foonoo ships with four different builders: `plain`, `blog`, `docs`, and `wiki`.

The plain builder provides no st
