# Elm Editor Plugins

Elm users should have a consistent and pleasant experience across a broad range of editors.

A core team member has reviewed each of the plugins listed here to make sure it is performant and cosistent with the community guidelines.


## Verified Editor Plugins

**Sublime Text**

  - [Elm Syntax Highlighting](https://github.com/evancz/elm-syntax-highlighting/)
  - [Elm Format on Save](https://github.com/evancz/elm-format-on-save)



## Adding Plugins to the List

The goal of this project is to promote consistency and quality in Elm editor plugins, so a plugin must meet certain specifications to be listed here.

There are specifications for three types of plugins:

- [Elm Syntax Highlighting](plugin-specifications.md#elm-syntax-highlighting) - Just add syntax highlighting. Must look good with the default color theme of the editor. Must have excellent install instructions.
- [Elm Format on Save](plugin-specifications.md#elm-format-on-save) - Run `elm-format` on save. Must run _before_ buffer is saved to disk.
- [Elm Make this file](plugin-specifications.md#elm-make-this-file) - Run `elm make --output=/dev/null` on the current file. Must be triggered by keyboard shortcut. Must not run on save.

It is fine to have other plugins as well, but that should be in addition to these core three that are focused on speed, reliability, and simplicity.

If you are interested in creating one of these plugins for an editor, check out [the complete specifications](plugin-specifications.md)!


## Future Work

Any future work should maintain the following design aesthetic:

**Great performance. Pleasant defaults. Minimal configuration.**

That is currently done by building editor plugins around high quality command line tools. Starting with command line tools encourages implementations that are focused, performant, and well-designed.

So if people want more features in editors, it may make sense to work on command line tools first. Some ideas I have in mind are:

- [`elm-find`](https://github.com/elm/projects/blob/master/elm-find.md)
- [`elm-refactor`](https://github.com/elm/projects/blob/master/elm-refactor.md)

The benefit of working on command line tools are (1) they can focus on performance, (2) they will not have a permanent memory overhead, (3) they promote consistency across editor plugins, and (4) they can be used even if there is no corresponding editor plugin.
