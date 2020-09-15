# Notes for Practical Vim, 2nd Edition

The `Alt` command in the following table is a remapping
of the original command for the Dvorak keyboard or Visual Studio.

| Command [Alt]      | Description |
|--------------|-------------|
| `s`          | Change the current letter to anything.
| `S`          | Change from the beginning of the line to anything.
| `I`          | Insert from the begining.
| `;`          | Repeat last search used with the `f` or `F` commands.
| `,`          | Reverse the last search used with the `f` or `F` commands.
| `?<pattern>` | Search for `<pattern>` backwards.
| `:%s/<word>/<replace>/g` | Replace `<word>` with `<replace>` in the whole document.
| `:s/<word>/<replace>/g` | Replace `<word>` with `<replace>` for the selected lines in Visual mode.
| `*` | Search for the current word under the cursor.
| `n` [`-`] | Search for the next match.
| `N` [`_`] | Serach for the previous match.
| `db` [`eb`] | Delete word backwards.
| `daw` [`eaw`] | Delete "a word".
| `Ctrl+a` | Add 1 to the current or next number under the cursor.
| `Ctrl+x` | Subtract 1 from the current or next number under the cursor.
| `W` | Move by words separated by spaces (not punctuation).
| `g~`, `gU`, `gu` | Swap case, make uppercase, or make lowercase; followed by motion (e.g., `gUaw` to capitalize an entire word).
| `Ctrl+w` | While in Insert mode, delete back one word.
| `Ctrl+u` | While in Insert mode, delete back to the start of the line.
| `Ctrl+o` | While in Insert mode, switch to Normal mode for one command, then back to Insert mode.
| `Ctrl+r<register>` [`Ctrl+y`] | While in Insert mode, paste from the given register.
| `Ctrl+r, =` [`Ctrl+y, =`] | While in Insert mode, calculate expression after `=`
| `Ctrl+v<code>` | While in Insert mode, insert the character by the 3-digit code `<code>`
| `Ctrl+v, u<code>` | While in Insert mode, insert the Unicode character by the 4-digit code `<code>`
| `ga` | Show a character's decimal, hex, and octal numerical code
| `Ctrl+v<char>` | While in Insert mode, insert the `<char>` literally (e.g., tab)
| `Ctrl+k<code>` | While in Insert mode, insert the character represented by the 2-digit digraph `<code>`
| `R` | Replace mode (instead of Insert mode); use `gR` to treat single tab character as spaces
| `Insert` | Toggle between Replace and Insert mode
| `v`, `V`, `<Ctrl+v>` | Character-wise, line-wise, or block-wise Visual mode
| `gv` | Reselect last visual selection
| `o` | In Visual mode, go to the other end of the selection
| `vit` | Select text inside an HTML tag
| `U` | In Visual mode, make selected text uppercase

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

## Ex Commands

| Command [Alt]      | Description |
|--------------|-------------|
| `:[range]delete <x>`          | Delete specified lines into register `<x>`

Note: Use `https://github.com/tomtom/tcomment_vim` to add comment operation to vim.
