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


## Plugin Settings
This section focuses on the plugins I’ve integrated with IdeaVim and how their settings are configured to enhance my coding workflow.

### General Plugins
```
set exchange
set commentary
set ReplaceWithRegister
set surround
set nerdtree
```
- `set exchange` Enables the vim-exchange plugin, which allows you to easily swap or exchange two pieces of text within your code.
- `set commentary` Activates the vim-commentary plugin, simplifying the process of commenting and uncommenting lines of code.
- `set ReplaceWithRegister` Enables the vim-replace-with-register plugin, allowing you to replace text using the contents of a register.
- `set surround` Activates the vim-surround plugin, which simplifies operations involving surrounding text with quotes, parentheses, brackets, etc.
- `set nerdtre` Activates the NERDTree plugin, which provides a file explorer tree for navigating your project structure within the editor.

### Searching Plugins
```
set sneak
set easymotion
```
- `set sneak` Enables the vim-sneak plugin, which provides quick two-character search functionality, allowing you to jump to locations in your code with minimal keystrokes.
- `set easymotion` Activates the vim-easymotion plugin, which provides a quick way to move around within your code by typing only a few characters. The additional setting:
  - `let g:EasyMotion_override_acejump = 0` disables the override of the AceJump functionality, allowing both easymotion and acejump to coexist without conflict.

### Highlighting Plugins
```
set highlightedyank
set quickscope
let g:qs_highlight_on_keys = ['f', 'F', 't', 'T']
```
- `set highlightedyank` Enables the vim-highlightedyank plugin, which visually highlights the text that has been yanked (copied), providing instant feedback.
- `set quickscope` Activates the vim-quickscope plugin, which highlights targets for quick jumps based on specific characters. The additional setting:
  - `let g:qs_highlight_on_keys = ['f', 'F', 't', 'T']` configures quickscope to highlight only when using the f, F, t, or T keys for character-based navigation.

### Object Plugins
```
set textobj-entire
set indent-object
set argtextobj
```
- `set textobj-entire` Activates the vim-textobj-entire plugin, which provides text objects that select the entire buffer, making it easy to manipulate the whole file.
- `set indent-object` Enables the vim-indent-object plugin, allowing you to select text based on indentation levels, which is particularly useful in Python or other indentation-sensitive languages.
- `set argtextobj` Enables the vim-argument-object plugin, which allows you to select and manipulate arguments within functions easily. The setting:
  - `let g:argtextobj_pairs="[:],(:),<:>"` defines the pairs of delimiters (e.g., parentheses, brackets) that the plugin recognizes as argument boundaries.

### Which-key Plugin
```
set which-key
set notimeout
let g:WhichKey_FontSize = 20
let g:WhichKey_PrefixColor = "#a403fe"
let g:WhichKey_CommandColor = "#01ffff"
let g:WhichKey_PrefixStyle = "bold"
let g:WhichKey_KeyStyle = "italic"
let g:WhichKey_SortOrder = "by_key_prefix_first"
let g:WhichKey_ShowTypedSequence = "false"
```
- `set which-key` Enables the which-key plugin, which displays a popup showing possible key bindings after you start a key sequence. This is particularly useful for discovering and remembering custom key mappings.
- `set notimeout` Disables the timeout for key sequences, ensuring that you have enough time to view and select the desired key binding.
  - `let g:WhichKey_FontSize = 20` Sets the font size of the which-key popup to 20 for better visibility.
  - `let g:WhichKey_PrefixColor = "#a403fe"` Changes the color of the prefix keys (the keys that trigger a sequence) to a purple hue.
  - `let g:WhichKey_CommandColor = "#01ffff"` Sets the color of the commands (the resulting actions) to cyan.
  - `let g:WhichKey_PrefixStyle = "bold"` Makes the prefix keys appear bold in the popup.
  - `let g:WhichKey_KeyStyle = "italic"` Styles the key bindings in italics, distinguishing them visually from other elements.
  - `let g:WhichKey_SortOrder = "by_key_prefix_first"` Organizes the popup items by key prefix first, making it easier to follow a logical sequence.
  - `let g:WhichKey_ShowTypedSequence = "false"` Disables the display of the typed key sequence in the popup, focusing on the available options instead.


## Key Mappings

### Tab Navigation
```
nmap <C-p> <Action>(PreviousTab)
nmap <C-n> <Action>(NextTab)
```
- `<C-p> (Ctrl + p)` This mapping switches to the previous tab in your JetBrains IDE. It's a quick way to navigate back through your open tabs.
- `<C-n> (Ctrl + n)` This mapping switches to the next tab in your JetBrains IDE. It allows you to move forward through your open tabs.

### Pane Navigation
```
nnoremap <C-h> <C-w>h
nnoremap <C-l> <C-w>l
nnoremap <C-k> <C-w>k
nnoremap <C-j> <C-w>j
```
- `<C-h> (Ctrl + h)` Move to the pane to the left.
- `<C-l> (Ctrl + l)` Move to the pane to the right.
- `<C-k> (Ctrl + k)` Move to the pane above.
- `<C-j> (Ctrl + j)` Move to the pane below.

### Navigation Actions
```
nmap <C-i> <Action>(Back)
nmap <C-o> <Action>(Forward)
nmap <C-m> <Action>(ShowPopupMenu)
nmap <C-S-m> <Action>(ToolWindowsGroup)
```
- `<C-i> (Ctrl + i)` Acts like the back button in the IDE, taking you to the previous location in the code.
- `<C-o> (Ctrl + o)` Acts like the forward button, taking you to the next location in the code after using the back action.
- `<C-m> (Ctrl + m)` Opens the popup menu in the IDE, allowing you to quickly access various actions.
- `<C-S-m> (Ctrl + Shift + m)` Opens the Tool Windows group, helping you manage and access different tool windows within the IDE.

### Jump Between Methods
```
nmap [[ <Action>(MethodUp)
nmap ]] <Action>(MethodDown)
```
- `[[` Moves the cursor to the previous method in the code.
- `]]` Moves the cursor to the next method in the code.

### Visual Indentation
```
vnoremap < <gv
vnoremap > >gv
```
- `<` Decreases the indentation of the selected block of code and keeps the selection active for further adjustments.
- `>` Increases the indentation of the selected block of code and keeps the selection active for further adjustments.

### Clear Search Highlighting
```
nnoremap <C-[> :noh<return>
```
`<C-[> (Ctrl + [)` Clears any search highlighting in the current buffer, making the code easier to read after a search operation.
