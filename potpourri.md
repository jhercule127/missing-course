# Potpourri

## Daemons
Most computers have a series of processes that are always running in the background
rather than waiting for a user to launch them and interact them.
- These are called daemons and prorgams that run them often end with a `d`

The `systemd` is the most common solution for running and setting up daemon processes
- You can run `systemctl status` to list the current running daemons

`systemd` can be intereacted with the `systemctl` command in order to `enable`, `disable`, `start`, `stop`, and `restart`

## APIs

Most APIs have a similar format, they are structured URLs
- Where path and query parameters indicate what data you want to read or what action you want to perform
- Some APIs require authentication and this usually takes the form of some sort of **secret token**

OAuth is a protocol you will often see - a way to give you tokens that can 
"act as you" on a given service and ONLY used for particular reasons

### Common Command Line Flags/Patterns
- the `help` flag to display brief usage
- the `--dry-run` and `--interactive` flags
- You can have `--version` or `-V` print the version


