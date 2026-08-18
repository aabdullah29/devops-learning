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

## Pipes and redirection
Pipes and redirection are fundamental shell concepts.

**Pipes** connect commands:
```bash
ls | grep ".txt"
```
The output of `ls` becomes the input to `grep`. Powerful for combining simple commands.

**Redirection** changes where output goes:
```bash
echo "Hello" > file.txt
echo "World" >> file.txt
```

Important:
- `>` overwrites the file
- `>>` appends to the file
- `2>` redirects errors
- `2>&1` sends both output and errors to the same place

This is important because:
- Many DevOps tasks involve filtering and transforming data.
- Log analysis uses pipes and redirection.
- Scripts often redirect output to files.

## Environment variables and PATH
Environment variables store configuration that programs can access.

Examples:
```bash
echo $HOME
echo $PATH
export DEBUG=1
```

Why it matters:
- Programs check environment variables to know how to behave.
- `PATH` tells the shell where to find commands.
- In DevOps, environment variables configure secrets, settings, and behavior.

I should remember:
- `export` makes a variable available to child processes.
- `which` and `command -v` show where a command actually is.
- `echo $VAR` shows a variable's value.

## Searching and filtering files
`grep` and `find` are essential tools for locating and filtering data.

`grep` searches inside files:
```bash
grep "error" /var/log/syslog
grep -r "function" ./src/
```

`find` searches for files:
```bash
find . -name "*.log"
find . -type f -size +10M
```

Why this matters:
- DevOps work involves searching logs and files constantly.
- `grep -r` is used to search entire codebases.
- `find` helps locate specific file types or sizes.

## Scheduling with cron
Cron allows you to schedule jobs to run automatically.

Example:
```bash
crontab -e
# Add: 0 2 * * * /path/to/script.sh
```

This runs the script every day at 2:00 AM.

Why it matters:
- Many DevOps tasks need to run on a schedule (backups, cleanups, checks).
- Cron is the standard way to automate recurring tasks in Linux.
- Understanding cron is essential for professional DevOps work.

## Bash scripting basics
Bash scripts automate repeated tasks.

Example:
```bash
#!/bin/bash
variable="value"
if [ -f "file.txt" ]; then
    echo "File exists"
fi
for item in one two three; do
    echo "$item"
done
```

Why it matters:
- DevOps professionals write scripts to automate deployments, testing, and maintenance.
- Understanding variables, conditionals, and loops is fundamental.
- Good scripts can save hours of manual work.

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

As I progress, I realize that:
- **Pipes and redirection** are the foundation of command-line power.
- **Environment variables** control how programs behave.
- **Searching tools** like grep and find are used every day in DevOps.
- **Scheduling with cron** automates repetitive work.
- **Bash scripting** multiplies productivity by automating complex tasks.

These concepts separate beginners from intermediate and professional-level Linux users.
