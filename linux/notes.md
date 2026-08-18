# Linux Notes

`notes.md` is for your own learning notes — things you understand, explanations, mistakes, and important concepts.

## Root user
`root` is the administrator user in Linux. It has full power over the system.

Example:
```bash
sudo apt update
```

Why it matters:
- Regular users cannot always install packages or change system files.
- `sudo` gives temporary administrator privileges.

## sudo
`sudo` allows a normal user to run a command with administrator privileges.

Example:
```bash
sudo apt update
```

Important:
- Use it carefully.
- It changes the current command's permissions, not the user permanently.

## Services
A service is a background process managed by `systemd`.

Check a service:
```bash
systemctl status ssh
```

Start a service:
```bash
sudo systemctl start ssh
```

Enable a service at boot:
```bash
sudo systemctl enable ssh
```

Why this matters:
- Many Linux tools run as services.
- Services must be enabled and running for programs like SSH, web servers, and databases.

## Files and directories
Linux organizes everything under a root filesystem `/`.

Common directories:
- `/etc` = configuration files
- `/home` = user files
- `/var` = logs and changing data
- `/usr` = installed software
- `/tmp` = temporary files

Example:
```bash
ls /etc
ls -la /home
```

## Permissions
Permissions decide who can read, write, or execute a file.

Example:
```bash
ls -l script.sh
chmod +x script.sh
```

Key idea:
- `r` = read
- `w` = write
- `x` = execute

## Users and groups
Linux uses users and groups to control access.

Example:
```bash
whoami
id
```

This helps you understand which account is running commands and what groups it belongs to.

## Processes
A process is a running program.

Example:
```bash
ps aux
ps -ef | grep ssh
```

This helps you check whether a program is still running.

## Networking
Linux networking is about interfaces, IP addresses, routes, and ports.

Examples:
```bash
ip -br addr
ip route
ping -c 4 8.8.8.8
```

I should remember:
- `ip addr` shows network interfaces
- `ping` checks connectivity
- `ss` checks listening ports

## SSH
SSH is used to securely connect to remote systems.

Examples:
```bash
ssh devops@192.168.187.129
systemctl status ssh
ss -tlnp | grep ':22'
```

I should remember:
- SSH uses port 22 by default.
- If the service is active and port 22 is listening, the SSH server is working.

## Logs
Logs are the record of system activity and failures.

Example:
```bash
journalctl -p 3 -b --no-pager
```

This shows current boot errors.

## Packages
Linux packages are software installed from repositories.

Examples:
```bash
sudo apt update
sudo apt upgrade
apt list --installed
```

Important idea:
- `apt update` refreshes package information.
- `apt upgrade` installs available updates.

## Important habit
For every command, I should ask:
- What does it do?
- Why do I need it?
- What does it change?
- How can I verify the result?

Example:
```bash
systemctl status ssh
```

This is not just a command to memorize. It is a way to check the state of a service.

## My learning summary
Linux is easier to learn when I practice commands in a VM and then verify the result with another command. I should not memorize commands blindly; I should understand what they do and how to confirm the change.
