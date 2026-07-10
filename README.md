# IdeaVim Configuration

A single-file, which-key-driven IdeaVim setup for JetBrains IDEs. For background and rationale, see my [Medium article](https://medium.com/@dbilici/a-practical-ideavim-setup-for-intellij-idea-cf74222e7b45).

> **Compatibility:** Tested with IdeaVim 2.x on recent JetBrains IDEs (2025.x). Some options here (`functextobj`, `ideaput`, `sethandler`) require a reasonably up-to-date IdeaVim.

## Installation

Everything lives in one file: `.ideavimrc`. Put it in your home directory.

```sh
# Back up any existing config first
cp ~/.ideavimrc ~/.ideavimrc.bak 2>/dev/null || true

# Copy this repo's file to your home directory…
cp .ideavimrc ~/.ideavimrc

# …or symlink it so the repo stays your live config:
ln -s "$(pwd)/.ideavimrc" ~/.ideavimrc
```

Reload without restarting via `<leader>vr`, the IdeaVim status-bar widget → **Reload**, or just restart the IDE.

The same `~/.ideavimrc` is loaded by every JetBrains IDE (IntelliJ, PyCharm, WebStorm, Rider…). A few Java-specific actions (e.g. `EncapsulateFields`, `ShowUmlDiagram`) simply do nothing in IDEs that lack them — no errors. Two features need extra IDE plugins: **AceJump** (for EasyMotion) and **CaseConv** (for the `<leader>c` case conversions).

## Options

```vim
set scrolloff=10
set history=1000
set number relativenumber
set showmode
set showcmd
set ignorecase
set smartcase
set incsearch
set hlsearch
set visualbell
set gdefault

set clipboard+=unnamed,ideaput
set ideajoin
set ideamarks
set idearefactormode=keep
set ideastatusicon=gray
```

- `scrolloff=10` Keeps 10 lines of context above/below the cursor.
- `history=1000` Remembers more command-line entries.
- `number relativenumber` Absolute number on the current line, relative elsewhere.
- `showmode` / `showcmd` Show the current mode and partial commands. *(On by default in current IdeaVim; kept for clarity.)*
- `ignorecase` + `smartcase` Search is case-insensitive **until** you type an uppercase letter. `smartcase` does nothing without `ignorecase` — both are required.
- `incsearch` / `hlsearch` Incremental search and match highlighting.
- `visualbell` Flash instead of beep.
- `gdefault` Substitutions are global by default.
- `clipboard+=unnamed,ideaput` Use the system clipboard, and paste via native IntelliJ insertion (multi-caret / template aware).
- `ideajoin` `J` uses the IDE's language-aware smart join.
- `ideamarks` Syncs Vim's uppercase marks with IDE bookmarks. *(On by default; kept for clarity.)*
- `idearefactormode=keep` Stay in **normal mode** during refactors (e.g. rename) instead of dropping into select mode. Valid values: `keep`, `select`, `visual`.
- `ideastatusicon=gray` Subtle status-bar icon.

## Plugins

```vim
set exchange
set commentary
set ReplaceWithRegister
set surround
set nerdtree

set easymotion
let g:EasyMotion_override_acejump = 0
set quickscope
let g:qs_highlight_on_keys = ['f', 'F', 't', 'T']

set highlightedyank

set textobj-entire
set indent-object
set argtextobj
let g:argtextobj_pairs="[:],(:),<:>"
set functextobj

set which-key
set notimeout
let g:WhichKey_FontFamily = "JetBrains Mono"
let g:WhichKey_FontSize = 20
let g:WhichKey_PrefixColor = "#a403fe"
let g:WhichKey_CommandColor = "#01ffff"
let g:WhichKey_PrefixStyle = "bold"
let g:WhichKey_KeyStyle = "italic"
let g:WhichKey_SortOrder = "by_key_prefix_first"
let g:WhichKey_SortCaseSensitive = "false"
let g:WhichKey_ShowTypedSequence = "false"
```

- `exchange` Swap two pieces of text (`cx` + motion).
- `commentary` Comment/uncomment (`gcc`, `gc` + motion).
- `ReplaceWithRegister` Replace text with a register's contents. Note: normal-mode `gr` is remapped to *Find Usages* in this config (see [LSP-style Bare Keys](#lsp-style-bare-keys)), so use visual-mode `gr` on a selection or `grr` for a whole line instead.
- `surround` Add/change/delete surroundings (`ys`, `cs`, `ds`).
- `nerdtree` File-explorer tree.
- `easymotion` Fast on-screen jumps. **Its default prefix is `<leader><leader>` (space space)** — so a single space opens your which-key menu, and a double space starts an EasyMotion jump. Relies on the **AceJump** IDE plugin. `g:EasyMotion_override_acejump = 0` lets EasyMotion and AceJump coexist.
- `quickscope` Passively highlights jump targets, limited to `f`/`F`/`t`/`T`. No keymaps — pure enhancement.
- `highlightedyank` Briefly highlights yanked text.
- `textobj-entire` / `indent-object` / `argtextobj` Text objects for the whole buffer (`ie`/`ae`), indentation (`ii`/`ai`), and function arguments (`ia`/`aa`).
- `functextobj` Method/function text objects: `am` (a method), `aM` (incl. comments/annotations), `im` (inner body).
- `which-key` + `notimeout` Popup that shows possible bindings after a prefix, with no timeout so it stays up. The `g:WhichKey_*` variables control the popup's font, colors, and sorting — `FontFamily` must name an installed font, and since the popup is rendered via Swing's HTML support, font ligatures won't display. The readable labels in the popup (e.g. "Debugging" instead of a raw action ID) come from the `g:WhichKeyDesc_*` variables that accompany every mapping group in the config.

> `vim-sneak` was removed — it overlapped EasyMotion and took over `s`/`S` (substitute). EasyMotion + QuickScope now cover jumping. To get sneak-style `s{char}{char}` back on a single engine, add `map s <Plug>(easymotion-s2)` (you lose `s`=substitute; use `cl` instead).

## Key Mappings

### Navigation

```vim
sethandler <C-h> n:vim
sethandler <C-j> n:vim
sethandler <C-k> n:vim
sethandler <C-l> n:vim

nmap <C-p> <Action>(PreviousTab)
nmap <C-n> <Action>(NextTab)

nnoremap <C-h> <C-w>h
nnoremap <C-l> <C-w>l
nnoremap <C-k> <C-w>k
nnoremap <C-j> <C-w>j

nmap <C-o> <Action>(Back)
nmap <C-i> <Action>(Forward)

nmap [[ <Action>(MethodUp)
nmap ]] <Action>(MethodDown)
```

- `sethandler <C-h/j/k/l> n:vim` Hands these keys to IdeaVim in normal mode so pane navigation is never swallowed by an IDE action.
- `<C-p>` / `<C-n>` Previous / next tab.
- `<C-h/l/k/j>` Move to the pane left / right / up / down.
- `<C-o>` / `<C-i>` Back / forward in the navigation history. In Vim `<C-o>` goes *back* and `<C-i>` *forward*; also `<C-i>` is the **same keycode as `<Tab>`**, so `<Tab>` triggers Forward too — exactly the Vim-native behavior.
- `[[` / `]]` Jump to the previous / next method.

### Editing & Selection

```vim
vnoremap < <gv
vnoremap > >gv

map <A-n> <Action>(SelectNextOccurrence)
map <A-p> <Action>(UnselectPreviousOccurrence)
map <A-a> <Action>(SelectAllOccurrences)

map <A-Up>   <Action>(EditorSelectWord)
map <A-Down> <Action>(EditorUnSelectWord)

nnoremap <A-j> <Action>(MoveLineDown)
nnoremap <A-k> <Action>(MoveLineUp)
```

- `<` / `>` Indent left / right and keep the selection active.
- `<A-n>` / `<A-p>` Add / remove a cursor at the next / previous occurrence (multi-caret).
- `<A-a>` Select all occurrences at once.
- `<A-Up>` / `<A-Down>` Expand / shrink the selection semantically (word → expression → statement → block).
- `<A-j>` / `<A-k>` Move the current line down / up.

> `Alt` mappings can be intercepted by the OS/keymap on some systems (menu mnemonics on Windows/Linux, special characters on macOS). Remap these if they don't fire.

### LSP-style Bare Keys

```vim
nmap K  <Action>(QuickJavaDoc)
nmap gd <Action>(GotoDeclaration)
nmap gi <Action>(GotoImplementation)
nmap gr <Action>(FindUsages)
nmap gy <Action>(GotoTypeDeclaration)
```

- `K` Quick documentation (hover) for the symbol under the cursor.
- `gd` Go to declaration. *(Overrides native go-to-local-declaration.)*
- `gi` Go to implementation. *(Overrides native insert-at-last-position; use `` `^ `` for that.)*
- `gr` Find usages (references). *(Shadows ReplaceWithRegister's normal-mode `gr`; visual `gr` and `grr` still work.)*
- `gy` Go to type declaration.

These complement the discoverable `<leader>g` / `<leader>i` groups below — bare keys for speed, leader groups for discovery.

### Quality-of-Life Motions

```vim
nnoremap n nzz
nnoremap N Nzz
nnoremap <C-d> <C-d>zz
nnoremap <C-u> <C-u>zz
nnoremap Y y$
xnoremap p P
```

- `n` / `N` and `<C-d>` / `<C-u>` Keep the cursor line centered (`zz`) after search jumps and half-page scrolls.
- `Y` Yank to the end of the line, consistent with `C` and `D`. (Native `Y` is a historical alias for `yy`.)
- `p` (visual mode) Paste over a selection **without clobbering the unnamed register**, so the same text can be pasted repeatedly. If your IdeaVim build still overwrites the register, use `xnoremap <leader>p "_dP` as a fallback.

### IDE Interaction

```vim
nmap <C-S-m> <Action>(ToolWindowsGroup)
nnoremap <silent> <Esc> :nohlsearch<CR>
```

- `<C-S-m>` Open the Tool Windows group.
- `<Esc>` Clear search highlighting. Written as `<Esc>` because `<C-[>` is byte-identical to it; if it ever clashes with dismissing the which-key popup, move it to `<leader>h`.

## Leader Commands

Space is the leader. Press it and pause to see the which-key popup. **Double space (`<leader><leader>`) starts EasyMotion.**

### IdeaVim · `<leader>v`

| Key | Action |
| --- | --- |
| `<leader>ve` | Edit `~/.ideavimrc` |
| `<leader>vr` | Reload `~/.ideavimrc` |

### Misc

| Key | Action |
| --- | --- |
| `<leader>m` | Show editor popup (context) menu |
| `<leader>T` | Toggle the terminal tool window |

> `ShowPopupMenu` is on `<leader>m` (not `<C-m>`) because `<C-m>` is the **same keycode as `<CR>`/Enter**.

### Information · `<leader>i`

| Key | Action |
| --- | --- |
| `<leader>ie` | Error description |
| `<leader>it` | Expression type |
| `<leader>ip` | Parameter info |
| `<leader>ij` | Quick JavaDoc |
| `<leader>if` | File structure popup |
| `<leader>iU` | UML diagram |
| `<leader>ih` | Call hierarchy |
| `<leader>iu` | Show usages |
| `<leader>im` | Method hierarchy |

### Window Splits · `<leader>w`

| Key | Action |
| --- | --- |
| `<leader>wv` | Split vertically |
| `<leader>wh` | Split horizontally |
| `<leader>wu` | Unsplit |
| `<leader>wm` | Move editor to opposite tab group |
| `<leader>wb` | Back split |
| `<leader>wf` | Forward split |

### Tabs · `<leader>t`

| Key | Action |
| --- | --- |
| `<leader>tP` | Pin active tab |
| `<leader>tg1`–`tg9` | Go to tab 1–9 |
| `<leader>tx` | Close current tab |
| `<leader>tX` | Close all tabs |
| `<leader>to` | Close all but active |
| `<leader>ta` | Close all unpinned |

### Display · `<leader>D`

| Key | Action |
| --- | --- |
| `<leader>Dd` | Toggle Distraction-Free mode |
| `<leader>Dz` | Toggle Zen mode |
| `<leader>Df` | Toggle full screen |

### File Navigation · `<leader>f`

| Key | Action |
| --- | --- |
| `<leader>fg` | Go to file |
| `<leader>fr` | Recent files |
| `<leader>fc` | Find in path |
| `<leader>fl` | Recent locations |
| `<leader>fs` | New scratch file |
| `<leader>fe` | Toggle NERDTree |
| `<leader>fo` | Open file |
| `<leader>fy` | Copy absolute path |
| `<leader>fp` | Manage recent projects |
| `<leader>fh` | Local history |
| `<leader>ff` | Show file path |
| `<leader>fi` | Select in |
| `<leader>fR` | Replace in path |

### Run · `<leader>r`

| Key | Action |
| --- | --- |
| `<leader>rm` | Run menu |
| `<leader>rn` | Run class |
| `<leader>rc` | Context run |
| `<leader>rr` | Rerun |
| `<leader>rt` | Run tests |
| `<leader>rf` | Rerun failed tests |
| `<leader>rs` | Stop |
| `<leader>rC` | Choose run configuration |

### Debug · `<leader>d`

| Key | Action |
| --- | --- |
| `<leader>dx` | Debug |
| `<leader>dc` | Context debug |
| `<leader>dv` | View breakpoints |
| `<leader>de` | Edit breakpoint |
| `<leader>dm` | Mute breakpoints |
| `<leader>db` | Toggle line breakpoint |
| `<leader>dC` | Run to cursor |
| `<leader>di` | Step into |
| `<leader>do` | Step over |
| `<leader>dr` | Resume |
| `<leader>dR` | Evaluate expression |
| `<leader>dw` | Activate debug tool window |

### Language / Refactoring · `<leader>l`

| Key | Action |
| --- | --- |
| `<leader>ll` | Quick refactorings list |
| `<leader>lr` | Rename |
| `<leader>lc` | Change signature |
| `<leader>lv` | Introduce variable |
| `<leader>li` | Inline |
| `<leader>lf` | Introduce field |
| `<leader>lm` | Extract method |
| `<leader>lC` | Introduce constant |
| `<leader>lp` | Introduce parameter |
| `<leader>lo` | Introduce parameter object |
| `<leader>le` | Encapsulate fields |
| `<leader>la` | Show intention actions |
| `<leader>lR` | Reformat code |
| `<leader>lI` | Inspect code |
| `<leader>lG` | Generate |

### Bookmarks · `<leader>b`

| Key | Action |
| --- | --- |
| `<leader>bm` | Bookmarks menu |
| `<leader>bs` | Show bookmarks |
| `<leader>bt` | Bookmarks tool window |
| `<leader>bb` | Toggle bookmark |
| `<leader>be` | Edit bookmark |
| `<leader>bp` | Previous bookmark |
| `<leader>bn` | Next bookmark |

### Go To · `<leader>g`

| Key | Action |
| --- | --- |
| `<leader>gd` | Go to declaration |
| `<leader>go` | Go to super method |
| `<leader>gD` | Go to type declaration |
| `<leader>gi` | Go to implementation |
| `<leader>gT` | Go to test |

### Search · `<leader>s`

| Key | Action |
| --- | --- |
| `<leader>sS` | Search everywhere |
| `<leader>su` | Find usages |
| `<leader>sn` | Show nav bar |
| `<leader>sa` | Go to action |
| `<leader>sc` | Go to class |
| `<leader>sf` | Go to file |
| `<leader>ss` | Go to symbol |
| `<leader>st` | Text search |

### Case Conversion · `<leader>c`

> Requires the **CaseConv** IDE plugin (`me.laria.code.idea_caseconv`). Works on a visual selection.

| Key | Result |
| --- | --- |
| `<leader>cm` | Case menu |
| `<leader>cc` | camelCase |
| `<leader>cp` | PascalCase |
| `<leader>cs` | snake_case |
| `<leader>cS` | SCREAMING_SNAKE_CASE |
| `<leader>cl` | lowercase |
| `<leader>cu` | UPPERCASE |
| `<leader>c.` | dot.case |
| `<leader>cw` | separate words |
| `<leader>ct` | Title Case |
| `<leader>c-` | dash-case |
| `<leader>cd` | Sentence case |

### Version Control · `<leader>G`

| Key | Action |
| --- | --- |
| `<leader>Gc` | Show local changes |
| `<leader>Gb` | Branches |
| `<leader>Gf` | Fetch |
| `<leader>Gp` | Push |
| `<leader>GP` | Commit & push |
| `<leader>Go` | Open pull requests |
| `<leader>Gm` | VCS menu |
| `<leader>Gg` | Check in (commit) |
| `<leader>Ga` | Annotate (blame) |
| `<leader>Gt` | VCS tool window |
| `<leader>Gr` | Rollback changed lines |
| `<leader>Gu` | Update project |

## Per-IDE Overrides

The same `~/.ideavimrc` is loaded by every JetBrains IDE, so the file ends with an `&ide` block for IDE-specific tweaks:

```vim
if &ide =~? 'pycharm'
  " PyCharm-only tweaks (e.g. Jupyter / scientific mode)
elseif &ide =~? 'webstorm'
  " WebStorm-only tweaks
elseif &ide =~? 'rider'
  " Rider-only tweaks
endif
```

Run `:echo &ide` to see the current IDE name.

## Finding Action IDs

Action IDs can change between IDE versions. If a mapping stops working, enable **`IdeaVim: Track Action Ids`** (open *Search Everywhere* / double-press Shift, type the command, toggle it on) — the IDE then shows the action ID of anything you trigger, ready to copy into your config.