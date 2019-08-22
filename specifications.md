# Elm Syntax Highlighting

**MUST** look nice with default color theme of the editor.

**MUST** have excellent install instructions. Use [these](https://github.com/evancz/elm-syntax-highlighting/blob/master/install/mac.md) as a reference.

**MUST** have uninstall instructions like [these](https://github.com/evancz/elm-syntax-highlighting/blob/master/uninstall.md).

**CAN** help with indenting newlines appropriately.

**MUST NOT** have configuration options.

<br/>

# Elm Format on Save

**MUST** search `PATH` to find `elm-format`.

**MUST** give helpful message if `elm-format` is not found, linking to troubleshooting document like [this](https://github.com/evancz/elm-format-on-save/blob/master/troubleshooting.md).

**MUST** run _before_ file is saved to disk. (i.e. buffer sent to `elm-format --stdin` and output replaces the current buffer)

**MUST** have install/uninstall instructions like [this](https://github.com/evancz/elm-format-on-save#install) and [this](https://github.com/evancz/elm-format-on-save/blob/master/uninstall.md).

**CAN** have [these](https://github.com/evancz/elm-format-on-save/blob/master/elm-format-on-save.sublime-settings) configuration options.

**CAN** provide a keyboard shortcut.


<br/>

# Elm Make this File

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

