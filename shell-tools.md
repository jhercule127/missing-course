## The Shell
The (~) is short for “home” and ($) tells you are not root user
Shell is a programming environment, when shell is asked to execute a command it consults a environment variable called $PATH which lists locations of programs 

When you do the (ls) command, the (-) indicates that the given principal does not have the given permission.

Connecting programs
Two primary streams: input and output

Simplest form of redirection `< file` and `> file`
Echo hello > hello.txt
Cat < hello.txt

Using pipes, the (|) operator lets you “chain” programs such that the output of one is the input of another


In order to be root is to write to the `syses` file mounted under `/sys`
- Not exist on MacOS


In order to add root users on Linux -> write to '/etc/passwd'
https://linuxier.com/how-to-give-root-privileges-to-a-user-in-linux/

open is another command that can open file and it will know how to open it

---

### Shell Scripting

What makes shell scripting different from other scripting programming languages is that it is optimized for performing shell-related tasks. Thus, creating command pipelines, saving results into files, and reading from standard input are primitives in shell scripting, which makes it easier to use than general purpose scripting languages.


What does source do?
Commands will often return output using STDOUT, errors through STDERR, and return code to report errors 
- Value of 0 means it went OK anything else an error occurred 


Process substitution 
<( CMD ) will execute CMD and place the output in a temporary file and substitute the <() with that file’s name
- Useful when commands expect values to be passed by file instead of by STDIN


When launching scripts, often want to provide arguments that are similar, Bash has ways to make this easier
- Expanding expressions by carrying out filename expansion -> shell globbing

Wildcards -> can use ? And *. 
Curly braces -> whenever you have a common substring in a series of commands, you can use curly braces for bash to expand this automatically 

```bash
convert image.{png,jpg}
# expands to image.png image.jpg

mv *{.py,.sh} folder
will move all *.py and *.s files
```


There are tools such as spellcheck that will help find errors in bash scripts
It is good practice to write shebang lines using the (env) command that will resolve to wherever the command lives in the system, increasing portability of your scripts
- ENV makes use of the PATH environment variable
- `#!/usr/bin/env python`

---

### Finding how to use commands
Sometimes manages provide too much detail, TLDR pages are complimentary solution that focuses on giving example use cases of a command

Finding files 
The command `fd` is simple and fast alternative to ‘find’ command

Finding the code
Use `grep` , a generic tool for matching patterns from the input text
Many alternatives have been developed, including `ack`, `ag`, and `rg`

Finding shell commands
The `history` command will let you access your shell history programmatically
- Most shells, you can make use of ‘Ctrl + R’ to perform backwards search through your history
- Type substring you want to match for commands

You can also use ‘fzf’ which is a general purpose fuzzy finder

Another trick is history-based autosuggestions,
It can be enabled in zsh and it is great


Directory navigation tools: fasd, tree


Cmd: ls -Glath
- This shows the lists of files, sizes in human format, files ordered by recency and colorized
The -print0 and -0 options are used in the find command and its arguments to handle filenames that contain special characters, such as spaces, newlines, or other unusual characters.








Vim Text Editor

Start with tutorial, then stick with editor and keep doing until you feel comfortable


Vim has a rich history, it is a modal editor. It has different modes for inserting text vs manipulating text
Vim is programmable, keystrokes are commands
- Match the speed at which you think

Modes:
- Normal - moving around and making edits
- Insert - insert text
- Replace - replace text
- Visual - selecting blocks of text
- CMD - running a command

Insert - Enter ‘I’
Replace - Enter ‘R’
Visual - Enter ‘v’
Command-line - Enter ‘:’
Enter ESC to go back to normal mode

Vim config by defaults -> look at lecture notes
Some commands:
:q - quits
:w - saves file
:help <topic> - shows docs for topic


Vim maintains a set of open files called “buffers”. A Vim sessions has a number of tabs each of which has number of windows
- A given buffer may be open in multiple windows even within the same tab
Enter “:sp”


Vim is a programming language 
Movement
You should spent most of your time in Normal time
- Basic Movement ‘hjkl’ (left,down,up,right)
- Words: w (next word), b (beginning of word), e (end of word)
- Lines: 0 (beginning of line), ^ (first non-blank character), $ (end of line)
- Screen: H (top of screen), M (middle of screen), L (bottom of screen)
- Scroll: Ctrl-u (up), Ctrl-d (down)
- File: gg (beginning of file), G (end of file)


Editing commands

Commands:
- Enter ‘o/O’ to insert line below or above
- Enter ‘d{motion}’ to delete something
* e.g. dw is delete word, d$ is delete to end of line, d0 is delete to beginning of line
c{motion} change {motion}
- Use ‘dd’ to delete whole line
* e.g. cw is change word
* like d{motion} followed by i
* x delete character (equal do dl)
* s substitute character (equal to cl)

How to copy and paste
y to copy / “yank” (some other commands like d also copy)
- p to paste

You can highlight words in Visual mode and then copy/paste. To copy a whole line use ‘yy’ 

Use ‘u’ to redo last command, use ‘U’ to fix a whole line
Use ‘Ctrl + R’ to redo commands

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





Data Wrangling

Have data in one format and transform to another format. To wrangle data, we need two things: data to wrangle, and something to do with it


The `sed` is a stream editor that builds on top of the old `ed` editor. Short commands for how to modify the file
The s command is written on the form: `s/REGEX/SUBSTITUION/


Regular expressions are common.Very common patterns:
* . means “any single character” except newline
* * zero or more of the preceding match
* + one or more of the preceding match
* [abc] any one character of a, b, and c
* (RX1|RX2) either something that matches RX1 or RX2

Well, * and + are, by default, “greedy”. They will match as much text as they can. In some regular expression implementations, you can just suffix * or + with a ? to make them non-greedy


Another command that is helpful for data wrangling is sort and uniq
- Command `uniq -c` will collapse consecutive lines that are the same into a single line and count number of occurrences

Another command is Awk
Column-based stream processor, more focused on columned data
For example  awk ‘{print $2}’ | paste -sd
- Prints out the second column

awk programs take the form of an optional pattern plus a block saying what to do if the pattern matches a given line.
Awk is a programming language


Analyzing data,
There are other tools such as `bc`, a calculator that can from STDIN

Arguments wrangling
- Sometimes you want to do data wrangling to find things to install or remove base on some longer list
- xargs can be a powerful tool

The xargs takes of lines of input and turns them into arguments

rustup toolchain list | grep nightly | grep -vE "nightly-x86" | sed 's/-x86.*//' | xargs rustup toolchain uninstall



Exercises DATA WRANGLING
1.

sed -E -n "/.*a.*a.*a[^'s]$/p" /usr/share/dict/words | awk '{for (i=1; i<=NF; i++) print substr($i, length($i)-1, 2)}' | sort | uniq -c | sort -nk1,1 | tail -n 3

2. Redirecting output to same file? It is not unique to sed; it applies to other command-line tools and scripts where output redirection is used. If you overwrite a file while simultaneously trying to read from it, you face similar risks of data corruption or loss.

DO NOT DO sed s/REGEX/SUBSTITUTION/ input.txt > input.txt

3. For the exercise on mls.csv I used 
awk -F, '{ print $6, $7 }' mls.csv | tail -n +2




