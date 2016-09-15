# Elmjutsu

A bag of tricks for developing with [Elm](http://elm-lang.org).

https://atom.io/packages/elmjutsu

## Feature Overview

* [Autocomplete](#autocomplete)

* [Go To Definition](#elmjutsu-go-to-definition)

* [Go To Symbol](#elmjutsu-go-to-symbol)

* [Find Usages](#elmjutsu-find-usages)

* [Go To Next Usage](#elmjutsu-go-to-next-usage)

* [Go To Previous Usage](#elmjutsu-go-to-previous-usage)

* [Go Back](#elmjutsu-go-back)

* [Rename Symbol](#elmjutsu-rename-symbol)

* [Toggle Sidekick](#elmjutsu-toggle-sidekick)
  * Show type hints and documentation for the symbol at cursor position.

## Requirements

* [Elm](http://elm-lang.org/install)
* [language-elm](https://atom.io/packages/language-elm)
* For `Go To Definition`:
  * [hyperclick](https://atom.io/packages/hyperclick) (optional)
* For `Autocomplete`:
  * [autocomplete-plus](https://atom.io/packages/autocomplete-plus) (installed by default)
  * [snippets](https://atom.io/packages/snippets) (optional, installed by default)

## Feature Details

### Autocomplete

Autocomplete is turned off by default.  To turn it on, check the `Enable Autocomplete` option in the package settings.

It's recommended to turn off the autocomplete feature of the [language-elm](https://atom.io/packages/language-elm) package to prevent duplicate suggestions.

This provides suggestions for imports, project symbols, and 3rd party package symbols.

![autocomplete](https://github.com/halohalospecial/atom-elmjutsu/blob/master/images/autocomplete.gif?raw=true)

You can also turn on `Enable Autocomplete Snippets` if you prefer.

![autocomplete-snippet](https://github.com/halohalospecial/atom-elmjutsu/blob/master/images/autocomplete-snippet.gif?raw=true)

### `Elmjutsu: Go To Definition`

![go-to-definition](https://github.com/halohalospecial/atom-elmjutsu/blob/master/images/go-to-definition.gif?raw=true)

If the [hyperclick](https://atom.io/packages/hyperclick) package is installed, you can also check the `Enable Hyperclick` option to jump to definition using `Ctrl` + click / `Cmd` + click (Mac).

### `Elmjutsu: Go To Symbol`

![go-to-symbol](https://github.com/halohalospecial/atom-elmjutsu/blob/master/images/go-to-symbol.gif?raw=true)

### `Elmjutsu: Find Usages`

![find-usages](https://github.com/halohalospecial/atom-elmjutsu/blob/master/images/find-usages.gif?raw=true)

### `Elmjutsu: Go To Next Usage`

If the `Usages` panel is shown, this command moves the cursor to the position of the next usage in the list.

### `Elmjutsu: Go To Previous Usage`

If the `Usages` panel is shown, this command moves the cursor to the position of the previous usage in the list.

### `Elmjutsu: Go Back`

The current cursor position is added to a navigation stack before jumping via:
  - `Go To Definition`
  - `Go To Symbol`
  - `Go To Next Usage`
  - `Go To Previous Usage`

Invoke this command to jump back to the previous position.

### `Elmjutsu: Rename Symbol`

Renames the symbol across the whole project.  Take note that this is *not* an undoable operation.  Modified modules with open editors will not be saved automatically.

![rename-symbol](https://github.com/halohalospecial/atom-elmjutsu/blob/master/images/rename-symbol.gif?raw=true)

Press <kbd>enter</kbd> to rename or <kbd>escape</kbd> to cancel.

### `Elmjutsu: Hide Usages Panel`

Closes the `Usages` panel (the panel is shown after invoking `Find Usages` or `Rename Symbol`).

### `Elmjutsu: Toggle Sidekick`
Shows the type hints and documentation for the symbol at cursor position.  The size and position of the panel can be modified in the package settings.

Example #1 (default): `Sidekick Position` = "bottom", `Sidekick Size` = 0 (Automatically resizes to fit content.)

![sidekick1](https://github.com/halohalospecial/atom-elmjutsu/blob/master/images/sidekick1.gif?raw=true)

Example #2: `Sidekick Position` = "bottom", `Sidekick Size` = 30 (Just shows the type hints.)

![sidekick2](https://github.com/halohalospecial/atom-elmjutsu/blob/master/images/sidekick2.gif?raw=true)

Example #3: `Sidekick Position` = "right", `Sidekick Size` = 300

![sidekick3](https://github.com/halohalospecial/atom-elmjutsu/blob/master/images/sidekick3.gif?raw=true)

## Keybindings

Here is an example:
```
'atom-text-editor:not([mini])[data-grammar^="source elm"]':
  'f12': 'elmjutsu:go-to-definition'
  'ctrl-r': 'elmjutsu:go-to-symbol'
  'shift-f12': 'elmjutsu:find-usages'
  'f8': 'elmjutsu:go-to-next-usage'
  'shift-f8': 'elmjutsu:go-to-previous-usage'
  'ctrl-f12': 'elmjutsu:go-back'
  'f2': 'elmjutsu:rename-symbol'

'atom-workspace':
  'f1': 'elmjutsu:toggle-sidekick'
  'ctrl-shift-f12': 'elmjutsu:hide-usages-panel'
```

Add them to your `keymap.cson` or bind them from `Settings` > `Keybindings`.

## Notes

* Be sure to check out the [settings](http://flight-manual.atom.io/using-atom/sections/atom-packages/#package-settings) for this package to find out about the available options.
* It's highly recommended to read `CHANGELOG.md` before upgrading to a newer version to check for breaking changes.
* The commands only work for top-level values for now.
* You may encounter weird behaviors if multiple files are using the same module name in your project.

## Credits

* The initial code was based on the [source](https://github.com/elm-lang/elm-lang.org) of [Try Elm](http://elm-lang.org/try).
* The [code](https://github.com/edubkendo/atom-elm) for computing snippet tab stops was from [language-elm](https://atom.io/packages/language-elm).
