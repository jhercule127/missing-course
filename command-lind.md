
# Command-line Environment

## Job Control
Sometimes a process is taking too long, you use `Ctrl-C` but how does it work and why does it sometimes fail?

Killing a process - your shell is using a UNIX communication mechanism called a signal
- When typing `Ctrl-C` this prompts the shell to deliver a `SIGINT` signal
- Signals are software interrupts

More generic signal for asking a process to exit gracefully is the `SIGTERM` signal
- To send this signal use the `kill` command

**Pausing and backgrounding processes**
For instance `SIGSTOP` pauses a process, typing `Ctrl-Z` will prompt shell to send a `SIGSTOP`
- Can continue the paused job in foreground or background using `fg` or `bg`


The `&` suffix in a command will run the command in the background. 
- For example `sleep 1000 &`

> [!TIP]
> Backgrounded processes are still children processes of your terminal 
> Can use `nohup` to prevent that from happening
 
A special signal is `SIGKILL` since it cannot be captured by the process and it will always terminate it immediately.


## Terminal Multiplexers
Allows you to multiplex terminal windows using panes and tabs so you can interact with multiple shell sessions
- Let you detach a current terminal sessions and reattach at some point later
- The command is `tmux`

`tmux` expects you to know its keybindings, and they have the form `<C-b>`
- it means press `Ctrl+b`, release `Ctrl+b` and then press x




### Hierarchy of objects
Session - they are independent workspaces with one or more windows
Windows - they are separate parts of the same session
Panes, like vim splits, lets you have multiple shells in the same visual display

You can exit a session at any point, this is called detaching (tmux will keep this session alive)
You can pick up the session up later by simply “attaching” to that session
You see that tmux basically offers two big features:
1. Window management in your terminal
2. and session management


If you’re interested in customizing your tmux experience I recommend that you read my Guide to Customizing your tmux.conf.

### Aliases

Most shells support aliasing, a shell alias is a short form for another command that your shell will replace automatically for you

**How to create alias?**
`alias alias_name="command_to_alias arg1 arg2"`

To make them persistent you need them in shell startup files



## Dotfiles

Many programs are configured using plain-text files known as **dotfiles** (because the file names begin with a (.), e.g. `~/.vimrc`, so that they are hidden in the directory listing ls by default).

Some other examples of tools that can be configured through dotfiles are:
* bash - `~/.bashrc`, `~/.bash_profile`
* git - `~/.gitconfig`

**How should you organize your dotfiles?** They should be in their own folder, under version control, and symlinked into place using a script. 
* Synchronization: you can update your dotfiles anywhere and keep them all in sync.
* Change tracking: you’re probably going to be maintaining your dotfiles for your entire programming career, and version history is nice to have for long-lived projects.

**What should you put in your dotfiles?** You can learn about your tool’s settings by reading online documentation or man pages. 

### Portability for dot files
If the configuration file supports it, use the equivalent of if-statements to apply machine specific customizations.

Check before using shell-specific features
`if [[ "$SHELL" == "zsh" ]]; then {do_something}; fi`

You can also make it machine-specific
`if [[ "$(hostname)" == "myServer" ]]; then {do_something}; fi`

