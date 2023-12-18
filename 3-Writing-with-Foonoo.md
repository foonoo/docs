---
title: Writing with Foonoo
---
# Writing with Foonoo
As already stated, foonoo generates content by converting text files (currently in Markdown) to your desired output (currently in HTML). However, before foonoo converts any text files, a pre-processor extracts foonoo specific tags and other front matter information for internal use.

Front matter information allows you to include meta details about the content you write. You can add attributes like, titles, authors, unique ids, and you can also provide other site builder specific information, like the taxonomy of a blog post. Front matter must always be placed at the very beginning of the contents text. 

Foonoo specific tags, on the other hand, are supplied inline with your content. Their job is to make it easier for you to perform tasks, like linking between foonoo pages, embedding media into pages, or listing a table of contents. Additionally, third party plugins and extensions have the ability to introduce their own tags which enriches the writing process within foonoo.

## Front-matter
Whenever extra meta information about a page is to be supplied to foonoo, front matter formatted as YAML must be used. To distinguish and delimit the front matter data, the YAML code must be braced between two lines of three (or four) dashes, like so `---`. Also, it is required that the front matter information appears first before the page's content, if it is to be recognized.

The following example shows how front matter can be used to specify the title of some content:

````
---
title: A front matter demonstration
author: Ekow Abaka 
---

This is just meant to show how front matter can easily be added to any page in foonoo.
````

Technically, there are no required front matter tags. The only requirement is that your front matter text must be valid YML content, structured as an object of key-value pairs. Most front matter tags are consumed by the individual site builder. 

Regardless of the lack of explicitly defined front matter tags, foonoo still recognizes the `title` and `id` tags and uses them whenever they are found. In cases where a `title` tag doesn't exist, foonoo just uses the first highest level header (with H1 as the highest) in the document as a title, or the title defaults to the file name if the (H1) tag doesn't exist. Also, the title doubles as the page's id if you don't provide an id tag in the front matter.

## Tags
Foonoo tags are heavily inspired by Github's gollum wiki tags. Every tag starts with a pair of opening square brackets and ends with a closing pair of square brackets. Thus, a simple foonoo tag will look something like this: `[[sometag]]`. Tags can have additional arguments that can be passed after a vertical bar (or pipe) character, `|`.

Some tags can span blocks of text, and for those, there is always an opening tag and a closing tag. The opening block tag is similar to the inline tags—where you have a pair of square brackets with the tag definition. The closing block tags take inspiration from HTML tags and precede the tag name with a forward slash `/`. As an example, the following shows how a block of text can be marked as a warning:

````
\[[block:warning]]
This is supposed to be rendered as a warning with some fancy icons and text.
\[[/block:warning]]
````

## Escaping Tags
In the case where an underlying text processor may require the double square bracket, or you want to have a double square bracket in your work for some reason, you could escape a tag by prefixing it with a backslash like so, `\[[`. 

It is also worth noting that the foonoo tag processor will regurgitate any tags it fails to properly interpret to minimize disruptions. This means, for most use cases of square brackets other that the ones explicitly for foonoo, you may not need to supply the escape character.

## Using Built In Tags
Currently, foonoo ships with default tags for handling links, loading images and media, displaying special blocks of text, and generating navigational tools (like as Tables of Content). It is worth noting that foonoo tags are extensible and it's possible for plugins to create their own tags, or even redifine the behaviour of inbuilt tags. The following sections describe the tags built into foonoo by default.

### Foonoo Link Tag
The link tag is the simplest of the foonoo tags. It allows you to link to other pages within a site by just providing its title or id. You can use this tag by putting either the title a page in between a pair of double square brackets. 

For example, to link to a page titled "Something Surreal", you could use:

````
\[[Something Surreal]]
````

And if you wanted to provide an alternate link text, instead of the page's title, you could supply it as follows:

````
\[[Find out about something surreal|Something surreal]]
````

Remember that for pages without explicit titles, the first header is assumed as the title, and in cases where an id does not exist, the title represents an id. Also, for the purposes of making page links, when ids supercede titles for page resolution.

### Hyperlink Tag
To provide hyperlinks to resources outside your foonoo site, you could use the hyperlink tag. Just like the link tag, the hyperlink tag requires you to place the link URL in between a pair of double square brackets. 

For example, to link Wikipedia, you could use:

````
\[[https://wikipedia.org]]
````

And similarly, to provide an alternate link text you could add a description as follows:

````
\[[Go to Wikipedia|https://wikipedia.org]]
````

### Image Tag
To embed an image in your content, you could use the image tag. This tag requires you to place the image filename between two pairs of square brackets. 

Note that all images referenced through this tag must be placed in the `_foonoo/assets/images` directory of the site. .

To embed an image, use the following:
````
\[[some_image.jpg]]
````

And to provide some description or alternate tags, you could extend it as follows:

````
\[[A description for the image|some_image.jpg]]
````

### Table of Contents Tag
To place the table of contents for a particular page anywhere, you could use the table of contents tag `[[__TOC__]]`. Note that this tag produces the table for the current page only. The full table of contents for the entire site is only available through themes.

### Block Tags
Block tags allow  you to decorate blocks of text. You might want to mark something as a warning, or as a note, or you might want to specify that some text should be displayed as though they were on the command line. Regardless of what you want to wrap, you can always rely on the block tags.

To open a block tag you use the `\[[block:type]]` tag at the begining of the text you want, and to close you use `[[\block:type]]`. The `type` in the block can be anything you want, provided the right CSS styles are available. By default foonoo ships with styles for `note`, `warning`, `alert`, `info`, and `commandline`.

When foonoo is writing to HTML, block tags are output as HTML divs that have special classes attached to reflect the type of block. 

