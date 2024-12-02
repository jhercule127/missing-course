## Remote Machines
Its really common to work with remote machines, where you commonly use ssh

`Executing commands: "ssh foobar@server ls" will execute ls in the home folder of foobar`

SSH Keys: key based authentication exploits public-key cryptography to prove to the server that the client owns the secret private key without revealing the key
- Do not need to enter password every time however treat `~/.ssh/id_rsa` as a password
To generate a pair, you use `ssh-keygen`


**Key based authentication**
SSH will look into `.ssh/authorized_keys` to determine which clients it should let in

Another command that helps is `ssh-copy-id` installs an SSH key on a server as an authorized key. Its purpose is to provide access without requiring a password for each login.
- An authorized key in SSH is a public key used for granting login access to users. 
~
**Copying files over SSH**

There are many ways to copy files:
- `ssh+tee`, by doing `cat localfile | ssh remote_server tee serverfile`
- `also using scp is useful for large files/directories`

**SSH Configuration**
Instead of crediting shell aliases for ssh commands, there is a better alternative. Allows you to ssh without referring to private key each time - reduces authentication


`~/.ssh/config`
```
Host vm
    User foobar
    HostName 172.16.174.141
    Port 2222
    IdentityFile ~/.ssh/id_ed25519
    LocalForward 9999 localhost:8888

# Configs can also take wildcards
Host *.mit.edu
    User foobaz

Server side configuration is usually specified in /etc/ssh/sshd_config
```

### Port Forwarding

Many scenarios you will run into software that listens to specific ports in the machine.
What if a remote server does not have its ports directly available through the network/internet?

This is called port forwarding and has two flavors: Local Port Forwarding and Remote Port Forwarding

**Use Local Port Forwarding when you need to access a service on a remote server securely from your local machine.**
![Alt text](./pictures/localhost.png)

Use Remote Port Forwarding when you want to allow external access to a service running on your local machine from a remote server.
![Alt text](./pictures/yourhost.png)



### Exercises
1. Question: Now use pgrep to find its pid and pkill to kill it without ever typing the pid itself. 
- Answer: `pgrep sleep and pkill sleep (had to install proctools)`

2. Question: Write a bash function called pidwait that takes a pid and waits until the given process completes. You should use sleep to avoid wasting CPU unnecessarily.
- Answer:
```
pidwait(){
   local pid=$1
   check_process=$(kill -0 "$pid")
   while $check_process; do
       echo "checking $pid" 
       sleep 1
       check_process=$(kill -0 "$pid")
   done	   
   echo "done waiting!"

}

```

3. I followed this tutorial: https://hamvocke.com/blog/a-quick-and-easy-guide-to-tmux/

**Aliasing**


1. Create an alias dc that resolves to cd for when you type it wrongly.
- Answer: Changed `clear` to `cl` alias

2. Run `history | awk '{$1="";print substr($0,2)}' | sort | uniq -c | sort -n | tail -n 10 to get your top 10 most used commands`

**Dotfiles**

I cloned this repo:  https://github.com/anishathalye/dotfiles/tree/master. I need to check what to include in `~/.vimrc` and `/.zshrc`
- also check out what was done to `~/.tmux` 

**See Tmux docs on the lecture page for customization**
