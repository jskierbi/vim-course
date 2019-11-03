## Section 3: Vim essentials

![1570530073552](../../.images/1570530073552.png)

**`[count]operation{motion}`**, eg: `11j`, `daw`, `dit`

### Command Mode

* **ctrl+f** (forward, page down)
* **ctrl+b** (backward, page up)
* **w**=word for**w**ard, **W**=word for**w**ard, ignore punctuation
* **b**=word **b**ack, **B**=word **b**ack, ignore punctuation
* **e**=word **e**nd, **E**=word **e**nd, ignore punctuation
* **z, enter** (scroll to cursor position)
* **0**=line beginning, **^**=first char in line, **$**=last char in line
* **{**=paragraph back, **}**=paragraph fwd
*  **gg**=first line, **G**=last line, **2G**=**2gg**=goto line 2
* **ctrl+g**=file info, **ctrl+g, g**=more file info
* **u**=undo, **ctrl+r**=redo
* **J**=concat line
* **a**=append ch**a**r, **A**=append line
* **i**=insert, **I**=insert at l**I**ne start
* **o**=insert line bel**o**w, **O**=insert line ab**O**ve

### Line mode:

* **:31** Go to line 31
* **:$** Jump to the end of the file
* **:^** Jump to the beginning of the file

### Deleting

* **x** delete character under the cursor
* **X** delete character before the cursor
* **dw** delete word (deletion starts where your cursor is)
* **d$ or D** - delete the line

`[count]operation{motion}`

### Navigation

* **ctrl+o**=navigate back
* **ctrl+i**=navigate forward
* **ctrl+]**=navigate to link (in documentation)
* **:{cmd} + <TAB>**=autocomplete

### Copy-Paste

* cut=**delete**, copy=**yank**, paste=**put**
* **dd** cut the line
* **p** or **P** paste the line (below or above current line)
* **"** specify register (0-9: std, like stack, a-z: named, **use uppercase to append**)
* **:reg 1z** show contents of registers 1 and z
* `:%y`=yank whole file

### VIM objects guide:

https://blog.carbonfive.com/2011/10/17/vim-text-objects-the-definitive-guide/

* **ci'** change inside single quote (delete + enter insert mode)
* **ca'** change an object including white space (includes quotes)
* **di'** delete inside single quite
* **dit** delete inside a HTML tag

### Search

* **f{char}**=**f**ind next char **F{char}**=find prev char
* **t{char}**=**t**ill next char **T{char}**=till prev char (place cursor before the character)
* **;**=repeat find char fwd **,**=repeat find char backw
  * Example: `Delete THIS<<--- word.` -> *fT, dtW* (find T, delete till W)
* **/**=find phrase fwd **?**=find phrase backw
* **n**=next match **N**=prev match
* **:nohls** remove highlights from current search
* *** or #** match whole word (forwards, backwards)
* **:[range]s/old/new/[flags]** <u>substitute old with new</u> (line, only replaces first occurance)
  * **[flags]** **g** all occurrences on the line
  * **[range]** **1,5**=lines from 1 to 5, **$**=last line, **.**=first line, **%**=all lines (entire file)
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
* Reply **multiple times**:
  * `2@c` apply macro 2 times
  * `:26,35normal @c`from line 26 to 35
  * `:.,+5normal @c` from current line to next 5 lines
* Saving macros, `.vimrc`:
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

### Buffers

* `:e`  = open new buffer
  * Shell expansion works (eg. `:e readme*`)
* `:ls` = list buffers
* `:b{name|num}` = switch buffer
* `:bn`=next `:bp`=prev `:bf`=first `:bl`=last
* `:badd`=add buffer `:bd`=delete
  * `:bd 3`
  * `:badd buf-dad.txt`
  * `:1,3bd`=range delete (1 to 3)
* `:bufdo`=execute command on all buffers
  * `:bufdo %s/#/*/g | w` = substitute and write (pipe=command separator)
* `set hidden`=hide buffers instead of closing when switching
* `:E`=open explorer
  * `:bd`=close explorer without opening anything (delete current buffer)

### Windows

* **ctrl+w, ctrl+w**=switch between windows
* **:q**=close window, `ctrl+w, q`=close window
* `:sp {name|num}`=s**p**lit horizontally `:vs {name|num}`=split **v**ertically
  * `ctrl+w, s`=**s**plit horizontally, `ctrl+w, v`=split **v**ertically
* `:on`=only, leave only current window open
* **ctrl+w, h/j/k/l**=focus window left/down/up/right
* **ctrl+w, +/-/>/<**=increase/decrease height/width
* **ctrl+w, H/J/K/L**=move window to far left/bottom/top/far right
* ``:windo {operation}``, `:bufdo {operation}`

### JSON
* `:%!jq .` formats json
  * Requires: `sudo apt install jq`

### External programms
* `:{range}! <cmd>` filter lines through external program
