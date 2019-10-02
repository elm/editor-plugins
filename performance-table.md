# Performance Table

Editor plugins may choose to have a file named `performance-table.md` that outlines the performance costs of various features.


<br>

## Goals

1. Learn how different editors implement features.
2. Try to think of ways to bring down costs.


<br>

## Example

When you create a `performance-table.md` for your plugin, it should be a table something like this:

| Feature            | Start Speed      | Incremental Speed | Constant RAM Overhead | Cumulative CPU Costs | Battery Implications |
|--------------------|------------------|-------------------|-----------------------|----------------------|----------------------|
| Compile this file  | ~1s per 100k LOC | <500ms            | 0                     | on keyboad shortcut  | minimal              |
| Format this file   | <1s              | <1s               | 0                     | on keyboad shortcut  | minimal              |
| Format on Save     | <1s              | <1s               | 0                     | on save              | notable              |
| Jump to Definition | ~2s per 100k LOC | <100ms            | 100MB                 | on key stroke        | significant          |
| Find Usages        | ↑                | ↑                 | ↑                     | ↑                    | ↑                    |
| Bulk Rename        | ↑                | ↑                 | ↑                     | ↑                    | ↑                    |

These numbers are just for example. They are based on intuitions from profiling the compiler and measuring heap allocations.

It may be nice to summarize this information above the table with a note like "If your computer has less than 4GB of RAM or fewer than 4 CPU cores, you may be better served by a lighter-weight text editor like X."


<br>

## Motivation

Not everyone has a great computer, and they may want to enable/disable features depending on if they will use too much RAM or decrease battery life.

Based on this [Firefox Public Data Report](https://data.firefox.com/dashboard/hardware) about hardware:

- 50% of people have 4GB or RAM or less
- 60% of people have two cores or less

My computer happens to have 4GB of RAM and two cores actually, but the idea here is that many people getting started with Elm are not professional developers. They may be working from a computer lab at school or from a laptop they got to work on group assignments and receive email.

I think making these costs transparent will ultimately make things nicer for these folks.


<br>

## Case Study

It may be "cheap" to parse a file on every key stroke in the sense that it is not perceptable, but that does not mean it is particularly cheap compared to other options.

With features like "jump to definition" you may go hours or days without using it. So a "parse on key stroke" strategy may end up parsing a file hundreds or thousands of times before the relevant feature is invoked.

This feature could probably work just as well if the reparses were less frequent. For reference, the compiler is able to do incremental compiles in about 300ms even when projects are in the 300k LOC range, but without keeping anything in RAM or doing any work between `elm make` invocations. That kind of time delay is acceptable for features like "Jump to Definition". That would be significantly cheaper!

It is hard to get things _that_ fast though, but you can still improve performance by throttling the incremental work. Maybe it can be done "on save" or "on save once an hour" to improve battery life without perceptably degrading the editor experience.

(This is the theory behind the [`elm-find`](https://github.com/elm/projects#elm-find) project.)
