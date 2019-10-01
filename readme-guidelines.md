# README Guidelines

It can be really difficult to get an editor set up.

These guidelines aim to help make this process as easy as possible.


## README Skeleton

We recommend using a `README.md` skeleton like this:

```markdown
# Elm Plugin for X

## Install

- [Mac](install/mac.md)
- [Linux](install/linux.md)
- [Windows](install/windows.md)


<br/>

## Highlighted Features

- [Compile this file](features/compile-this-file.md) (Ctrl+B)
- [Format this file](features/format-this-file.md) (Cmd+K Cmd+F)


<br/>

## Additional Features

- [Format on Save](features/format-on-save.md) ([enable](features/format-on-save.md#enable))
- [Jump to Definition](features/jump-to-definition.md) (Cmd+Click)
- [Find Usages](features/find-usages.md) (Ctrl+Shift+U)
- [Bulk Rename](features/bulk-rename.md) (Ctrl+R)
- ...
```

The rest of this document gets into the particulars of each section. Which details are important? Why are they important?


## Guidelines for "Install"

**Location:** This is right at the top so it is easy to find.

Many editors come with a bunch of pre-installed plugins, so people may have been using the editor for years without needing to know how install new plugins.

This is the most important information in the whole README because it blocks people from using any of the features.

**Link:** The link should go to documents that explain all the tricky corner cases.

Use the install instructions for the Sublime Text as a model:

- [Mac](https://github.com/evancz/elm-syntax-highlighting/blob/master/install/mac.md)
- [Linux](https://github.com/evancz/elm-syntax-highlighting/blob/master/install/linux.md)
- [Windows](https://github.com/evancz/elm-syntax-highlighting/blob/master/install/windows.md)

It is possible to do all this with keyboard shortcuts, but I found that the directions were easiest to follow when they just used big images with arrows like this.

Having the images be specific to the operating system makes people a lot more confident that they are doing things correctly.

The bold text in those directions is also important. Emphasize the essentials of each image in text just in case!


## Guidelines for "Highlighted Features"

**Purpose:** Avoid overwhelming newcomers with features.

It can be overwhelming to see a bunch of possibilities all at once.

Having fewer bullets somehow makes them easier to understand.

**Structure:** No more than three very short bullets.

Bullets that fit on one line are way easier to read, particularly if they are under five words.

Start with a link to a file explaining the feature in more detail. (Guidelines for these files are in the next section.) Then have the keyboard shortcut. Specify explicitly if the keyboard shortcut is different between Mac, Linux, and Windows.

**Selection:** Pick keyboard shortcuts that a newcomer would want.

Newcomers are mostly just trying to get a file compiling on their computer. They are often stressed out because they have recently had to install software, so **pick things that do not require more installation**.

Newcomers may not be super familiar with all Elm features yet (e.g. types) so try to **pick things that do not rely on knowing a bunch of things already**.


### Guidelines for "Additional Features"

These should look basically the same as the "Highlighted Features" except that there are more of them.

Each feature should have an entry in the `features/` directory.

Those files would be something like this:

```markdown
# Format On Save

Run `elm-format` whenever you save a file.

This is useful for Elm projects with many team members. You can save
time in code review if your files are just always formatted this way.

This feature may lead to slight delays (<500ms) when saving.


<br>

## Enable

... instructions ...


<br>

## Demo

![format-on-save-demo](images/format-on-save-demo.png)

```

The first line is a short description of the feature. Avoid wrapping to a second line!

The second line is a description of who wants it and why.

The third line is a performance disclosure. It explicitly describes any RAM overhead or battery implications for people who care about that sort of thing. "Enabling this feature will keep about 10MB in memory per file" or "Enabling this feature will do work on each keystroke, so it will shorten battery life." These should be as quantitative as possible, matching up with your [perf table](perf-table.md).



## Other Content?

Having more things in a document somehow makes it harder to understand overall, so it is best to have as few sections as possible.

Try to answer the questions of newcomers directly, and provide links to materials that people may find interesting once they have been using your plugin for a while.
