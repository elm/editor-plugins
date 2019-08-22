# Specifications

There are currently specifications for three types of plugins:

- [Elm Syntax Highlighting](#elm-syntax-highlighting) - Just add syntax highlighting.
- [Elm Format on Save](#elm-format-on-save) - Run `elm-format` on save.
- [Elm Make this file](#elm-make-this-file) - Run `elm make` on the current file.

It is fine to create other plugins, but that should be in addition to the core three specified here.

The goals of having clear specifications like this include:

- Easy for beginners to get started with just Elm Syntax Highlighting.
- Easy for people to switch between editors.
- User experience is a strict improvement over command line equivalent.
- Performance is excellent. Operations are in the <300ms range.


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

So if people want more features in editors, it may make sense to work on command line tools first. Some ideas I have in mind are:

- [`elm-find`](https://github.com/elm/projects/blob/master/elm-find.md)
- [`elm-refactor`](https://github.com/elm/projects/blob/master/elm-refactor.md)

The benefit of working on command line tools are (1) they can focus on performance, (2) they will not have a permanent memory overhead, (3) they promote consistency across editor plugins, and (4) they can be used even if there is no corresponding editor plugin.
