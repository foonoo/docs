# Using Plugins

Plugins provide a great way to extending Foonoo's, already fantastic 😉, features. By taking advantage of Foonoo's extensible architecture, you can build in features that you need for your own work.

## Installing Plugins
With foonoo still in active development, there are currently no automated ways to install plugins. For now, you may need to get your hands a little dirty. The current approach for installing plugins is to manually checkout a plugin's code from github into either foonoo's local settings directory or a user specified directory. 

Foonoo's local settings directory can be found in `$XDG_DATA_HOME/foonoo/` or `~/.local/share/foonoo/` on Linux, `LOCALAPPDATA\foonoo\` on Windows, and `$HOME/Library/Application Support/foonoo/` on macos.

In cases where you want to keep plugins in a designated directory, you can use either the `-P` or `--plugin-path` option to point to the directory holding your plugins.

## Using Plugins
All plugins needed for a site must be listed in the <code>site.yml</code> file. For example, to build a site with the 
`foonoo/highlight` and the `foonoo/responsive-images` plugins, you could use the following:

```yml
plugins:
- foonoo/highlight
- foonoo/responsive-images</code>
```

... and if you wanted to set the parameters of one of the plugins, you could go with the following ....

```yml
plugins:
- foonoo/highlight:
    - style: rainbow
- foonoo/responsive-images</code>
```
