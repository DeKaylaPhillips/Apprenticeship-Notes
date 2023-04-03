# VIM NOTES

**How to use VIM in VSCode to commit changes?:**

1. Open the file to commit changes to in VSCode
2. Make changes to file
3. Run command: `git commit` - this will open the Vim editor

## VIM Commands/Shortcuts

**Basic Movement:**

- h, j, k, l: move the cursor left, down, up, and right, respectively.
- 0: move to the beginning of the current line.
- $: move to the end of the current line.
- ^: move to the first non-blank character of the current line.
- G: move to the end of the file.
- gg: move to the beginning of the file.

**Editing:**

- i: insert text before the cursor.
- a: append text after the cursor.
- A: append text to the end of the current line.
- o: open a new line below the current line and start inserting text.
- O: open a new line above the current line and start inserting text.
- d: delete text. For example, "dw" deletes a word.
- x: delete the character under the cursor.
- u: undo the last change.
- Ctrl-r: redo the last undone change.
- yy: yank (copy) the current line.
- p: put (paste) the last yanked or deleted text after the cursor.

**Command Mode:**

- :w save the current file.
- :q quit Vim.
- :wq save the current file and quit Vim.
- :q! quit Vim without saving changes.
- :%s/pattern/replacement/g search and replace "pattern" with "replacement" throughout the file.
