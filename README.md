## Section 3: Vim essentials

![1570530073552](../../.images/1570530073552.png)

### Command Mode

* **ctrl+f** (forward, page down)
* **ctrl+b** (backward, page up)

Vim understands objects such as: words, sentences, lines, paragraphs

* **w** (right one word, punctuation is a separator)
* **W** (right one word, whitespace is a separator)
* **b** (left one word, whitespace is a separator)
* **B** (left one word, whitespace is a separator)

* **z + enter** (reposition text to cursor position)
* **0** (zero: jump to the beginning of the line)
* **^** (caret: jump to first character in the line, like in regex)
* **$** (jump to last character in the line, like in regex)
* **2gg** (go to line 2), if you don't specify line number: go to first line
* **2G** (go to line 2), if you don't specify line number: go to last line
* **ctrl+g**: display file information
* **ctrl+g, g**: display more detailed file information

### Line mode:

* **:31** Go to line 31
* **:$** Jump to the end of the file
* **:^** Jump to the beginning of the file

### Settings

* `:set ruler` set ruler on (line number displayed all the time)
* `:set noruler` set ruler off
* `:set ruler!` toggle ruler

### Deleting

* **x** delete character under the cursor
* **X** delete character before the cursor
* **dw** delete word (deletion starts where your cursor is)
* **D** (same as **d$**) - delete the line

### [count]operation{motion}