
# Vim Text Editor

Vim has a rich history, it is a modal editor. It has different modes for inserting text vs manipulating text
Vim is programmable, keystrokes are commands
- Match the speed at which you think

Modes:
- **Normal** - moving around and making edits
- **Insert** - insert text
- **Replace** - replace text
- **Visual** - selecting blocks of text
- **CMD** - running a command

Insert - Enter `I`
Replace - Enter `R`
Visual - Enter `v`
Command-line - Enter `:`
Enter `ESC` to go back to normal mode

Vim config by defaults -> look at lecture notes
Some commands:
`:q` - quits
`:w` - saves file
:help <topic> - shows docs for topic


Vim maintains a set of open files called “buffers”. A Vim sessions has a number of tabs each of which has number of windows
- A given buffer may be open in multiple windows even within the same tab
Enter “:sp”


Vim is a programming language 

### Movement
You should spent most of your time in Normal time
- Basic Movement `hjkl` (left,down,up,right)
- Words: w (next word), b (beginning of word), e (end of word)
- Lines: 0 (beginning of line), ^ (first non-blank character), $ (end of line)
- Screen: H (top of screen), M (middle of screen), L (bottom of screen)
- Scroll: `Ctrl-u` (up), `Ctrl-d` (down)
- File: `gg` (beginning of file), `G` (end of file)


### Editing commands

Commands:
- Enter `o/O` to insert line below or above
- Enter `d{motion}` to delete something
- e.g. dw is delete word, d$ is delete to end of line, d0 is delete to beginning of line
c{motion} change {motion}
- Use `dd` to delete whole line
- e.g. `cw` is change word
- like d{motion} followed by i
- x delete character (equal do dl)
- s substitute character (equal to cl)

**How to copy and paste?**
y to copy / “yank” (some other commands like d also copy)
- p to paste

You can highlight words in Visual mode and then copy/paste. To copy a whole line use ‘yy’ 

Use `u` to redo last command, use ‘U’ to fix a whole line
Use `Ctrl + R` to redo commands

Visual modes:
Are for selecting chunks of texts
* Visual: v
* Visual Line: V
* Visual Block: Ctrl-v

When you make an edit and if you need to repeat it again, type in ‘.’ (Dot) to make the same edit elsewhere

Replace command
To replace a single character, Enter ‘r’ . To replace multiple characters Enter ‘R’ 

Search Command
Type ‘/‘ followed by phrase to search for a phrase.
- To search for the same phrase again, type ’n’
- To search in the opposite direction ’N’

Setting an option to help with search
- You can set “:set hls” then search as normal to highlight the search
- “:set is” shows partial matches for a search phrase
- To switch them off just add “no” to the option after “:set”

Matching Parenthesis Search
Type ‘%’ to find a matching ), ], or }

Substitute Command
Type ‘:s/old/new/g’ to substitute new for old in a line (all occurrences)
- To change every occurrence in the whole file: :%s/old/new/g or for confirmation :%s/old/new/gc


Execute external command:
Enter “:!” Then type in any command

Selecting Text to write
- Type ‘v’ and move the cursor to highlight texts you want to write
- Press the “:” and type “w TEST”
It should write the selected lines to the file TEST

Also “:r FILENAME” retrieves the FILENAME and puts it below the cursor position

Cool tip: “:r !ls” reads the output of the command and puts it below the cursor

To append NEXT to the cursor, Enter “a” and make edits

Command Line completion **
Make sure Vim is not in compatible mode - “:set nocp”
Press CTRL+D to see list of commands that start with something (possible completions)
Pressing <TAB> will get Vim to complete (one completion)

For help on the vimrc file you look at “:help vimrc-intro"






