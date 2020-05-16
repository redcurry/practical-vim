# Notes for Practical Vim, 2nd Edition

The `Alt` command in the following table is a remapping
of the original command for the Dvorak keyboard.

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

When deleting many words, it's preferable to use one `dw` and repeat with `.` as needed,
rather than use a count with `dw`.
This is because a single `dw` has more granularity as is more flexible with undo and redo.
