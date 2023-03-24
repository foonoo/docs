# Writing with Foonoo
As you may already know, foonoo handles content by converting text files (currentl Markdown) to your desired output format (currently HTML). However, before foonoo converts any text files, a pre-processor is ran over every file to extract certain foonoo specific tags and other front matter information.

Front matter information is provided at the very begining of every page, and through this information, meta details about a page can be supplied. You can set a title, specify an author, give the page a unique id, and you can also provide other site-generator specific information like the taxonomy of a blog post. 

Foonoo tags, on the other hand, are supplied inline with your content, and they make it easier to perform tasks, like linking between foonoo pages, embedding media into pages, or listing a table of contents. Additionally, third party plugins and extensions have the ability to introduce their own tags to enrich the writing process within foonoo.

# Frontmatter
Whenever extra meta information about a pages is to be supplied to foonoo, front matter formatted as YAML can be supplied. To distinguish and delimit the front matter data, the YAML code must be braced between two lines of four dashes, `----`. 

# Tags

## Structure of Foonoo Tags
Foonoo tags are heaviliy inspired by Github's gollum wiki tags. Every tag starts with a pair of square brackets and end with same. Thus a simple foonoo tag will look something like this: `[[sometag]]`. Tags can have additional arguments that can be passed after a vertical bar (or pipe) character, `|`.

## All Built In Tags
The following are the tags currently built into foonoo.

### Link Tag
The link tag is the simplest of the foonoo tags. It allows you to link to other pages within a site. You can use this tag by putting either the title of the page or a page's ID int
