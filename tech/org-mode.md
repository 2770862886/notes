#+STARTUP: content

* Emacs PlugIns
** auto-complete
** company
** flycheck
** helm
** golden-ratio
** jedi
** paredit
** rainbow-delimeters
** undo-tree
** nyan-mode
** yasnippet
* Org Mode Hotkeys
** Cursor Motion
|-----+-----------+-----------------------------------|
| No. | KeyStroke | Description                       |
|-----+-----------+-----------------------------------|
|   1 | C-c C-n   | Next heading.                     |
|   2 | C-c C-p   | Previous heading.                 |
|   3 | C-c C-f   | Next heading same level.          |
|   4 | C-c C-b   | Previous heading same level.      |
|   5 | C-c C-u   | Backward to higher level heading. |
|-----+-----------+-----------------------------------|
** Structrue Editing
|--------------------+--------------------------------------------------------------------------------------------------------------------------------|
| M-<RET>            | Insert new heading with same level as current. If the cursor is in a plain list item, a new item is created (see Plain lists). |
|                    | When this command is used in the middle of a line, the line is split and the rest of the line becomes the new headline1.       |                                                                                                                               |
| M-S-<RET>          | Insert new TODO entry with same level as current heading.                                                                      |
| <TAB>              | in new, empty entry.In a new entry with no text yet, <TAB> will cycle through reasonable levels.                               |
| M-<left>/<right>   | Promote/demote current heading by one level.                                                                                   |
| M-S-<left>/<right> | Promote/demote the current subtree by one level.                                                                               |
| M-S-<up>/<down>    | Move subtree up/down (swap with previous/next subtree of same level).                                                          |
| C-c C-w            | Refile entry or region to a different location. See Refiling notes.                                                            |
| C-x n s/w          | Narrow buffer to current subtree / widen it again                                                                              |
|--------------------+--------------------------------------------------------------------------------------------------------------------------------|
** C-c C-t: Mark a line of text with TODO
   SCHEDULED: <2011-04-13 Wed>
** Shift-Meta-Enter: Create a new TODO item
** Shift-Tab: Callaps all the node and uncallaps
** C-c C-l: Modify a link after cursor moving on the link
** C-c C-s: To run org-schedule. The calendar pops up. I can either enter or click the desired date.

** Table Related Issue
*** Hotkey
|-----+----------------------+---------------------------------------------------------------------------------------------------------------------------|
| No. | KeyStroke            | Description                                                                                                               |
|-----+----------------------+---------------------------------------------------------------------------------------------------------------------------|
|   0 | C-c vbar             | convert the active region to table. if every line contains <TAB>, the function assumes the material is tab seperated.     |
|     |                      | if every line contains a comma, comma-seperated values are assumed. if not, lines are splite at whitespace into fields.   |
|     | C-u C-c vbar         | If you want to force the comma as a field separator                                                                       |
|     | C-u C-u C-c vbar     | If you want to force TAB as a field separator                                                                             |
|     | C-u C-u C-u C-c vbar | If you want to force a specific number of spaces                                                                          |
|-----+----------------------+---------------------------------------------------------------------------------------------------------------------------|
|   1 | C-c C-c              | Re-aligning                                                                                                               |
|   2 | <TAB>                |                                                                                                                           |
|   3 | <RET>                |                                                                                                                           |
|   4 | S-<TAB>              |                                                                                                                           |
|-----+----------------------+---------------------------------------------------------------------------------------------------------------------------|
|   5 | M-left or M-right    | move column left or right                                                                                                 |
|   6 | M-S-left             | kill current column                                                                                                       |
|   7 | M-S-right            | insert a column to the left of the cursor                                                                                 |
|   8 | M-up or M-down       | move the current row up or down                                                                                           |
|   9 | M-S-up               | kill current row or horizontal line                                                                                       |
|  10 | M-S-down             | insert a row above the cursor                                                                                             |
|  11 | C-c -                | insert a horizontal line below the current row, with a prefix argument, the line is created above the current line        |
|  12 | C-c <RET>            | insert a horizontal line below the current row, and move the cursor below the current row                                 |
|  13 | C-c ^                | sort the table lines in the region. the position of the point indicates the column to be used for sorting, and the region |
|     |                      | of lines is between the nearest horizontal seperater lines, or the entire table.                                          |
|-----+----------------------+---------------------------------------------------------------------------------------------------------------------------|
*** Grouping Columns
|---+----+-----+-----+-----+---------+---------|
|   |  N | N^2 | N^3 | N^4 | sqrt(n) | sqrt(N) |
|---+----+-----+-----+-----+---------+---------|
| / | <> |   < |     |   > |       < |       > |
| # |  1 |   1 |   1 |   1 |       1 |       1 |
| # |  2 |   4 |   8 |  16 |  1.4142 |  1.1892 |
| # |  3 |   9 |  27 |  81 |  1.7321 |  1.3161 |
|---+----+-----+-----+-----+---------+---------|
** Agenda Related Issue