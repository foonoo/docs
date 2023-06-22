# Building Sites

Foonoo's default site generator provides a unique way of combining templates and text files, as well as data to generate sites. For most parts, the default site generator is heavily dependent on the themes to provide a lot of the features to tie sites together. Regardless, the site generators is still capable of some site building features on its own. In this section, we will take a look at how the default site generator could be used, and we would look at how the default theme allows to build even more complex sites.

## The Default Generator and Theming
Sites in foonoo always have themes enabled when being built. When simply rendering text files, the default site generator and its default themes are used. The default site generator ships with a default theme that is highly configurable. For example, if you were to place 

In its initial setting, the theme simply wraps the processed HTML output of the text file with an HTML wrapper that provides a stylesheet to decorate the text. Beyond this blank default, this theme can be configured to provide title bars, navigation blocks, and even special colour schemes.

To theme a text file, just place it in a directory and execute foonoo with said directory as input.

## How Templates are Resolved

## Overriding Layouts

## Using Custom YML Data

## Adding Menus

## Adding Content Navigation

## Adjusting Color Schemes