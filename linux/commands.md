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

> Keep adding new commands, examples, and notes to this file as you learn.

