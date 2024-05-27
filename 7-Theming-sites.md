---
title: Theming Sites
---
# Theming Sites

Themes define the overall look of a site. They work through templates which specify the HTML code, stylesheets which define the site's looks, JavaScripts which provide extra smarts interactivity, as well as image and other files web-browsers can meaningfully use. Essentially, the template engine allows you to consistently control every aspect of your site's appearance. 

Foonoo's theming system consists an asset pipeline for compiling assets, like stylesheets, scripts and images, and a templating system for injecting content into HTML (and other text) files.

## Defining a site's looks
In general, there are two ways to customize the look of a foonoo site. The simplest approach is to tweak an existing theme. This can be done by augmenting stylesheets, overriding templates templates, or modifying other asset files like images and scripts. The other approach, which offers better customizability, is to create new themes from scratch. 

For the rest of this chapter, we will briefly discuss both approaches to styling and theming foonoo sites. Before we go through these approaches, however, it will be worth taking some time to look at foonoo's asset pipeline and its templating engine.


## Template Engine
In foonoo, templates define the HTML code themes generate by supplying partial code that have gaps to be filled in with information later. Templating in foonoo is achieved through mechanisms that allow different templating languages to transparently transform templates into HTML (or other required text files). By default, foonoo supports templates written in either pure PHP, Mustache, or Smarty. 

### Finding Templates
When generating sites, the templating system determines which engines to use according the extension of the template file. The template files themselves are discovered according to a fixed, pre-defined file path hierarchy. Templates can exist anywhere in the hierarchy, however, those found in earlier paths tend to override any subsequent ones.

Templates are searched as follows:

- First, templates in the `_foonoo/templates` directory are searched and applied first. These templates will typically be supplied by you, the person building the site, and they carry the highest priority to override any other templates.
- Next, templates in special template paths supplied through the `templates` configuration of the `site.yml` file are searched. These templates can also be supplied by you, the site designer, and they are useful when you want to add your own templates outside the `_foonoo` directory.
- Afterwards, templates from the current active theme are searched. These templates are supplied by theme designers and are expected to be used by the theme. Most template requests are expected to resolve here, and most templates that can be overridden in earlier paths will be found here.
- Finally, the built in templates from foonoo's tag parser are searched. The templates here are built into foonoo, and they are meant to be used for generating the outputs of the built-in text parser. 


## Theming by Overriding Existing Templates 
Now that we know how to find templates, how do we override them? Well, it's quite simple: the actual templates available at any time are mainly defined by the active theme and foonoo's tag parser. To override those, your best option will be to create your own templates and place them in the `_foonoo/templates` directory.

As an example, let's override the layout of the Ashes theme. To do this, you could create a `layout.tpl.php` file and place it into the `_foonoo/templates` directory. This template is required by Ashes to wrap all rendered content. A PHP variable named `$body`, which contains the rendered HTML for any content, is exposed to the layout. You can put the following code into the `layout.tpl.php` file:

````php
<html>
	<head><title>Some Title Site!</title></head>
	<body>
		<h1>Some Title Site</h1>
		<hr/>
		<?= $body ?>
	</body>
</html>
````

Now, if you go ahead and place this `layout.tplphp` file into the `_foonoo/templates` directory of our earlier [[example|Introduction]], you should have the following output:

[[The site after the layout code above has been applied|hello_layout_screenshot.png|figure="frame"]]

Neat! Right? Well, if you look carefully you should realize a big problem. Compared to the earlier example, this output is devoid of any styling, and rightfully so, because all the styling is supplied by Ashes whose template we just overrode. But even more prominently, you should notice that only the raw HTML code was output. This is because the HTML code for the content has been escaped by the template engine. To fix this escaping, you can go ahead and use the following layout code, which has the content unescaped by changing `$body` to `$body->u()`. 

````php
<html>
	<head><title>Some Title Site!</title></head>
	<body>
		<h1>Some Title Site</h1>
		<hr/>
		<?= $body->u() ?>
	</body>
</html>
````

And this should now be properly rendered as:

[[A properly rendered output from the custom template|hello_improved_layout_screenshot.png|frame="figure"]]

We just overrode the default layout! The default site builder has several other templates we can override. Heck, we can also define our own templates to be used within our overridden template. The possibilities for extending the look of your foonoo sites are endless.

## Asset Pipeline
Assets used in sites are assembled and processed through a built in assets pipeline. This asset pipeline is built such that site designers can easily inject their own assets, such as custom javascripts, stylesheets, images, or other downloadable content, into the site build process. 

Much of the asset pipeline can be accessed through either the `site.yaml` file, or while defining themes. In fact, for themes defined as part of thmes, the pipeline can either be defined through YAML configuration files or dynamically through PHP code.

The asset pipeline 

## Creating Themes from Scratch
