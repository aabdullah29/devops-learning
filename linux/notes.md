# Linux Notes

## Overview
Linux is the foundation of most DevOps workflows. Learning Linux well helps with server administration, scripting, containers, and cloud infrastructure.

## Key concepts
- Filesystems and directories
- Users, groups, and permissions
- Processes and daemons
- Package managers
- Networking and SSH
- Logs and troubleshooting
- Shell scripting with Bash

## Learning method for commands
For every command, ask:
- What does it do?
- Why would I use it?
- What does it change?
- How do I confirm the change?

## Example
```bash
systemctl status ssh
```

Break it apart:
- `systemctl` = talks to systemd
- `status` = asks for current state
- `ssh` = the service being checked

Then verify with:
```bash
systemctl is-active ssh
ss -tlnp | grep ':22'
```

This helps you understand the command in context instead of memorizing it.

## Practical Linux mindset
- Start with the command output
- Understand what changed in the system
- Use a second command to confirm the result
- Learn the difference between checking state and changing state

## Good habits
- Practice in a VM or container
- Write down the purpose of each command in your own words
- Test commands in safe scenarios before using them in production
- Always verify your result after running a command

## Typical Linux workflow
1. Check current state
2. Make a change if needed
3. Verify the result
4. Review logs if something fails
5. Repeat with a clear understanding

## Useful habit
Practice commands in a VM or container and write down the purpose of each command as you use it.
