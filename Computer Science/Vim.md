Vim is an open source configurable text editor. It is an improved version of the text editor Vi. Vim allows the addition of extensions through the use of vim script. This creates an editor which can be easily customized. Neo-Vim is a fork of Vim that has been expanded to have support for [[Lua]] scripting.

Vim is a **modal editor** which has four main modes. These modes are:
- **Normal mode** is the default mode which enables text navigation, copy/paste, and undo/redo. This is accessed through exiting other modes with `Esc` or `Ctrl+c`.
- **Insert mode** allows for plain text editing through typing. It is accessed with `i` for direct switch, `a` for append character, `o` for append newline in front and `O` for behind. `s` can also be used to delete selected character and `S` to delete the line and enter the mode.
- **Visual mode** which selects text areas and puts them within the buffer. It is entered with `v` which starts the selection. `V` can be used to select the entire line.
- **Command-line mode** can be accessed with `:` and enables commands to be written. Key operations include `:w` for save, `:q` for quit, and `:%s/old/new/g` for search and replace with regex patterns.
- **Replace mode** allows text to be written over. This is called with `R`. A single character can be replaced with `r`.

# Movements
Basic movement with Vim can be done with the arrow keys or `h`, `l` for left and right, and `h`, `k` for up and down. These are further expanded with jump forwards to start of word `w`,  jump forwards to end of word `e`, jump backwards to start `b`, and jump backwards to end `ge`. Screen movements can be sone with top `H`, middle `M`, and bottom `L`.

Move to matching character is done with `%` which jumps to the other bracket. Jump to first occurrence on the line is `fx`, where `x` is any character and `tx` does before. Capitalising `F` or `T` goes backwards. `;` repeats the movement forwards and `,` backwards. Paragraph jumps can be done with `}` for forwards and `{` for backwards. Jump to local declaration is `gd`, and global `gD`. Jump to start of line is done with `0`, and end is `$`. Jump to first line of document is `gg`.

Jump to line number can be done with `:#` in command line mode and `#G`. Relative line jumps can be done with `#k` and `#j`. 

Screen movements are done with `Ctrl+e`, `Ctrl+y` for one line movement and `Ctrl+b` and `Ctrl+f` for page. `zz` positions the cursor to be in the middle of the screen and `zt` and `zb` for top and bottom of the screen.

# Yanks
Copy (yank) is `y` while cut/delete is `d`. Yank puts and item into a generic register. `yy` can yank a line while `#yy` yanks `#` number of lines. `yw` yanks characters from the cursor position to start of next word. `yiw` yanks the word.

There are many different registers, which can be seen with `:reg` command.

Indent can be done with `>>` and de-indent with `<<`. A block can be combined with `>%` or an inner block with `>ib`

# Marks & Macros
Marks are a location which can be jumped to. These are listed with `:marks`. To set a mark use `mx` where `x` is any character and `` `x `` can be used to jump to the mark. This text can also be yanked.

Macros can be recorded with `qx` which starts recording macro `x`. To stop recording click `q` again. A macro can be run with `@x`.

# Windows & Tabs
Tabs can be moved left and right with `gt` and `gT` or `:tabn` and `:tabp`. You can move to specific tab numbers with `#gt`.

To open a new file for editing use `:e file`. Split window is done with `Ctrl+wv` to split vertical. To switch between windows use `Ctrl+ww`. To close use `Ctrl+wq`.
