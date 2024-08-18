# IdeaVim Configuration
## Base Settings
This section of the configuration covers the fundamental settings that establish the basic behavior and appearance of IdeaVim in your JetBrains IDE. Below is a description of each setting included in this part of the configuration.

```
set scrolloff=10
set history=1000
set number relativenumber
set showmode
set showcmd
set smartcase
set incsearch
set hlsearch
set visualbell
```
- `set scrolloff=10` Keeps 10 lines visible above and below the cursor when scrolling, making it easier to maintain context while editing.
- `set history=1000` Increases the number of command-line history entries to 1000, allowing you to recall more previous commands.
- `set number relativenumber` Displays line numbers alongside relative line numbers, aiding in navigation and editing.
- `set showmode` Displays the current mode (e.g., insert, normal) in the command line, helping you keep track of your mode.
- `set showcmd` Shows partial commands in the command line as you type, providing visual feedback on your input.
- `set smartcase` Makes search case-insensitive unless an uppercase letter is used, balancing case sensitivity in searches.
- `set incsearch` Enables incremental search, highlighting matches as you type, which improves search efficiency.
- `set hlsearch` Highlights all matches of the search pattern, making it easier to locate search results in the text.
- `set visualbell` Uses a visual flash instead of an audible bell to indicate errors or alerts, reducing distraction.


### Clipboard Integration
```
set clipboard+=unnamed
```
`set clipboard+=unnamed` Allows Vim to use the system clipboard for copy and paste operations, facilitating seamless interaction with other applications.


### Leader Key
```
let mapleader="\<space>"
```
`let mapleader="\<space>"` Sets the space key as the leader key, which is used as a prefix for custom key mappings, making them more accessible.


### Default Behavior
```
set gdefault
```
`set gdefault` Automatically applies the global default flag to substitution commands, simplifying text replacement tasks.


### IdeaVim Specific Settings
```
set ideajoin
set ideamarks
set idearefactormode=normal
set ideastatusicon=gray
```
- `set ideajoin` Enables the join command specific to IdeaVim, which helps in joining lines in the editor.
- `set ideamarks` Activates IdeaVim-specific mark features, integrating Vim marks with the IDE’s navigation tools.
- `set idearefactormode=normal` Sets the default refactor mode to normal, controlling how refactor operations behave.
- `set ideastatusicon=gray` Configures the status icon color for IdeaVim, providing a visual indicator in the IDE.

