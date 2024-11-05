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
- Most shells, you can make use of `Ctrl + R` to perform backwards search through your history
- Type substring you want to match for commands

You can also use `fzf` which is a general purpose fuzzy finder

Another trick is history-based autosuggestions,
It can be enabled in zsh and it is great


Directory navigation tools: fasd, tree


Cmd: ls -Glath
- This shows the lists of files, sizes in human format, files ordered by recency and colorized
The -print0 and -0 options are used in the find command and its arguments to handle filenames that contain special characters, such as spaces, newlines, or other unusual characters.


