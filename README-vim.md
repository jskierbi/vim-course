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
* **J** concat line
* **a**, **A** enter edit mode (next char, end of line)
* **i**, **I** enter edit mode (prev char, beginning of the line)
* **o**, **O** enter edit mode (line below, line above)

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
* **"** specify register (0-9: std, like stack, a-z: named, **use uppercase to append**)
* **:reg 1z** show contents of registers 1 and z

### Search

* **f{char}**=find next char **F{char}**=find prev char
* **t{char}**=till next char **T{char}**=till prev char (place cursor before the character)
* **;**=repeat find char fwd **,**=repeat find char backw
  * Example: `Delete THIS<<--- word.` -> *fT, dtW* (find T, delete till W)
* **/**=find phrase fwd **?**=find phrase backw
* **n**=next match **N**=prev match
* **:nohls** remove highlights from current search
* *** or #** match whole word (forwards, backwards)
* **:[range]s/old/new/[flags]** <u>substitute old with new</u> (line, only replaces first occurance)
  * **[flags]** **g** all occurrences on the line
  * **[range]** 1,5=lines from 1 to 5, $=last line, .=first line, %=all lines (entire file)
  * **1,5s/for/FOR/g** replace all occurrences of FOR in lines 1 to 5

### Text Objects

* {operator}{a|i}{object}
  * Opearators: **d**=delete, **c**=change, **y**=yank
  * Objects: **s**=sentence, **w**=word, **p**=paragraph, **t**=tag, **b**=block

### Macros

* **q{register}(sequence)q**: record macro to {register}
* **@{register}**=reply macro, **@@**=reply last macro
* Macros are stored in named registers
  * Use upper-case to append
  * To modify: paste, modify and yank
* Reply multiple times:
  * `2@c` apply macro 2 times
  * `:26,35normal @c`from line 26 to 35
  * `:.,+5normal @c` from current line to next 5 lines
* Saving macros, `vimrc`:
  * `let @d = '<contents>'` only for initialization, may be overwritten
  * Special cars (enter, esc): when in insert mode, `ctrl+v` followed by `enter` or `esc`

### Visual Mode

* **v**, **V**, **ctrl+v** visual mode: character, line, block
* **gv** reselect previous selection
* `:center`, `:left`, `:right` center selected text
* Commands:
  * **I**, **A** insert mode at beginning/end of the selection
  * **c** change
* Mapping
  * Example: `map <F3> i<ul><CR><Space><Space><li></li><CR><Esc>0i<ul><Esc>kcit`
  * **map**, **vmap**, **nmap**: map for all/visual/normal modes