# Linux

This section is focused on learning the fundamentals of Linux operating systems, command-line usage, and system administration.

## Core learning rule
For every command, understand:
- What is it?
- Why do I need it?
- What does it change?
- How can I check the result?

For example:

```bash
systemctl status ssh
```

Don't only memorize it. Understand:

> `systemctl` → communicates with systemd  
> `status` → asks for the current state  
> `ssh` → the service being inspected

This helps you learn commands as tools, not as random text.

## Topics
- Files & directories
- Permissions & ownership
- Users & groups
- Processes
- Services / systemd
- Packages
- Networking
- SSH
- Disk / memory / CPU
- Logs
- Bash basics

## Files
- `commands.md` — command reference and examples
- `notes.md` — personal notes and explanations

## Study goals
- Understand Linux filesystem structure
- Practice common shell commands
- Learn permission and ownership concepts
- Explore process and service management
- Use Bash for automation and daily tasks

## How to learn each command
Before using a command, ask:
1. What does this command do?
2. What system component does it interact with?
3. What output should I expect?
4. How do I verify the change after running it?

## Example workflow
```bash
systemctl status ssh
systemctl is-active ssh
ss -tlnp | grep ':22'
```

These three commands together answer:
- Is the service running?
- Is it active?
- Is it listening on the expected port?

That is the difference between memorizing a command and understanding Linux.
