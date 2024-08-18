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
```
- `<C-i> (Ctrl + i)` Acts like the back button in the IDE, taking you to the previous location in the code.
- `<C-o> (Ctrl + o)` Acts like the forward button, taking you to the next location in the code after using the back action.

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

### IDE Interaction
```
nmap <C-m> <Action>(ShowPopupMenu)
nmap <C-S-m> <Action>(ToolWindowsGroup)
```
- `<C-m> (Ctrl + m)` Opens the popup menu in the IDE, allowing you to quickly access various actions.
- `<C-S-m> (Ctrl + Shift + m)` Opens the Tool Windows group, helping you manage and access different tool windows within the IDE.

### Clear Search Highlighting
```
nnoremap <C-[> :noh<return>
```
`<C-[> (Ctrl + [)` Clears any search highlighting in the current buffer, making the code easier to read after a search operation.


## Leader Commands

### EasyMotion
```
let g:WhichKeyDesc_easymotion = "<leader><leader> EasyMotion"
```
- `g:WhichKeyDesc_easymotion` This is a custom variable that defines the description for the EasyMotion leader command in the which-key plugin.
- `"<leader><leader> EasyMotion"` This indicates that pressing <Space><Space> will activate EasyMotion. This is a mnemonic mapping where double pressing the leader key triggers EasyMotion, making it easy to remember and access.

### Information Commands
This section provides a set of leader key mappings focused on retrieving various types of information in your JetBrains IDE. Each command is designed to quickly access important details related to your code.
```
nmap <leader>ie <Action>(ShowErrorDescription)
nmap <leader>it <Action>(ExpressionTypeInfo)
nmap <leader>ip <Action>(ParameterInfo)
nmap <leader>ij <Action>(QuickJavaDoc)
nmap <leader>if <Action>(FileStructurePopup)
nmap <leader>iU <Action>(ShowUmlDiagram)
nmap <leader>ih <Action>(CallHierarchy)
nmap <leader>iu <Action>(ShowUsages)
nmap <leader>im <Action>(MethodHierarchy)
let g:WhichKeyDesc_info = "<leader>i Information"
let g:WhichKeyDesc_info_error = "<leader>ie Error Description"
let g:WhichKeyDesc_info_type = "<leader>it Expression Type"
let g:WhichKeyDesc_info_parameter = "<leader>ip Parameter Info"
let g:WhichKeyDesc_info_javadoc = "<leader>ij Java Doc"
let g:WhichKeyDesc_info_file_structure = "<leader>if File Structure"
let g:WhichKeyDesc_info_uml_diagram = "<leader>iU UML Diagram"
let g:WhichKeyDesc_info_call_hierarchy = "<leader>ih Call Hierarchy"
let g:WhichKeyDesc_info_show_usages = "<leader>iu Usages"
let g:WhichKeyDesc_info_method_hierarchy = "<leader>im Method Hierarchy"
```
- `<leader>ie` Shows the error description of the current issue under the cursor. Useful for quickly identifying and understanding errors in your code.
- `<leader>it` Displays the type information of the expression under the cursor. This is particularly helpful when working with languages where type inference is common.
- `<leader>ip` Provides information about the parameters of a function or method, showing the expected arguments and their types.
- `<leader>ij` Opens the Quick JavaDoc window, which shows the documentation for the symbol under the cursor. This is useful for understanding the purpose and usage of methods, classes, and other elements in your code.
- `<leader>if` Displays the file structure popup, allowing you to quickly navigate through the structure of the current file, such as methods, variables, and classes.
- `<leader>iU` Opens the UML diagram for the current class or file. This is particularly helpful for visualizing class relationships and understanding the overall structure of the code.
- `<leader>ih` Displays the call hierarchy, showing how the current method is called and where it is used. This is useful for tracking dependencies and understanding the flow of the program.
- `<leader>iu` Lists all the usages of the current symbol, helping you find where a variable, method, or class is used across your project.
- `<leader>im` Displays the method hierarchy, showing how methods relate to each other, including overrides and implementations. This is useful for navigating complex inheritance structures.

### Window Split Commands
This section provides leader key mappings for managing and navigating window splits within your JetBrains IDE. These commands allow you to split the editor window vertically or horizontally, unsplit windows, and manage window groups.
```
nmap <leader>wv <Action>(SplitVertically)
nmap <leader>wh <Action>(SplitHorizontally)
nmap <leader>wu <Action>(Unsplit)
nmap <leader>wm <Action>(MoveEditorToOppositeTabGroup)
nmap <leader>wb <Action>(Back)
nmap <leader>wf <Action>(Forward)
let g:WhichKeyDesc_window = "<leader>w Window splits"
let g:WhichKeyDesc_window_split_vertically = "<leader>wv Split vertically"
let g:WhichKeyDesc_window_split_horizontally = "<leader>wh Split horizontally"
let g:WhichKeyDesc_window_split_unsplit = "<leader>wu Unsplit"
let g:WhichKeyDesc_window_split_move_editor = "<leader>wm Move editor to opposite tab group"
let g:WhichKeyDesc_window_split_back = "<leader>wb Back split"
let g:WhichKeyDesc_window_split_forward = "<leader>wf Forward split"
```
- `<leader>wv` Splits the current window vertically, creating a new editor pane to the right of the current one.
- `<leader>wh` Splits the current window horizontally, creating a new editor pane below the current one.
- `<leader>wu` Un-splits the current window, closing the split and returning to a single editor pane.
- `<leader>wm` Moves the current editor tab to the opposite tab group (i.e., from the left to the right group or vice versa). This is useful for organizing your workspace.
- `<leader>wb` Navigates back to the previous editor split or pane. Similar to the back button in a browser, it returns you to the last active split.
- `<leader>wf` Navigates forward to the next editor split or pane. This is the counterpart to the back action and moves you forward through your split history.

### Tab Management Commands
This section provides leader key mappings for managing editor tabs within your JetBrains IDE. These commands allow you to pin tabs, navigate between specific tabs, and close tabs in various ways.
```
nmap <leader>tp <Action>(PinActiveEditorTab)
nmap <leader>tg1 <Action>(GoToTab1)
nmap <leader>tg2 <Action>(GoToTab2)
nmap <leader>tg3 <Action>(GoToTab3)
nmap <leader>tg4 <Action>(GoToTab4)
nmap <leader>tg5 <Action>(GoToTab5)
nmap <leader>tg6 <Action>(GoToTab6)
nmap <leader>tg7 <Action>(GoToTab7)
nmap <leader>tg8 <Action>(GoToTab8)
nmap <leader>tg9 <Action>(GoToTab9)
nmap <leader>tx <Action>(CloseContent)
nmap <leader>tX <Action>(CloseAllEditors)
nmap <leader>tA <Action>(CloseAllEditorsButActive)
nmap <leader>tP <Action>(CloseAllUnpinnedEditors)
let g:WhichKeyDesc_tabs = "<leader>t Tabs"
let g:WhichKeyDesc_tabs_pin = "<leader>tp Pin Active Tab"
let g:WhichKeyDesc_tabs_go_to = "<leader>tg Go to Tab"
let g:WhichKeyDesc_tabs_go_to_1 = "<leader>tg1 Go to Tab 1"
let g:WhichKeyDesc_tabs_go_to_2 = "<leader>tg2 Go to Tab 2"
let g:WhichKeyDesc_tabs_go_to_3 = "<leader>tg3 Go to Tab 3"
let g:WhichKeyDesc_tabs_go_to_4 = "<leader>tg4 Go to Tab 4"
let g:WhichKeyDesc_tabs_go_to_5 = "<leader>tg5 Go to Tab 5"
let g:WhichKeyDesc_tabs_go_to_6 = "<leader>tg6 Go to Tab 6"
let g:WhichKeyDesc_tabs_go_to_7 = "<leader>tg7 Go to Tab 7"
let g:WhichKeyDesc_tabs_go_to_8 = "<leader>tg8 Go to Tab 8"
let g:WhichKeyDesc_tabs_go_to_9 = "<leader>tg9 Go to Tab 9"
let g:WhichKeyDesc_tabs_close = "<leader>tx Close Current Tab"
let g:WhichKeyDesc_tabs_close_all = "<leader>tX Close All Tabs"
let g:WhichKeyDesc_tabs_close_all_but_active = "<leader>tA Close All Tabs But Active"
let g:WhichKeyDesc_tabs_close_all_unpinned = "<leader>tP Close All Unpinned Tabs"
```
- `<leader>tp` Pins the currently active editor tab, ensuring that it stays open even when you close other tabs or open new ones.
- `<leader>tg<number>` Switches to the tab corresponding to `<number>`. For example, `<leader>tg1` switches to the first tab, `<leader>tg2` to the second tab, and so on, up to the ninth tab with `<leader>tg9`.
- `<leader>tx` Closes the current editor tab.
- `<leader>tX` Closes all open editor tabs.
- `<leader>tA` Closes all editor tabs except the one that is currently active, helping you focus on your current work.
- `<leader>tP` Closes all unpinned editor tabs, keeping only the pinned ones open. This is useful for cleaning up your workspace without losing important tabs.

### Display Mode Commands
This set of leader key mappings provides quick access to various display and distraction-free modes in your JetBrains IDE. These commands help you focus on your work by adjusting the IDE’s interface.
```
map <leader>Dd <Action>(ToggleDistractionFreeMode)
map <leader>Dz <Action>(ToggleZenMode)
map <leader>Df <Action>(ToggleFullScreen)
let g:WhichKeyDesc_display = "<leader>D Display options"
let g:WhichKeyDesc_zen_mode = "<leader>Dz Toggle Zen mode"
let g:WhichKeyDesc_df_mode = "<leader>Dd Toggle Distraction-Free mode"
let g:WhichKeyDesc_fullscreen = "<leader>Df Toggle full screen"
```
- `<leader>Dd` Toggles Distraction-Free Mode, which hides all tool windows, menus, and other interface elements to give you a clean, uninterrupted workspace.
- `<leader>Dz` Toggles Zen Mode, which typically includes a more focused view with minimal distractions, combining full-screen and distraction-free features.
- `<leader>Df` Toggles Full-Screen Mode, which maximizes the editor window to cover the entire screen, hiding other applications or windows for a focused work environment.

### File Management and Navigation Commands
These leader key mappings help you efficiently manage files, access recent items, and perform various file-related actions within your JetBrains IDE.
```
nmap <leader>fg <Action>(GotoFile)
nmap <leader>fr <Action>(RecentFiles)
nmap <leader>fc <Action>(FindInPath)
nmap <leader>fl <Action>(RecentLocations)
nmap <leader>fs <Action>(NewScratchFile)
nmap <leader>fe :NERDTreeToggle<CR>
nmap <leader>fo <Action>(OpenFile)
nmap <leader>fy <Action>(CopyAbsolutePath)
nmap <leader>fp <Action>(ManageRecentProjects)
nmap <leader>fh <Action>(LocalHistory.ShowHistory)
nmap <leader>ff <Action>(ShowFilePath)
nmap <leader>fi <Action>(SelectIn)
nmap <leader>fp <Action>(ReplaceInPath)
let g:WhichKeyDesc_file_opt = "<leader>f File navigation"
let g:WhichKeyDesc_file_opt_goto_file = "<leader>fg Go To File"
let g:WhichKeyDesc_file_opt_goto_content = "<leader>fc Find In Files"
let g:WhichKeyDesc_file_opt_show_recent_files = "<leader>fr Recent Files"
let g:WhichKeyDesc_file_opt_show_recent_locations = "<leader>fl Recent Locations"
let g:WhichKeyDesc_file_opt_new_scratch_file = "<leader>fs New Scratch File"
let g:WhichKeyDesc_file_opt_toggle_nerdtree = "<leader>fe Toggle NERDTree"
let g:WhichKeyDesc_file_opt_open_file = "<leader>fo Open File"
let g:WhichKeyDesc_file_opt_copy_path = "<leader>fy Copy Absolute Path"
let g:WhichKeyDesc_file_opt_recent_projects = "<leader>fp Manage Recent Projects"
let g:WhichKeyDesc_file_opt_history = "<leader>fh Show Local History"
let g:WhichKeyDesc_file_opt_show_path = "<leader>ff Show File Path"
let g:WhichKeyDesc_file_opt_select_in = "<leader>fi Select In"
let g:WhichKeyDesc_file_opt_replace_in_path = "<leader>fp Replace In Path"
```
- `<leader>fg` Opens the "Goto File" dialog, allowing you to quickly navigate to any file within your project by typing part of its name.
- `<leader>fr` Opens a list of recent files, making it easy to reopen files you’ve worked on recently.
- `<leader>fc` Opens the "Find in Path" dialog, enabling you to search for text or code within a specific directory or across your entire project.
- `<leader>fl` Opens a list of recent locations in the code, allowing you to quickly jump back to recent positions within files.
- `<leader>fs` Creates a new scratch file, which is a temporary file you can use for quick notes or testing code snippets.
- `<leader>fe` Toggles the NERDTree file explorer panel, which provides a tree view of your project's directory structure.
- `<leader>fo` Opens the file selection dialog, allowing you to open files from your file system directly.
- `<leader>fy` Copies the absolute path of the currently focused file to the clipboard.
- `<leader>fp` Opens a list of recent projects, letting you quickly switch between projects you’ve worked on recently.
- `<leader>fh` Displays the local history for the currently open file, showing previous versions and changes made over time.
- `<leader>ff` Shows the file path of the currently open file, often used to quickly view the file's location within the project or filesystem.
- `<leader>fi` Opens the "Select In" dialog, allowing you to view and select the current file in various views or tools, such as the project view.
- `<leader>fp` Opens the "Replace in Path" dialog, enabling you to search and replace text across multiple files within a specified path.

# Run and Test Management Commands
These leader key mappings provide quick access to various run and test-related actions in your JetBrains IDE. They help streamline the process of running, rerunning, and managing configurations for your code.
```
nmap <leader>rm <Action>(RunMenu)
nmap <leader>rn <Action>(RunClass)
nmap <leader>rc <Action>(ContextRun)
nmap <leader>rr <Action>(Rerun)
nmap <leader>rt <Action>(RunTests)
nmap <leader>rf <Action>(RerunFailedTests)
nmap <leader>rs <Action>(Stop)
nmap <leader>rC <Action>(ChooseRunConfiguration)
let g:WhichKeyDesc_run = "<leader>r Run"
let g:WhichKeyDesc_run_menu = "<leader>rm Run Menu"
let g:WhichKeyDesc_run_class = "<leader>rn Run Class"
let g:WhichKeyDesc_run_context = "<leader>rc Context Run"
let g:WhichKeyDesc_run_rerun = "<leader>rr Rerun"
let g:WhichKeyDesc_run_tests = "<leader>rt Run Tests"
let g:WhichKeyDesc_run_failed = "<leader>rf Rerun Failed Tests"
let g:WhichKeyDesc_run_stop = "<leader>rs Stop"
let g:WhichKeyDesc_run_choose_configuration = "<leader>rC Choose Run Configuration"
```
- `<leader>rm` Opens the "Run Menu," allowing you to select and execute various run configurations or commands related to running your code.
- `<leader>rn` Executes the currently selected class, typically used for running the main class in a Java project or similar environments.
- `<leader>rc` Runs the code or tests in the context of the currently selected file or editor. Useful for quickly executing code without needing to configure run settings.
- `<leader>rr` Reruns the last executed run configuration or command, useful for quickly testing changes without manually initiating the run process again.
- `<leader>rt` Runs all tests in the project or selected scope, allowing you to execute and verify the correctness of your code.
- `<leader>rf` Reruns only the tests that failed during the previous test run, helping you focus on fixing issues without running all tests again.
- `<leader>rs` Stops the currently running process or test, allowing you to halt execution if needed.
- `<leader>rC` Opens the "Choose Run Configuration" dialog, letting you select or switch between different run configurations for your project.

### Debugging Commands
These leader key mappings streamline various debugging tasks in your JetBrains IDE. They provide quick access to debugging features such as running, stepping through code, and managing breakpoints.
```
nmap <leader>dx <Action>(Debug)
nmap <leader>dc <Action>(ContextDebug)
nmap <leader>dv <Action>(ViewBreakpoints)
nmap <leader>de <Action>(EditBreakpoint)
nmap <leader>dm <Action>(XDebugger.MuteBreakpoints)
nmap <leader>dt <Action>(ToggleLineBreakpoint)
nmap <leader>dC <Action>(RunToCursor)
nmap <leader>di <Action>(StepInto)
nmap <leader>do <Action>(StepOver)
nmap <leader>dr <Action>(Resume)
nmap <leader>dR <Action>(EvaluateExpression)
nmap <leader>dt <Action>(ActivateDebugToolWindow)
let g:WhichKeyDesc_debugging = "<leader>d Debugging"
let g:WhichKeyDesc_debug_execute = "<leader>dx Execute Debug"
let g:WhichKeyDesc_debug_context = "<leader>dc Context Debug"
let g:WhichKeyDesc_debug_view_breakpoints = "<leader>dv View Breakpoints"
let g:WhichKeyDesc_debug_edit_breakpoints = "<leader>de Edit Breakpoints"
let g:WhichKeyDesc_debug_mute_breakpoints = "<leader>dm Mute Breakpoints"
let g:WhichKeyDesc_debug_toggle_line_breakpoint = "<leader>dt Toggle Line Breakpoint"
let g:WhichKeyDesc_debug_run_to_cursor = "<leader>dC Run to Cursor"
let g:WhichKeyDesc_debug_step_into = "<leader>di Step Into"
let g:WhichKeyDesc_debug_step_over = "<leader>do Step Over"
let g:WhichKeyDesc_debug_resume = "<leader>dr Resume Debugging"
let g:WhichKeyDesc_debug_evaluate_expression = "<leader>dR Evaluate Expression"
let g:WhichKeyDesc_debug_activate_tool_window = "<leader>dt Activate Debug Tool Window"
```
- `<leader>dx` Starts debugging the currently selected file or run configuration, launching the debugger with the specified settings.
- `<leader>dc` Starts debugging in the context of the currently selected file or editor, allowing you to debug specific sections of code without reconfiguring the debugger.
- `<leader>dv` Opens the "View Breakpoints" dialog, showing a list of all breakpoints set in your code, making it easy to manage and review them.
- `<leader>de` Allows you to edit the properties of a selected breakpoint, such as conditions or actions to be performed when the breakpoint is hit.
- `<leader>dm` Mutes all breakpoints, temporarily disabling them without removing them, useful for focusing on specific parts of your code without being interrupted by breakpoints.
- `<leader>dt` Toggles a breakpoint at the current line in the editor, allowing you to quickly set or remove breakpoints while debugging.
- `<leader>dC` Runs the debugger up to the cursor's current position, allowing you to skip over code and focus on specific parts of your program.
- `<leader>di` Steps into the next function or method call in the debugger, allowing you to dive deeper into the execution flow of your code.
- `<leader>do` Steps over the current line of code, executing it without entering any function calls, useful for moving through your code line by line.
- `<leader>dr` Resumes normal execution of the program, continuing from the current breakpoint or pause point until the next breakpoint or program end.
- `<leader>dR` Opens the "Evaluate Expression" dialog, allowing you to inspect or evaluate expressions while debugging to understand the state of your program.
- `<leader>dt` Activates the Debug Tool Window, bringing up the debugging interface where you can view variables, stack traces, and other debugging information.

### Refactoring and Code Impromenet Commands
These leader key mappings provide quick access to various refactoring and code improvement features in your JetBrains IDE. They help you streamline code changes, improve code quality, and perform common refactoring tasks efficiently.
```
nmap <leader>ll <Action>(Refactorings.QuickListPopupAction)
nmap <leader>lr <Action>(RenameElement)
nmap <leader>lc <Action>(ChangeSignature)
nmap <leader>lv <Action>(IntroduceVariable)
nmap <leader>li <Action>(Inline)
nmap <leader>lf <Action>(IntroduceField)
nmap <leader>lm <Action>(ExtractMethod)
nmap <leader>lC <Action>(IntroduceConstant)
nmap <leader>lp <Action>(IntroduceParameter)
nmap <leader>lo <Action>(IntroduceParameterObject)
nmap <leader>le <Action>(EncapsulateFields)
nmap <leader>la <Action>(ShowIntentionActions)
nmap <leader>lR <Action>(ReformatCode)
nmap <leader>lI <Action>(InspectCode)
nmap <leader>lG <Action>(Generate)
let g:WhichKeyDesc_language = "<leader>l Language"
let g:WhichKeyDesc_language_menu = "<leader>ll Quick List"
let g:WhichKeyDesc_language_rename = "<leader>lr Rename"
let g:WhichKeyDesc_language_change_signature = "<leader>lc Change Signature"
let g:WhichKeyDesc_language_inline_variable = "<leader>li Inline"
let g:WhichKeyDesc_language_introduce_field = "<leader>lf Introduce Field"
let g:WhichKeyDesc_language_extract_method = "<leader>lm Extract Method"
let g:WhichKeyDesc_language_introduce_constant = "<leader>lC Introduce Constant"
let g:WhichKeyDesc_language_introduce_parameter = "<leader>lp Introduce Parameter"
let g:WhichKeyDesc_language_introduce_param_object = "<leader>lo Introduce Parameter Object"
let g:WhichKeyDesc_language_encapsulate = "<leader>le Encapsulate Fields"
let g:WhichKeyDesc_language_show_intention_actions = "<leader>la Show Intention Actions"
let g:WhichKeyDesc_language_reformat_code = "<leader>lR Reformat Code"
let g:WhichKeyDesc_language_inspect_code = "<leader>lI Inspect Code"
let g:WhichKeyDesc_language_generate = "<leader>lG Generate"
```
- `<leader>ll` Opens the Quick Refactorings List, providing a menu of available refactoring actions you can apply to the current code element.
- `<leader>lr` Renames the selected code element (e.g., variable, method, class), updating all occurrences of the element throughout your codebase.
- `<leader>lc` Changes the signature of a method or function, allowing you to modify its parameters or return type and automatically update all references.
- `<leader>lv` Introduces a new variable for the selected expression or value, simplifying complex expressions and improving code readability.
- `<leader>li` Inlines the selected code element (e.g., variable or method), replacing its occurrences with its value or implementation directly in the code.
- `<leader>lf` Introduces a new field in the current class or object, helping to manage and organize data within your classes.
- `<leader>lm` Extracts a selected block of code into a new method, improving code modularity and reusability.
- `<leader>lC` Introduces a new constant for a selected value or expression, making it easier to manage and update constant values in your code.
- `<leader>lp` Introduces a new parameter to a method or function, allowing you to modify its signature and update all references accordingly.
- `<leader>lo` Introduces a parameter object for a method with multiple parameters, grouping them into a single object to simplify method signatures.
- `<leader>le` Encapsulates fields by creating getter and setter methods, improving data encapsulation and access control.
- `<leader>la` Displays a list of intention actions available for the current code element, offering quick fixes and code improvements.
- `<leader>lR` Reformats the selected code or entire file according to the code style settings, improving readability and consistency.
- `<leader>lI` Inspects the selected code or file for potential issues, offering suggestions for code improvements and optimizations.
- `<leader>lG` Opens the "Generate" menu, providing options to automatically generate code such as getters, setters, constructors, or other boilerplate code.

### Bookmark Management Commands
These leader key mappings help you manage and navigate bookmarks within your JetBrains IDE. Bookmarks are useful for marking important sections of code, making it easier to return to them later.
```
nmap <leader>bm <Action>(Bookmarks)
nmap <leader>bs <Action>(ShowBookmarks)
nmap <leader>bt <Action>(ActivateBookmarksToolWindow)
nmap <leader>bb <Action>(ToggleBookmark)
nmap <leader>be <Action>(EditBookmark)
nmap <leader>bp <Action>(GotoPreviousBookmark)
nmap <leader>bn <Action>(GotoNextBookmark)
let g:WhichKeyDesc_bookmarks = "<leader>b Bookmarks"
let g:WhichKeyDesc_bookmarks_menu = "<leader>bm Bookmark Menu"
let g:WhichKeyDesc_bookmarks_show = "<leader>bs Show Bookmarks"
let g:WhichKeyDesc_bookmarks_tool = "<leader>bt Bookmark Tool"
let g:WhichKeyDesc_bookmarks_toggle_bookmark = "<leader>bb Toggle Bookmark"
let g:WhichKeyDesc_bookmarks_edit = "<leader>be Edit Bookmark"
let g:WhichKeyDesc_bookmarks_prev = "<leader>bp Previous Bookmark"
let g:WhichKeyDesc_bookmarks_next = "<leader>bn Next Bookmark"
```
- `<leader>bm` Opens the "Bookmarks" menu or dialog, allowing you to view and manage all bookmarks set in your project.
- `<leader>bs` Displays a list of all bookmarks within the current file or project, making it easy to review and navigate through them.
- `<leader>bt` Activates the Bookmarks Tool Window, providing a dedicated interface to manage and navigate your bookmarks.
- `<leader>bb` Toggles a bookmark at the current line in the editor, allowing you to quickly mark or unmark important sections of code.
- `<leader>be` Opens the "Edit Bookmark" dialog, letting you modify the details or description of a selected bookmark.
- `<leader>bp` Jumps to the previous bookmark in the current file or project, helping you navigate to earlier marked locations.
- `<leader>bn` Jumps to the next bookmark in the current file or project, allowing you to quickly move to subsequent marked locations.
