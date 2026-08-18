# Linux Commands

## Useful quick reference

| Goal | Command |
|---|---|
| OS info | `cat /etc/os-release` |
| CPU count | `nproc` |
| CPU info | `lscpu` |
| RAM/swap | `free -h` |
| Disk usage | `df -h` |
| Root disk usage | `df -h /` |
| Disk/partitions/LVM | `lsblk` |
| Network/IP | `ip -br addr` |
| Test network | `ping -c 4 8.8.8.8` |
| Hostname | `hostname` |
| Detailed system info | `hostnamectl` |
| Files & directories | `ls`, `cd`, `mkdir`, `cp`, `mv`, `rm`, `find` |
| Permissions & ownership | `ls -l`, `chmod`, `chown`, `whoami` |
| Users & groups | `whoami`, `id`, `sudo` |
| Processes | `ps`, `top` |
| Services / systemd | `systemctl status`, `systemctl start`, `systemctl enable` |
| Packages | `sudo apt update`, `apt list --upgradable`, `sudo apt upgrade` |
| SSH | `ssh`, `ssh-keygen`, `ssh-copy-id` |
| Logs | `journalctl`, `tail -f /var/log/syslog` |
| Listening ports | `ss -tlnp` |
| Boot time | `systemd-analyze` |
| System errors | `journalctl -p 3 -b --no-pager` |
| Installed packages | `apt list --installed`, `dpkg -l` |
| Manual packages | `apt-mark showmanual` |
| Change password | `passwd` |
| Pipe commands | `command1 | command2` |
| Redirect output | `command > file`, `command >> file` |
| Redirect errors | `command 2> error.txt`, `command 2>&1` |
| Search text in files | `grep "text" file.txt`, `grep -r`, `grep -i` |
| Find files | `find . -name file.txt`, `find . -type f` |
| Show environment vars | `printenv`, `env`, `echo $HOME` |
| Set environment var | `export NAME="value"` |
| Find command location | `which command`, `command -v command` |
| HTTP requests | `curl https://url`, `curl -I https://url` |
| Download file | `wget https://url`, `wget -O filename https://url` |
| Create archive | `tar -cvf archive.tar dir/` |
| Extract archive | `tar -xvf archive.tar` |
| View scheduled jobs | `crontab -l` |
| Edit scheduled jobs | `crontab -e` |
| Create variable | `variable="value"` |
| Make script executable | `chmod +x script.sh` |
| Shutdown system | `shutdown -h now`, `shutdown -h +5`, `poweroff` |
| Reboot system | `shutdown -r now`, `reboot` |
| Cancel shutdown | `shutdown -c` |
| Halt system | `halt` |

---

## Key command explanations and aliases

### Pipe command
```bash
command1 | command2
# Send output of command1 as input to command2
```
Example:
```bash
ls | grep ".txt"
# List files, then filter for .txt files
```

### Output redirection
```bash
command > file.txt
# Write output to file (overwrite)

command >> file.txt
# Append output to file (do not overwrite)

command > output.txt 2> error.txt
# Redirect output and errors separately

command > file.txt 2>&1
# Redirect both output and errors to the same file
# 2>&1 means "send stream 2 (errors) to stream 1 (output)"
```

### Set environment variable
```bash
export MYVAR="value"
# Make variable available to current shell and child processes

unset MYVAR
# Remove the variable
```

### Find command location
```bash
which git
# Show the full path of a command

command -v git
# Similar to which, but more accurate in some shells
```

### Search in files
```bash
grep "text" file.txt
# Find lines containing "text"

grep -i "text" file.txt
# Case-insensitive search (-i flag)

grep -n "text" file.txt
# Show line numbers (-n flag)

grep -r "text" directory/
# Search recursively in directory (-r flag)

grep -v "text" file.txt
# Show lines that do NOT match (-v flag, invert match)
```

### Find files
```bash
find . -name "file.txt"
# Find by name in current directory and subdirectories

find . -type f
# Find all files (not directories)

find . -type d
# Find all directories (not files)

find . -size +10M
# Find files larger than 10 MB
```

### HTTP requests and downloads
```bash
curl https://example.com
# Make an HTTP request and display response

curl -I https://example.com
# Show headers only (-I flag)

curl -O https://example.com/file.zip
# Download file with original filename (-O flag)

wget https://example.com/file.zip
# Alternative download tool

wget -O filename.zip https://example.com/file.zip
# Download with custom filename (-O flag)
```

### Archive operations
```bash
tar -cvf archive.tar directory/
# Create tar archive (-c create, -v verbose, -f file)

tar -xvf archive.tar
# Extract tar archive (-x extract, -v verbose, -f file)

tar -czvf archive.tar.gz directory/
# Create compressed tar.gz (-z for gzip compression)

tar -xzvf archive.tar.gz
# Extract compressed tar.gz
```

### Cron - scheduled tasks
```bash
crontab -l
# List current user's cron jobs

crontab -e
# Edit cron jobs (opens in editor)

crontab -r
# Remove all cron jobs for current user
```

### Bash basics
```bash
variable="value"
echo "$variable"
# Create and use a variable

if [ -f "file.txt" ]; then
    echo "File exists"
fi
# If statement (check if file exists)

for item in one two three; do
    echo "$item"
done
# For loop (iterate through items)

#!/bin/bash
# Script shebang (tells system to use bash)

chmod +x script.sh
# Make script executable (+x adds execute permission)

./script.sh
# Run script from current directory
```

---

## 1. Basic filesystem commands

### `pwd`
```bash
pwd
```
Shows the current working directory.
- What is it? A command that prints your current location in the filesystem.
- Why do I need it? To know where you are before running file operations.
- What does it change? Nothing; it only displays information.
- How do I check the result? It prints a path like `/home/devops`.

### `ls`
```bash
ls
ls -la
```
Lists files and directories.
- `-l` = long format
- `-a` = include hidden files

### `cd`
```bash
cd /path/to/folder
cd ~
```
Changes the current working directory.
- Use `pwd` afterward to confirm the directory changed.

### `mkdir` / `touch`
```bash
mkdir demo
touch file.txt
```
Creates a folder and a blank file.
- Check with `ls -l` or `ls -la`.

### `cp` / `mv` / `rm`
```bash
cp source.txt dest.txt
mv old.txt new.txt
rm file.txt
```
Copies, renames, and removes files.
- Check with `ls` or `ls -l` after each action.

---

## 2. Files and directories

### `find`
```bash
find /etc -type f | head
```
Searches files in a directory tree.
- Use it to locate files by name, type, or path.
- Confirm by checking the returned paths.

### `cat`
```bash
cat /etc/os-release
```
Displays file contents.
- Good for reading config files and text files.
- Check output to confirm file content.

### `head` / `tail`
```bash
head /var/log/syslog
tail -n 20 /var/log/syslog
```
Views the start or end of a file.
- Useful for logs and text output.

---

## 3. Permissions and ownership

### `ls -l`
```bash
ls -l
```
Shows permissions, owner, group, size, and timestamps.
- Example: `-rw-r--r--` means read/write for owner, read-only for group and others.

### `chmod`
```bash
chmod 755 script.sh
chmod +x script.sh
```
Changes file permissions.
- What does it change? The access rights of the file.
- Check with `ls -l script.sh`.

### `chown`
```bash
sudo chown devops:devops file.txt
```
Changes the owner and group of a file.
- Check with `ls -l file.txt`.

### `whoami`
```bash
whoami
```
Shows the current user.
- Use this to understand which account is running commands.

---

## 4. Processes and services

### `ps`
```bash
ps aux
ps -ef | grep ssh
```
Shows running processes.
- Good for checking whether a process is active.
- Confirm with process list output.

### `top`
```bash
top
```
Displays live system process activity.
- Use it for CPU and memory view.
- Check the process list and resource usage.

### `systemctl status`
```bash
systemctl status ssh
```
Shows the current state of a service.
- Understand: `systemctl` talks to `systemd`; `status` asks for state; `ssh` is the service.
- Check result: active/inactive, enabled/disabled, and logs.

### `systemctl start / stop / restart / enable / disable`
```bash
sudo systemctl start ssh
sudo systemctl stop ssh
sudo systemctl restart ssh
sudo systemctl enable ssh
sudo systemctl disable ssh
```
Controls service behavior.
- Use `systemctl is-active ssh` to verify the service state.

### `systemctl is-active`
```bash
systemctl is-active ssh
```
Returns whether the service is active.
- Output is usually `active` or `inactive`.

---

## 5. Networking and SSH

### `ip addr`
```bash
ip addr
ip -br addr
```
Shows network interfaces and IP addresses.
- Check the interface name and assigned address.

### `ip route`
```bash
ip route
```
Displays the routing table.
- Useful for checking default gateway and network routes.

### `ping`
```bash
ping -c 4 8.8.8.8
```
Tests connectivity to a remote address.
- Confirm by checking packet loss or response time.

### `ss`
```bash
ss -tlnp | grep ':22'
```
Shows listening sockets and ports.
- `:22` indicates SSH is listening on port 22.
- Good verification command for SSH.

### `ssh`
```bash
ssh devops@192.168.187.129
```
Connects to a remote Linux machine over SSH.
- Check by seeing a shell prompt from the remote host.

### `ssh-keygen`
```bash
ssh-keygen
```
Generates a public/private key pair.
- Use `ls ~/.ssh` to check the generated key files.

### `ssh-copy-id`
```bash
ssh-copy-id devops@192.168.187.129
```
Copies the public key to a remote server to enable passwordless login.
- Verify by SSH without entering a password.

---

## 6. Disk, memory, and CPU

### `df -h`
```bash
df -h
```
Shows disk usage for mounted filesystems.
- Check free space and usage percentages.

### `du -sh`
```bash
du -sh .
```
Shows the size of the current directory.
- Useful to find large folders.

### `free -h`
```bash
free -h
```
Shows memory and swap usage.
- Check how much RAM is available and used.

### `lscpu`
```bash
lscpu
```
Displays CPU architecture and details.
- Check number of CPUs, model, and architecture.

### `nproc`
```bash
nproc
```
Displays the number of processing units available.
- Quick way to confirm CPU count.

### `lsblk`
```bash
lsblk
```
Shows block devices and partitions.
- Useful for understanding disks and LVM layout.

---

## 7. Logs and troubleshooting

### `journalctl`
```bash
journalctl -xe
journalctl -p 3 -b --no-pager
```
Reads system logs.
- `-p 3` = errors only
- `-b` = current boot
- Check the output to identify problems.

### `tail`
```bash
tail -f /var/log/syslog
```
Views the end of a log file and follows new output.
- Useful for real-time troubleshooting.

---

## 8. Package management

### `apt update`
```bash
sudo apt update
```
Refreshes package metadata from repositories.
- It does not install updates yet.
- Confirm with the list of packages and repository status.

### `apt list --upgradable`
```bash
apt list --upgradable
```
Shows which installed packages can be upgraded.
- Check the list to confirm pending updates.

### `apt upgrade`
```bash
sudo apt upgrade
```
Installs available upgrades.
- Verify by checking the command output and re-running `apt list --upgradable`.

### `dpkg -l`
```bash
dpkg -l
```
Lists installed packages.
- Useful when checking if a package is present.

### `apt-mark showmanual`
```bash
apt-mark showmanual
```
Shows packages installed manually.
- Helps understand what was added intentionally.

---

## 9. System basics and shell

### `echo`
```bash
echo "Hello"
```
Prints text to the terminal.
- It is a basic shell command used in scripts and troubleshooting.

### `||` conditional execution
```bash
lsb_release -a 2>/dev/null || cat /etc/os-release
```
Runs the second command only if the first fails.
- Good for fallback behavior in scripts.

### `sudo`
```bash
sudo apt update
```
Runs a command as root/admin.
- Verify by checking whether the command succeeds without permission errors.

---

## 10. OS information and hostname

### `cat /etc/os-release`
```bash
cat /etc/os-release
```
Shows the OS distribution information.
- Check result: prints the Ubuntu release details.

### `lsb_release -a`
```bash
lsb_release -a
```
Shows detailed Linux distribution information.
- Useful when `cat /etc/os-release` is not enough.

### `hostname`
```bash
hostname
```
Shows the current machine hostname.
- Verify by checking the printed host name.

### `hostnamectl`
```bash
hostnamectl
```
Shows system and hardware details such as hostname, OS, kernel, and architecture.
- Check result: output includes hostname and OS details.

---

## 11. CPU and shell basics

### `nproc`
```bash
nproc
```
Shows how many processing units are available.
- Check result: number of CPUs/cores visible to the system.

### `lscpu`
```bash
lscpu
```
Shows detailed CPU architecture and model information.

### `lscpu | grep -E 'Architecture|CPU\(s\)|Model name'`
```bash
lscpu | grep -E 'Architecture|CPU\(s\)|Model name'
```
Filters the CPU output to the most relevant lines.
- `|` sends output from one command to another.
- `grep` filters matching lines.

### `grep`
```bash
grep "text" file.txt
```
Searches for text in a file or command output.
- Check result: matching lines appear.

### `echo`
```bash
echo "Hello"
```
Prints text to the terminal.
- Good for testing shell behavior in scripts and commands.

### `||` fallback logic
```bash
lsb_release -a 2>/dev/null || cat /etc/os-release
```
Runs the second command only if the first one fails.
- `2>/dev/null` hides error output.

---

## 12. System service commands

### `systemctl --type=service --state=running`
```bash
systemctl --type=service --state=running
```
Shows currently running services.
- Check the result: running services are listed.

### `systemctl list-unit-files --type=service`
```bash
systemctl list-unit-files --type=service
```
Shows installed service unit files.
- Useful for checking service availability and configuration.

### `systemctl list-unit-files --type=service --state=disabled`
```bash
systemctl list-unit-files --type=service --state=disabled
```
Shows services that are installed but disabled.
- Verify by looking for `disabled` entries.

### `systemctl status <service-name>`
```bash
systemctl status ssh
```
Shows detailed state for a specific service.
- Check result: active, failed, enabled, or disabled status.

### `systemctl is-active ssh`
```bash
systemctl is-active ssh
```
Returns whether the service is active.
- Output is usually `active`.

### `systemctl start / stop / restart / enable / disable`
```bash
sudo systemctl start ssh
sudo systemctl stop ssh
sudo systemctl restart ssh
sudo systemctl enable ssh
sudo systemctl disable ssh
```
Changes the state of a service.
- Verify with `systemctl status ssh` or `systemctl is-active ssh`.

---

## 13. Boot, logs, and troubleshooting

### `systemd-analyze`
```bash
systemd-analyze
```
Shows system boot time information.
- Check result: startup duration and breakdown.

### `journalctl -p 3 -b --no-pager`
```bash
journalctl -p 3 -b --no-pager
```
Shows error-level log messages from the current boot.
- Useful for diagnosing problems.

### `tail -f /var/log/syslog`
```bash
tail -f /var/log/syslog
```
Displays the latest log entries and follows new ones.
- Good for live troubleshooting.

---

## 14. Packages and installed software

### `sudo apt update`
```bash
sudo apt update
```
Refreshes package metadata from Ubuntu repositories.
- It does not install new versions yet.

### `apt list --upgradable`
```bash
apt list --upgradable
```
Lists packages that can be upgraded.
- Check result: package names and new versions appear.

### `sudo apt upgrade`
```bash
sudo apt upgrade
```
Installs available upgrades.
- Verify by re-running `apt list --upgradable`.

### `apt list --installed`
```bash
apt list --installed
```
Lists installed packages.

### `dpkg -l`
```bash
dpkg -l
```
Shows installed packages in a more detailed package-manager view.

### `apt-mark showmanual`
```bash
apt-mark showmanual
```
Shows packages that were manually installed.

### `dpkg -l | grep nginx`
```bash
dpkg -l | grep nginx
```
Searches installed packages for a specific name.
- Good for checking whether a package is installed.

---

## 15. Pipes and redirection

### Pipes: `|`
```bash
command1 | command2
```
Sends the output of `command1` as input to `command2`.

Example:
```bash
ls | grep ".txt"
```
Lists files, then filters for names containing `.txt`.
- Useful for combining multiple commands.

### Output redirection: `>`
```bash
command > file.txt
```
Writes command output to a file (overwrites the file).

Example:
```bash
echo "Hello" > greeting.txt
```
Creates or overwrites `greeting.txt` with "Hello".
- Verify with `cat greeting.txt`.

### Append: `>>`
```bash
command >> file.txt
```
Appends command output to a file (does not overwrite).

Example:
```bash
echo "World" >> greeting.txt
```
Adds "World" to the end of `greeting.txt`.

### Input redirection: `<`
```bash
command < file.txt
```
Uses a file as input for a command.

Example:
```bash
sort < names.txt
```
Sorts the contents of `names.txt`.

### Error redirection: `2>`
```bash
command 2> error.txt
```
Redirects errors to a file.

Example:
```bash
ls /invalid 2> error.log
```
Captures the error in `error.log`.

### Both output and error: `2>&1`
```bash
command > output.txt 2>&1
```
Redirects both normal output and errors to the same file.

Example:
```bash
script.sh > results.txt 2>&1
```
Logs everything to `results.txt`.

---

## 16. Environment variables

### `printenv` / `env`
```bash
printenv
env
```
Shows all environment variables.
- Verify by looking for common variables like `PATH`, `HOME`, `USER`.

### `echo $VARIABLE`
```bash
echo $HOME
echo $PATH
echo $USER
```
Displays the value of an environment variable.

Example:
```bash
echo $PATH
```
Shows directories where the shell searches for commands.

### `export`
```bash
export MYVAR="value"
```
Creates or updates an environment variable.
- It is available for the current shell and child processes.
- Verify with `echo $MYVAR`.

### `unset`
```bash
unset MYVAR
```
Removes an environment variable.
- Verify by running `echo $MYVAR` (should be empty).

### Temporary environment variable
```bash
ENV_NAME="value" command
```
Runs a command with a temporary environment variable.

Example:
```bash
DEBUG=1 ./script.sh
```
Runs `script.sh` with `DEBUG=1` set.

---

## 17. PATH

### `echo $PATH`
```bash
echo $PATH
```
Shows directories where the shell looks for executable commands.
- The directories are separated by `:`.
- Verify by checking common paths like `/usr/bin`, `/usr/local/bin`.

### `which`
```bash
which python
which git
```
Shows the full path of a command.

Example:
```bash
which python
```
Outputs something like `/usr/bin/python3`.
- Useful to confirm which version of a command is installed.

### `command -v`
```bash
command -v git
```
Checks how a command is resolved in the shell.
- More accurate than `which` in some shells.

---

## 18. grep - searching files

### `grep`
```bash
grep "text" file.txt
```
Searches for text in a file and displays matching lines.
- What is it? A text search command.
- Why do I need it? To find specific content in files or command output.

Example:
```bash
grep "error" /var/log/syslog
```
Finds all lines containing "error" in the syslog.

### `grep -i` (case-insensitive)
```bash
grep -i "Error" file.txt
```
Searches ignoring case (matches "error", "Error", "ERROR").

### `grep -n` (line numbers)
```bash
grep -n "text" file.txt
```
Displays matching lines with their line numbers.

### `grep -r` (recursive search)
```bash
grep -r "function" ./src/
```
Searches recursively through directories.
- Useful for searching source code.

### `grep -v` (invert match)
```bash
grep -v "comment" file.txt
```
Shows lines that do NOT match.

Example:
```bash
ps aux | grep -v grep
```
Removes the grep command itself from process output.

---

## 19. find - searching for files

### `find`
```bash
find . -name "file.txt"
```
Searches for a file by name.
- What is it? A file search command.
- Why do I need it? To locate files in a directory tree.

Example:
```bash
find /home -name "*.log"
```
Finds all `.log` files in `/home`.

### `find -type f` (files only)
```bash
find . -type f
```
Searches for files (not directories).

### `find -type d` (directories only)
```bash
find . -type d
```
Searches for directories (not files).

### `find -size` (file size)
```bash
find . -type f -size +10M
```
Finds files larger than 10 MB.

### Combining conditions
```bash
find /var/log -name "*.log" -type f
```
Finds all `.log` files in `/var/log`.

---

## 20. curl - HTTP requests

### `curl`
```bash
curl https://example.com
```
Makes an HTTP request and displays the response.
- What is it? A command-line tool for HTTP/HTTPS requests.
- Why do I need it? To test APIs, download content, or check web servers.

Example:
```bash
curl https://httpbin.org/get
```
Fetches a test page and displays the response.

### `curl -I` (headers only)
```bash
curl -I https://example.com
```
Shows HTTP headers without the body.
- Useful for checking response codes and server info.

### `curl -O` (download file)
```bash
curl -O https://example.com/file.zip
```
Downloads a file with its original filename.

### `curl -L` (follow redirects)
```bash
curl -L https://short.url
```
Follows HTTP redirects.

---

## 21. wget - download files

### `wget`
```bash
wget https://example.com/file.zip
```
Downloads a file from the web.
- Similar to `curl -O`, but designed specifically for downloading.

### `wget -O`
```bash
wget -O myfile.zip https://example.com/file.zip
```
Downloads and saves with a custom filename.

---

## 22. tar - archive and compress

### `tar -cvf` (create archive)
```bash
tar -cvf archive.tar directory/
```
Creates a tar archive.
- `-c` = create, `-v` = verbose, `-f` = file

### `tar -xvf` (extract archive)
```bash
tar -xvf archive.tar
```
Extracts a tar archive.
- `-x` = extract, `-v` = verbose, `-f` = file

### `tar -czvf` (create compressed)
```bash
tar -czvf archive.tar.gz directory/
```
Creates a compressed `.tar.gz` archive.
- `-z` = compress with gzip

### `tar -xzvf` (extract compressed)
```bash
tar -xzvf archive.tar.gz
```
Extracts a compressed `.tar.gz` archive.

---

## 23. Cron - scheduled tasks

### `crontab -l`
```bash
crontab -l
```
Lists the current user's scheduled cron jobs.
- Verify by checking the output.

### `crontab -e`
```bash
crontab -e
```
Opens the cron editor to add or modify jobs.
- Adds the job to the crontab for the current user.

### `crontab -r`
```bash
crontab -r
```
Removes all cron jobs for the current user.
- Use with caution.

### Cron format
```
# ┌──────── minute (0-59)
# │ ┌────── hour (0-23)
# │ │ ┌──── day of month (1-31)
# │ │ │ ┌── month (1-12)
# │ │ │ │ ┌ day of week (0-7)
# │ │ │ │ │
# * * * * * command
```

Example:
```bash
0 2 * * * /path/to/script.sh
```
Runs the script every day at 2:00 AM.

---

## 24. Bash basics

### `echo`
```bash
echo "Hello"
```
Prints text to the terminal.
- Verify by seeing the output.

### Variables
```bash
variable="value"
echo "$variable"
```
Creates and uses a shell variable.
- Variables store values for later use.

### If statement
```bash
if [ condition ]; then
    command
fi
```
Runs a command only if the condition is true.

Example:
```bash
if [ -f "file.txt" ]; then
    echo "File exists"
fi
```

### For loop
```bash
for item in one two three; do
    echo "$item"
done
```
Repeats a command for each item.

### Bash script shebang
```bash
#!/bin/bash
echo "Script started"
```
The `#!/bin/bash` line tells the system to run the script as a bash script.

### Make script executable
```bash
chmod +x script.sh
```
Adds execute permission to a script.

### Run script
```bash
./script.sh
```
Executes the script from the current directory.

---

## 25. System shutdown and reboot

### `shutdown` command
```bash
shutdown [OPTIONS] [TIME] [MESSAGE]
```
Schedules the system to shutdown or reboot.
- What is it? A system control command that gracefully shuts down the machine.
- Why do I need it? To safely shut down the system with a grace period.
- What does it change? Prepares the system for shutdown.
- How do I verify it? Check system status or wait for shutdown.

### Shutdown immediately
```bash
shutdown -h now
# Shutdown immediately (-h = halt)
# "now" means execute immediately

shutdown -h 0
# Same as 'shutdown -h now'
```
Shuts down the system right away.

### Shutdown with delay (minutes)
```bash
shutdown -h +5
# Shutdown in 5 minutes

shutdown -h +10
# Shutdown in 10 minutes

shutdown -h +30
# Shutdown in 30 minutes
```
Gives users time to save work before shutdown.

### Shutdown at specific time
```bash
shutdown -h 14:30
# Shutdown at 2:30 PM today

shutdown -h 23:59
# Shutdown at 11:59 PM
```
Schedules shutdown for a specific time of day.

### Shutdown with warning message
```bash
shutdown -h +5 "System maintenance in 5 minutes"
# Shutdown in 5 minutes with custom message
# Connected users will see this message
```
Notifies logged-in users about the shutdown reason.

### Reboot system
```bash
shutdown -r now
# Reboot immediately (-r = reboot)

shutdown -r +5
# Reboot in 5 minutes

shutdown -r 15:00
# Reboot at 3:00 PM
```
Reboots instead of powering off.

### Cancel scheduled shutdown
```bash
shutdown -c
# Cancel any pending shutdown or reboot
```
Cancels a previously scheduled shutdown.
- Example: if you scheduled `shutdown -h +10` but want to cancel it
- Only works if shutdown hasn't started yet

### Quick shutdown alternatives
```bash
poweroff
# Power off immediately (no grace period)

reboot
# Reboot immediately (no grace period)

halt
# Halt the system (stop all processes)
```
These are faster but less safe than `shutdown` command.

### Shutdown with option combinations
```bash
shutdown -h +10 "Database backup in progress. Shutdown in 10 minutes"
# Combined: 10-minute delay + reboot message

shutdown -r now --no-wall
# Reboot now without wall message (don't notify users)
```
Useful for scripted or automated shutdowns.

### Shutdown for maintenance
```bash
shutdown -h +120
# Provide 2-hour warning for maintenance
# Users have time to close applications

shutdown -c
# Cancel if maintenance is postponed
```
Gives administrators and users advance notice.

### Important notes

**Permissions:**
- Most shutdown commands require `sudo` or root access
- Regular users cannot usually shutdown the system

**Examples:**
```bash
sudo shutdown -h now
# Need sudo to execute

sudo shutdown -r +5 "Patching system"
# Reboot in 5 minutes with message
```

**Best practices:**
- Always use `shutdown` for graceful shutdown, not `poweroff` or `halt`
- Give users warning time (e.g., +10 or +30 minutes)
- Use descriptive messages for why shutdown is happening
- Cancel if shutdown is no longer needed
- Check `who` command to see logged-in users before shutdown

**Check scheduled shutdown:**
```bash
shutdown -c
# If no shutdown is pending, you'll get a message
# If one is pending, it will show details and ask to confirm cancellation
```

---

> Keep adding new commands, examples, and notes to this file as you learn.

