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
![Alt text](./localhost.png)

Use Remote Port Forwarding when you want to allow external access to a service running on your local machine from a remote server.
![Alt text](./yourhost.png)
