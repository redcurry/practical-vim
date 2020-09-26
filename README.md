# Notes for Practical Vim, 2nd Edition

The `Alt` command in the following table is a remapping
of the original command for the Dvorak keyboard or Visual Studio.

| Command [Alt]                 | Description                           |
|-------------------------------|---------------------------------------|
| `s`                           | Change the current letter to anything.
| `S`                           | Change from the beginning of the line to anything.
| `I`                           | Insert from the begining.
| `;`                           | Repeat last search used with the `f` or `F` commands.
| `,`                           | Reverse the last search used with the `f` or `F` commands.
| `?<pattern>`                  | Search for `<pattern>` backwards.
| `:%s/<word>/<replace>/g`      | Replace `<word>` with `<replace>` in the whole document.
| `:s/<word>/<replace>/g`       | Replace `<word>` with `<replace>` for the selected lines in Visual mode.
| `*`                           | Search for the current word under the cursor.
| `n` [`-`]                     | Search for the next match.
| `N` [`_`]                     | Serach for the previous match.
| `db` [`eb`]                   | Delete word backwards.
| `daw` [`eaw`]                 | Delete "a word".
| `Ctrl+a`                      | Add 1 to the current or next number under the cursor.
| `Ctrl+x`                      | Subtract 1 from the current or next number under the cursor.
| `W`                           | Move by words separated by spaces (not punctuation).
| `g~`, `gU`, `gu`              | Swap case, make uppercase, or make lowercase; followed by motion (e.g., `gUaw` to capitalize an entire word).
| `Ctrl+w`                      | While in Insert mode, delete back one word.
| `Ctrl+u`                      | While in Insert mode, delete back to the start of the line.
| `Ctrl+o`                      | While in Insert mode, switch to Normal mode for one command, then back to Insert mode.
| `Ctrl+r<register>` [`Ctrl+y`] | While in Insert mode, paste from the given register.
| `Ctrl+r, =` [`Ctrl+y, =`]     | While in Insert mode, calculate expression after `=`
| `Ctrl+v<code>`                | While in Insert mode, insert the character by the 3-digit code `<code>`
| `Ctrl+v, u<code>`             | While in Insert mode, insert the Unicode character by the 4-digit code `<code>`
| `ga`                          | Show a character's decimal, hex, and octal numerical code
| `Ctrl+v<char>`                | While in Insert mode, insert the `<char>` literally (e.g., tab)
| `Ctrl+k<code>`                | While in Insert mode, insert the character represented by the 2-digit digraph `<code>`
| `R`                           | Replace mode (instead of Insert mode); use `gR` to treat single tab character as spaces
| `Insert`                      | Toggle between Replace and Insert mode
| `v`, `V`, `<Ctrl+v>`          | Character-wise, line-wise, or block-wise Visual mode
| `gv`                          | Reselect last visual selection
| `o`                           | In Visual mode, go to the other end of the selection
| `vit`                         | Select text inside an HTML tag
| `U`                           | In Visual mode, make selected text uppercase

When deleting many words, using `dw` and repeating with `.`
is more granular than using a count with `dw`.
This will make it easier to undo.
But for replacing many words, using a count, like `c3w`, is probably better.

Typically, when an operator is invoked in duplicate it applies to the current line.
For example `gUgU` capitalizes the current line (`gUU` is a shortcut).

When using the dot command in Visual mode, it repeats the command on the same range of text,
which may not be desired when the text to act on is longer or shorter than the original.
Instead, use an equivalent command in Normal mode.

Replace every character in the selection (in any visual mode) with `r<char>`
where `<char>` is the new character.

In block-wise Visual mode, use `c` to change the topmost selected word and automatically
change all selected words below.

Similarly, in block-wise Visual mode, use `A` to append to each line selected,
even if the lines don't end in the same column.

In Command-Line mode, you can use many of the same commands as in Insert mode,
such as `Ctrl+w` and `Ctrl+u`.

## Ex and Shell Commands

| Command [Alt]                    | Shortcut | Description                  |
|----------------------------------|----------|------------------------------|
| `:[range]delete <x>`             | `:d`     | Delete specified lines into register `<x>`.
| `:[range]copy <address>`         | `:t`     | Copy lines in `[range]` to `<address>` (e.g., `:t$` copies the current line to the end of the file).
| `:[range]move <address>`         | `:m`     | Move lines in `[range]` to `<address>`.
| `@:`                             |          | Repeat the last Ex command.
| `:[range]normal <command>`       | `:norm`  | Execute a vim command in normal mode on the range (e.g., `:%normal i//` comments all lines).
| `Ctrl+D` and/or `<tab>`          |          | Show auto-completed commands.
| `:Ctrl+r Ctrl+w`                 |          | Copy the word under the cursor to the Ex command-line.
| `q:`                             |          | Open Ex command-line history window.
| `q/`                             |          | Open search history window.
| `:!<cmd> %`                      |          | Run `<cmd>` on the shell, passing the current file (`%`).
| `:read !<cmd>`                   | `:r`     | Send output of `<cmd>` to current file in vim.
| `:write !<cmd>`                  | `:w`     | Send all lines from vim to `<cmd>` as standard input.
| `:[range]write !<cmd>`           |          | Send lines in `[range]` to `<cmd>` as stdout.
| `:write !sh`                     |          | Since `sh` executes commands, it executes every line from vim.
| `[range]!<cmd>`                  |          | Send lines in `[range]` to stdin of `<cmd>`, and replace lines in `[range]` with output of `<cmd>`.
| `!<motion>`                      |          | Automatically fills in the range represented by the motion.
| `:source <file.vim>`             |          | Execute each Ex command from the script `<file.vim>`.

The `[range]` can be a single line number or a range in the form of `<start>,<end>`.

The `.` symbol represents the current line and the `$` symbol represents the last line,
so a range of `.,$` represents everything from the current line to the end of the file.

`%` represents all the lines in the current file (equilavent to `1,$`).

In Visual mode, typing `:` will automatically prepopulate the "visual" range,
so one can just start typing the Ex command.

The `<start>` and `<end>` may also be patterns in the form of `/<pattern>/`.
It may also be a mark, using `'<m>` where `<m>` is the mark.

Add or subtract from `<start>` or `<end>`, e.g., `.,/void/+3` represents
the lines starting at the current to the line containing `void` plus 3.

In the command-line history window (opened by `q:` or `q/`), you can use vim commands
to navigate and edit the history and execute edited commands by pressing Enter.

Note: Use `https://github.com/tomtom/tcomment_vim` to add comment operation to vim.

## Working with Files

| Command [Alt]                    | Shortcut | Description                  |
|----------------------------------|----------|------------------------------|
| `:ls`                            |          | List the buffers loaded by vim (when run like `vim *.txt`).
| `:bnext`, `bprev`                |          | Switch to the next or previous buffer, respectively.
| `:bfirst`, `blast`               |          | Switch to the first or last buffer, respectively.
| `Ctrl+^` or `Ctrl+6`             |          | Switch to the alternate buffer.
| `:buffer <n>`                    | `:b`     | Switch to the buffer `<n>`, which could be a number (listed by `:ls`) or name (file name).
| `:bufdo`                         |          | Execute an Ex command to all buffers
| `:bdelete <n1> <n2> ...`         | `:bd`    | Delete buffers `<n1>`, `<n2>`, and so on from memory (does not delete the files).
| `:<n>,<m> bdelete`               |          | Delete buffers from `<n>` to `<m>`.
| `:args`                          |          | Show all files (arguments) opened by vim (when run like `vim *.cs`).
| `:first`                         |          | Go to the first file in the argument list.
| `:next`                          |          | Go to the next file in the argument list.
| `:prev`                          |          | Go to the previous file in the argument list.
| `:argdo <cmd>`                   |          | Execute `<cmd>` on all files in the argument list (such as applying a script file).
| `:args <file1> <file2> ...`      |          | Set the argument list to the given values, which may be wildcards (e.g., `*.txt`) or a shell command enclosed in backticks.

In vim, a buffer is the contents of a file loaded into memory.

In the list shown by the `:ls` command, the `%` symbol is the current buffer
and the `#` symbol is the alternate file.
