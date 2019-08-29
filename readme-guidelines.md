What follows is a skeleton for a plugin README.md

* * *

# Elm Plugin for X

## Install

Follow the directions [here](install.md) to install.

## Simple Features

- [Compile this file](features/compile-this-file.md) (Ctrl+B)
- [Format this file](features/format-this-file.md) (Cmd+K Cmd+F)


## Advanced Features

- [Format on Save](features/format-on-save.md) ([enable](features/format-on-save.md#enable))
- [Jump to Definition](features/jump-to-definition.md) (Cmd+Click)
- [Find Usages](features/find-usages.md) (Ctrl+Shift+U)
- [Bulk Rename](features/bulk-rename.md) (Ctrl+R)
- ...


* * *

**Guidelines for Install:**

This should be the top thing so it is easy to find.

If the installation is through a GUI, it should link to `install.md` that has screenshots and arrows showing exactly how to do it. If it varies by platform, there should be links to `install/mac.md`, `install/linux.md`, and `install/windows.md`.


**Guidelines for Features:**

Editor configuration is really costly for beginners, but quite cheap for experts. So the main goal here is to get a set of defaults that works for beginners (taking into account high schoolers on hand-me-down laptops) and easy instructions for advanced users who want different trade offs.

**Guidelines for Simple Features:**

There should be three of these at most. The point here is "if you still have energy after the install instructions, here are three useful things that will 100% work if you try them."

These should not have constant RAM overhead or battery implications.


**Guidelines for Advanced Features:**

These should all have an entry in the `features/` directory.

Those files would be something like

```markdown
# Format On Save

Run `elm-format` whenever you save a file.

This is useful for Elm projects with many team members. You can save time in code review if your files are just always formatted this way.

This feature may lead to slight delays (<500ms) when saving.

## How to Enable

... instructions ...

## Demo

gif of feature if that is necessary
```

The first line is a short description of the feature (no wrap)

The second line is a description of who wants it and why.

The third line is a "perf disclosure". If the feature has RAM overhead or battery implications, that should be outlined explicitly. "Enabling this feature will keep about N MB in memory per file" or "Enabling this feature will do work on each keystroke, so it will shorten battery life." These should try to be as quantitative as possible!
