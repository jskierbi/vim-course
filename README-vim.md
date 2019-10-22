## Section 3: Vim essentials

![1570530073552](../../.images/1570530073552.png)

`[count]operation{motion}`

### Command Mode

* **ctrl+f** (forward, page down)
* **ctrl+b** (backward, page up)

Vim understands objects such as: words, sentences, lines, paragraphs

* **w** (right one word, punctuation is a separator)
* **W** (right one word, whitespace is a separator)
* **b** (left one word, whitespace is a separator)
* **B** (left one word, whitespace is a separator)
* **11j**, **11k** (11 lines down, 11 lines up)
* **z + enter** (reposition text to cursor position)
* **0** (zero: jump to the beginning of the line)
* **^** (caret: jump to first character in the line, like in regex)
* **$** (jump to last character in the line, like in regex)
* **2gg** (go to line 2), if you don't specify line number: go to first line
* **2G** (go to line 2), if you don't specify line number: go to last line
* **ctrl+g**: display file information
* **ctrl+g, g**: display more detailed file information
* **{** or **}** (paragraf back, paragraph forwards)
* **u** undo (same as ctrl-z in other editors)
* **ctrl+r** redo (same as ctrl+shift+z or ctrl+y in other editors)

### Line mode:

* **:31** Go to line 31
* **:$** Jump to the end of the file
* **:^** Jump to the beginning of the file

### Settings

* `:set ruler` set ruler on (line number displayed all the time)
* `:set noruler` set ruler off
* `:set ruler!` toggle ruler
* `:set nowildmenu` disable wildmenu from tab-completion

### Deleting

* **x** delete character under the cursor
* **X** delete character before the cursor
* **dw** delete word (deletion starts where your cursor is)
* **d$ or D** - delete the line

`[count]operation{motion}`

### Navigation

* **ctrl+o** navigate back
* **ctrl+i** navigate forward
* **ctrl+]** navigate to link (in documentation)
* **ctrl+w, w** jump between open windows (when documentation is open)

Command line completion:

* **:h d** (then press tab) -> will show autocomplete list of available options

### Copy-Paste

* cut=**delete**, copy=**yank**, paste=**put**
* **dd** cut the line
* **p** or **P** paste the line (below or above current line)
* **"** specify register (0-9: std, like stack, a-z: named, use uppercase to append)
* **:reg 1z** show contents of registers 1 and z



### VIM objects guide:

https://blog.carbonfive.com/2011/10/17/vim-text-objects-the-definitive-guide/

* **ci'** change inside single quote (delete + enter insert mode)
* **ca'** change an object including white space (includes quotes)
* **di'** delete inside single quite
* **dit** delete inside a HTML tag