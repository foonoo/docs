# Building Sites

We've already established Foonoo's multi-site generator architecture, and we've also briefly looked at how it ships with a default site generator. In this chapter, we'll go into the details of how sites can be built with this default site generator. By the end of this chapter you should be able to build simple sites, like a personal home page, or complex ones, like the one serving this documentation.

Foonoo's default site generator provides a unique way of combining templates, text files, and even data in some cases to generate sites. For most parts, the default generator depends heavily on its themes to provide most of the features needed to tie sites together, like menus. In this section, we will take a look at how the default site generator works, and we'll look at how the default theme that ships with Foonoo allows us to build complex sites.

## The Default Site Generator and Theming
Sites in foonoo always have themes enabled when being generated. When you're simply rendering text files, the default site generator and its default theme are used. The default theme that ships with foonoo's default site generator is called Ashes. Ashes is highly configurable, and it allows you to significantly personalize sites to your taste. But you don't have to stick with Ashes; you always have the opportunity to use your own themes.

When generating simple sites, where you're merely rendering Markdown files, Ashes simply wraps the processed HTML output of the text file with HTML code that attaches a simple stylesheet to decorate the text. Beyond this blank default however, Ashes can be configured to provide other valuable features, like title bars, navigation blocks, and even special colour schemes. All configurations for Ashes can be set in the main `site.yml` file.

## Let's build a sample site
Before delving into the configuration of Ashes, and how to build sites with foonoo in general, let's consider the following files as our content:

Here's `Introduction.md`:

```Markdown
---
title: Introduction
---

# Introduction

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut 
labore et dolore magna aliqua. Scelerisque felis imperdiet proin fermentum leo vel. Eu facilisis 
sed odio morbi quis commodo odio aenean. 

## Something Interesting
At in tellus integer feugiat. Sit amet nulla facilisi morbi tempus iaculis. Luctus accumsan 
tortor posuere ac ut consequat semper viverra. Scelerisque viverra mauris in aliquam sem 
fringilla ut morbi tincidunt. 

## Another Interesting Thing
Nunc sed augue lacus viverra vitae. Aliquet nec ullamcorper sit amet risus. Egestas sed tempus 
urna et pharetra pharetra massa massa. Nunc sed augue lacus viverra vitae congue eu consequat. 
Mattis aliquam faucibus purus in massa. 
```

And here's, `Description.md`:

```Markdown
---
title: Description
---

# Description
At in tellus integer feugiat. Sit amet nulla facilisi morbi tempus iaculis. Luctus accumsan 
tortor posuere ac ut consequat semper viverra. Scelerisque viverra mauris in aliquam sem 
fringilla ut morbi tincidunt. Quam pellentesque nec nam aliquam. 

## Some Details
Aliquet nec ullamcorper sit amet risus nullam eget felis eget. Aliquam sem et tortor consequat id 
porta nibh venenatis cras. Sed augue lacus viverra vitae congue. Vivamus at augue eget arcu 
dictum varius duis. Dui vivamus arcu felis bibendum ut tristique et egestas quis.

## Some other Details
Habitant morbi tristique senectus et. Pellentesque habitant morbi tristique senectus et. Sed 
libero enim sed faucibus turpis in eu mi. Justo donec enim diam vulputate ut.
```

Assuming we keep both of these files in a directory and run the foonoo generate command:

    foonoo generate

The output of this command should be a `_foonoo` directory along with an `output_site` directory in the same directory. The `output_site` directory will contain the output HTML files, `Introduction.html` and `Description.html`, as well as other site assets. These two files would be styled with the Ashes theme, and they should look as shown below.

[[The Introduction.md file as rendered into HTML|introduction_html.png| frame="figure"]]
[[The Description.md file as rendered into HTML|description_html.png| frame="figure"]]


### Adding a Title
With the pages in place, we can tie our site together with a common title. There's no way to tie a site together better than with a common header. We would love to have this header displayed on all the generated pages. Thankfully, Ashes has a configuration for that. Assuming we're calling this site the "Pseudo Latin Placeholder", then we can create our `site.yml` file to reflect this as follows. 

```yml
type: default
title: "The Latin Placeholder Site"
```

Note that we supplied the `type` key to refer to the site generator, which is default in this case. Once this `site.yml` is in place, another execution of `foonoo generate` should update our two pages with headers displaying our new site title.

[[The Introduction.html file with the header applied|introduction_styled.png|frame="figure"]]
[[The Description.html file with the header applied|description_styled.png|frame="figure"]]

### Adding an index page
Our site will now need a default page to display when some just visits our domain. This page, typically known as the index page, can be created by simply adding an `index.md` file to your site with any contnet you want. Apart from supplying your own `index.md` file, you could also designate one of your pages as the index page in the `site.yml` file, or you could have an automatically generated one.

To designate a page as the index, you can add an `index` key that is pointed to your preferred page to the `site.yml` file. For example, to add designate our introduction page as the index, you could make the following change to the `site.yml` file.

```yml
type: default
title: "The Latin Placeholder Site"
index: Introduction.md
```

### Adding Navigation Links
Ashes also allows for the definition of navigation links. All you have to do is provide the labels and links in your `site.yml` file, and the links will be placed on all the site headers. For our running example, if we wanted to add navigation links, our `site.yml` could look as follows:

```yml
type: default
title: "The Latin Placeholder Site"
index: Introduction.md

menu:
  - title: Introduction
    url: Introduction.html
  - title: Foonoo
    url: https://github.com/foonoo
```

This would place two navigation links: one for the `Introduction.md` page and another to foonoo's github page. Leading to a page that looks like the following:

[[The Introduction page showing the newly added menus|menu_sample.png|frame="figure"]]

### Adding a Table of Contents
When building a documentation site, like this one, or some kind of site with detailed reference material, you might want to have the table of contents displayed on the side. Foonoo—through Ashes of course—makes this process a little easier. 

The first step, as you may have already guessed, involves setting a value in the `site.yml` file. In this case, the value is `enable-toc` and you just have to set it to a boolean value of `True`. This will lead to the more matured `site.yml` file below:

```yml
type: default
title: "The Latin Placeholder Site"
index: Introduction.md

menu:
  - title: Introduction
    url: Introduction.html
  - title: Foonoo
    url: https://github.com/foonoo

enable-toc: True
```

## Rendering Custom Data
Although you're building static sites, sometimes you may have the need to inject some dynamic data. For example, you may want to add an easy to manage list of your projects to your personal home page, or you want to showcase your ever-growing recipe database. Regardless of your needs, Foonoo provides the infrastructure for you to inject, render, and style structured YML or JSON data for your site. 

Data to be rendered must be YAML or JSON formatted files placed in the `__foonoo/data` directory. The file's name should only alpha-numeric characters (preferable lower-case) and nothing else.

For example, if you wanted to add a list of projects to a site, you could start with by defining the template for rendering this data. This template could just be put directly into the site directory where other content reside. Whenever the site is rendered, a page with the same name as the template will be generated. 

In the case of this example, since you are creating a page to list projects, you could name this template page `my_projects.mustache`—explicitly implying you'll be using the mustache templating system.

At this point, you can put the following code into the `my_projects.mustache` file:

````html
<h1>Projects</h1>

{{#projects}}
	<h2>{{name}}</h2>
	<p>{{description}}</p>
{{/projects}}
````

Or if you wanted to use good old PHP, you could go with the following:

````php
<h1>Projects</h1>
<?php foreach($projects as $project): ?>
    <h2><?= $project["name"] ?></h2>
    <p><?= $project["description"] ?></p>
<?php endforeach; ?>
````

and save this file as `my_projects.tplphp`.

With these in place, you can create your `_foonoo/data/projects.yml` data file as follows:

````yaml
- name: Foonoo
  description: A tool for building static websites.
- name: Ntentan
  description: A manifestation of the sunken cost fallacy.
- name: Ananse Basic
  description: A programming language that lives in a deluded person's mind.
````

Or if you prefer JSON as your data format, you could go with the a `_foonoo/data/projects.json` as follows:

````JSON
[
    {
        "name": "Foonoo", 
        "description": "A tool for building static websites."
    },
    {
        "name": "Ntentan", 
        "description": "A manifestation of the sunken cost fallacy."
    },
    {
        "name": "Ananse Basic", 
        "description": "A programming language that lives in a deluded person's mind."
    }
]
````

Once these are in place, generating your site should produce a `my_projects.html` file that looks like below.

[[The projects listing as rendered by foonoo | data_listing_screenshot.png | frame="figure"]]
