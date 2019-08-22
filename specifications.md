# Specifications

The goal of these specifications is to manifest the following design aesthetic:

**Great performance. Pleasant defaults. Minimal configuration.**

There are currently specifications for three separate plugins:

- [Elm Syntax Highlighting](#elm-syntax-highlighting) - Just add syntax highlighting.
- [Elm Format on Save](#elm-format-on-save) - Run `elm-format` on save.
- [Elm Make this file](#elm-make-this-file) - Run `elm make` on the current file.

We get some worthwhile benefits by separating out the functionality. First, beginners can start with Elm Syntax Highlighting and not have to worry about their `PATH` at all. Second, plugins are more likely to be stable and reliable thanks to their smaller scope. If one plugin is messed up, it is easy to remove it or swap it out with an alternative.


<br/>

## Elm Syntax Highlighting

**MUST** look nice with default color theme of the editor.

**MUST** have excellent install instructions. Use [these](https://github.com/evancz/elm-syntax-highlighting/blob/master/install/mac.md) as a reference.

**MUST** have uninstall instructions like [these](https://github.com/evancz/elm-syntax-highlighting/blob/master/uninstall.md).

**CAN** help with indenting newlines appropriately.

**MUST NOT** have configuration options.

<br/>


## Elm Format on Save

**MUST** search `PATH` to find `elm-format`.

**MUST** give helpful message if `elm-format` is not found, linking to troubleshooting document like [this](https://github.com/evancz/elm-format-on-save/blob/master/troubleshooting.md).

**MUST** run _before_ file is saved to disk. (i.e. buffer sent to `elm-format --stdin` and output replaces the current buffer)

**MUST** have install/uninstall instructions like [this](https://github.com/evancz/elm-format-on-save#install) and [this](https://github.com/evancz/elm-format-on-save/blob/master/uninstall.md).

**CAN** have [these](https://github.com/evancz/elm-format-on-save/blob/master/elm-format-on-save.sublime-settings) configuration options.

**CAN** provide a keyboard shortcut.

<br/>


## Elm Make this File

**MUST** search `PATH` to find `elm`.

**MUST** give helpful message if `elm` is not found, linking to troubleshooting document like [this](https://github.com/evancz/elm-format-on-save/blob/master/troubleshooting.md).

**MUST** be triggered by a keyboard shortcut, listed prominently in the README.

**MUST** save before running `elm make`.

**MUST** run `elm make --output=/dev/null --report=json $CURRENT_FILE_PATH` from `$CURRENT_FILE_DIR`. The `elm make` binary can run from subdirectories as of 0.19.1, so you should rely on it to quickly and reliably find the `elm.json` file.

**MUST** accurately reproduce error message colors in the editor.

**MUST** only list error messages for the current file. If there are errors in dependencies, give a message like this:

```
I found errors in some of your imports:

    src/Student.elm
    src/Slideshow.elm

Fix the errors in those files first!
```

**MUST** have install/uninstall instructions like [this](https://github.com/evancz/elm-format-on-save#install) and [this](https://github.com/evancz/elm-format-on-save/blob/master/uninstall.md).

**MUST NOT** have configuration options.

**MUST NOT** run on save or on key press.


<br/>

# Adding Other Specifications

Any future specifications should maintain the following design aesthetic:

**Great performance. Pleasant defaults. Minimal configuration.**

That is currently done by building editor plugins around high quality command line tools. Starting with command line tools encourages implementations that are focused, performant, and well-designed.

So if people want more plugins listed in this repo, proceed by working on a command line tool first. Possible designs include:

- [`elm-find`](https://github.com/elm/projects/#elm-find)
- [`elm-refactor`](https://github.com/elm/projects/#elm-refactor)

The benefit of working on command line tools are (1) they can focus on performance, (2) they will not have a permanent memory overhead, (3) they promote consistency across editor plugins, and (4) they can be used even if there is no corresponding editor plugin.

Once things like this exist, we can evaluate if it is possible to create a nice specification for any editor integrations.
