## Debugging and Profiling
A golden rule in programming is that code does not do what you expect it to do, but what you tell it to do.

“The most effective debugging tool is still careful thought, coupled with judiciously placed print statements”
* A first approach to debug a program is to add print statements around where you have detected the problem, and keep iterating until you have extracted enough information to understand what is responsible for the issue.
* 2nd approach is to use logging in your program instead of ad hoc print statements 

Logging is better since:
- You can log to files, sockets, or even remote servers instead of standard output
- Logging supports severity levels
- New issues may appear better in logging


**TIP: make logs more readable by coloring code them**

### Third Party Logs
As you start building larger software systems you will most probably run into dependencies that run as separate programs

In UNIX systems, it is commonplace for programs to write their logs under `/var/log`
On Mac you can use `log show`

For logging under the system logs you can use the logger shell program.

```
logger "Hello Logs"
# On macOS
log show --last 1m | grep Hello
# On Linux
journalctl --since "1m ago" | grep Hello
```


## Debuggers


When printf debugging is not enough you should use a debugger. Debuggers are programs that let you interact with the execution of a program
In Python the debugger is `pdb`

There are commands that pdb supports. Note that since Python is an interpreted language we can use the pdb shell to execute commands and to execute instructions. ipdb is an improved pdb that uses the IPython



Whenever programs need to perform actions that only the kernel can, they use `System Calls`. There are commands that let you trace the syscalls your program makes.
In Linux there’s `strace` and macOS and BSD have `dtrace` or better `dtruss`

Some circumstances you meed need to look at the network packets to figure out the issue in your program. Tools like `tcpdump`
- Read contents of the network packets


### Static Analysis
Static analysis programs take source code as input and analyze it using coding rules to reason about its correctness.

There are also listing tools and code formatters that help with stylizing the code to look better for reading 



