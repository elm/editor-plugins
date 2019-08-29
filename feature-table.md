# Feature Table

The goal of this table is to start learning about how features are implemented in various editors.

From there, the goal is to bring the performance costs down such that more things can be enabled by default.


## Example

These are all made up numbers, but made up based on intuitions from profiling the compiler and measuring heap allocation:

| Feature            | Start Speed      | Incremental Speed | constant RAM overhead | cumulative CPU costs | Battery Implications |
|--------------------|------------------|-------------------|------------------------|---------------------|----------------------|
| Compile this file  | ~1s per 100k LOC | <500ms            | 0                      | on keyboad shortcut | minimal              |
| Format this file   | <1s              | <1s               | 0                      | on keyboad shortcut | minimal              |
| Format on Save     | <1s              | <1s               | 0                      | on save             | notable              |
| Jump to Definition | ~2s per 100k LOC | <100ms            | 100MB                  | on key stroke       | significant          |
| Find Usages        | ~2s per 100k LOC | <100ms            | 100MB                  | on key stroke       | significant          |
| Bulk Rename        | ~2s per 100k LOC | <100ms            | 100MB                  | on key stroke       | significant          |


## Goal

The goal is to start with tables like this and then figure out how we can bring down various costs.

For example, I think a project like [`elm-find`](https://github.com/elm/projects#elm-find) could bring the costs down a ton for the "Jump to Definition" variations. It could bring the constant RAM overhead down to zero, and from there it depends on performance. If start speed is really fast, maybe it can only run on keyboard shortcut. If that is >500ms then we could try doing "rebuild indexes on save" such that we can get the incremental speed faster without incurring to much cumulative CPU and degrading battery life too much.

As we start bringing performance costs down (and get more things integrated into `elm` over time) the dynamics of which features should be enabled by default starts to change.
