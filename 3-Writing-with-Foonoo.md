# Writing with Foonoo
As already stated, foonoo generates content by converting text files (currently in Markdown) to your desired output (currently in HTML). However, before foonoo converts any text files, a pre-processor extracts foonoo specific tags and other front matter information for internal use.

Front matter information allows you to include meta details about pages. With front matter data you can add attributes like,  titles, authors, unique ids, and you can also provide other site-generator specific information like the taxonomy of a blog post. Front matter must always be placed at the very beginning of the contents text. 

Foonoo tags, on the other hand, are supplied inline with your content, and they make it easier for you to perform tasks, like linking between foonoo pages, embedding media into pages, or listing a table of contents. Additionally, third party plugins and extensions have the ability to introduce their own tags to enrich the writing process within foonoo.

# Frontmatter
Whenever extra meta information about a page is to be supplied to foonoo, front matter formatted as YAML can be used. To distinguish and delimit the front matter data, the YAML code must be braced between two lines of three (or four) dashes, `---`. Also, it is required that the front matter information appears first before the page's content, if it is to be recognized.

The following example shows how front matter can be used to specify the title of some content:

````
---
title: A front matter demonstration
author: Ekow Abaka 
---

This is just meant to show how front matter can easily be added to any page in foonoo.
````

Technically, there are no required front matter tags. The only requirement is that your front matter text must be valid YML content, structured as an object of key-value pairs. Most front matter tags are specified and consumed by the individual site generators. 

## How titles work in Foonoo
Regardless of that, foonoo still recognizes the `title` and `id` tags and uses them whenever they are found. In cases where a `title` tag doesn't exist, foonoo just uses the first highest level header (H1) in the document as a title, or the file name if the (H1) tag doesn't exist. Also, the title doubles as the page's id if you don't provide an id tag in the front matter.


# Tags
Foonoo tags are heaviliy inspired by Github's gollum wiki tags. Every tag starts with a pair of opening square brackets and ends with a closing pair of square brackets. Thus, a simple foonoo tag will look something like this: `[[sometag]]`. Tags can have additional arguments that can be passed after a vertical bar (or pipe) character, `|`.

Some tags can span blocks of text, and for those, there is always an opening tag and a closing tag. The opening block tag is similar to the inline tags—where you have a pair of square brackets with the tag definition. The closing block tags take inspiration from HTML tags and precede the tag name with a forward slash `/`. As an example, the following shows how a block of text can be marked as a warning:

````
[[block:warning]]
This is supposed to be rendered as a warning with some fancy icons and text.
[[/block:warning]]
````

## Built In Tags
The following are the tags currently built into foonoo.

### Link Tag
The link tag is the simplest of the foonoo tags. It allows you to link out to external pages. You can consider it as an alternative to Markdown's internal link tag. To use this tag, place your link between the pairs of square brackets. For example, to link to wikipedia, you can use: `[[https://wikipedia.com]]`

### Foonoo Page Link Tag
It allows you to link to other pages within a site by just providing its title or id. You can use this tag by putting either the title of the page or a page's ID int

For example to link to 

### Image Tag

### Table of Contents Tag

### Block Tags