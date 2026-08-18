# Ubuntu / Linux Learning Commands

> Personal command reference for learning Ubuntu/Linux.  
> VM: Ubuntu Server 26.04 LTS on VMware on Apple M2 (ARM64).

---

## 1. OS Information

### Show Ubuntu/OS information

```bash
cat /etc/os-release
```

Shows the contents of the OS release information file.

```bash
lsb_release -a
```

Shows Linux distribution information.

### Show hostname

```bash
hostname
```

Shows the system hostname.

```bash
hostnamectl
```

Shows hostname, OS, kernel, architecture, virtualization, and hardware information.

---

## 2. CPU

### Show number of available CPUs

```bash
nproc
```

### Show CPU information

```bash
lscpu
```

### Show selected CPU information

```bash
lscpu | grep -E 'Architecture|CPU\(s\)|Model name'
```

### Pipe `|`

```bash
command1 | command2
```

Sends the output of `command1` to `command2`.

### `grep`

```bash
grep "text"
```

Searches/filter lines containing matching text.

---

## 3. RAM and Swap

### Show RAM and swap usage

```bash
free -h
```

- `free` = memory information
- `-h` = human-readable format

---

## 4. Disk / Storage

### Show filesystem disk usage

```bash
df -h
```

Shows mounted filesystems, their size, used space, available space, and usage percentage.

### Check the root filesystem

```bash
df -h /
```

Shows disk usage for `/`.

### Show disks, partitions, and LVM

```bash
lsblk
```

Shows block devices, partitions, logical volumes, sizes, and mount points.

### Current VM storage structure

```text
nvme0n1              30G   <- VMware virtual disk
├── nvme0n1p1         1G   <- /boot/efi
├── nvme0n1p2         2G   <- /boot
└── nvme0n1p3        26.9G <- LVM partition
    └── ubuntu--vg-ubuntu--lv
                       13.5G <- / filesystem
```

### LVM basics

```text
Disk
  ↓
Partition
  ↓
LVM Volume Group
  ↓
Logical Volume
  ↓
Filesystem
  ↓
/
```

In this VM:

- VMware disk = 30 GB
- LVM partition = 26.9 GB
- Root logical volume = 13.5 GB
- The remaining LVM space is currently not assigned to `/`.

---

## 5. Network

### Show network interfaces and IP addresses

```bash
ip -br addr
```

`-br` = brief output.

Example:

```text
lo       UNKNOWN  127.0.0.1/8
enp2s0   UP       192.168.187.129/24
```

- `lo` = loopback interface
- `enp2s0` = VM network interface
- `192.168.187.129` = VM's IP address

### Test Internet connectivity

```bash
ping -c 4 8.8.8.8
```

- `ping` = test network connectivity
- `-c 4` = send 4 packets
- `8.8.8.8` = destination

Useful result:

```text
4 packets transmitted, 4 received, 0% packet loss
```

means all 4 packets were received.

### `ens33` / `eth0`

```bash
ens33
eth0
```

These are interface names, not commands. Typing them directly gives:

```text
command not found
```

Use:

```bash
ip -br addr
```

to find the actual interface name.

---

## 6. SSH

### Check SSH service

```bash
systemctl status ssh --no-pager
```

Shows detailed SSH service status.

### Check if SSH is active

```bash
systemctl is-active ssh
```

Expected result:

```text
active
```

### Check port 22

```bash
ss -tlnp | grep ':22'
```

- `ss` = socket/network information
- `-t` = TCP
- `-l` = listening
- `-n` = numeric output
- `-p` = process information
- `grep ':22'` = show port 22

### SSH connection

```bash
ssh devops@192.168.187.129
```

Connects to the VM using the `devops` user.

### Change current user's password

```bash
passwd
```

The new password is also used for SSH when SSH password authentication is enabled.

---

## 7. Services with `systemctl`

### Show currently running services

```bash
systemctl --type=service --state=running
```

### Show all installed service unit files

```bash
systemctl list-unit-files --type=service
```

Common states:

- `enabled` = starts automatically at boot
- `disabled` = installed but not automatically started
- `static` = normally started as a dependency/when needed
- `masked` = prevented from starting

### Show disabled services

```bash
systemctl list-unit-files --type=service --state=disabled
```

### Check one service

```bash
systemctl status <service-name>
```

Example:

```bash
systemctl status ssh
```

### Common service commands

```bash
sudo systemctl start <service>
sudo systemctl stop <service>
sudo systemctl restart <service>
sudo systemctl enable <service>
sudo systemctl disable <service>
```

---

## 8. Boot Time

### Show boot time

```bash
systemd-analyze
```

Example:

```text
Startup finished in ...
```

Shows kernel, initrd, and userspace startup times.

---

## 9. System Logs

### Show error-level messages from current boot

```bash
journalctl -p 3 -b --no-pager
```

- `journalctl` = read system logs
- `-p 3` = priority 3 (errors)
- `-b` = current boot
- `--no-pager` = print directly

---

## 10. Packages / Applications

### Update package information

```bash
sudo apt update
```

Downloads the latest package information from configured Ubuntu repositories.

**It does not install the updates.**

### Show packages that can be upgraded

```bash
apt list --upgradable
```

### Install available updates

```bash
sudo apt upgrade
```

### Show installed packages

```bash
apt list --installed
```

### Another way to list installed packages

```bash
dpkg -l
```

or:

```bash
dpkg --get-selections
```

### Show manually installed packages

```bash
apt-mark showmanual
```

Useful for finding packages that were manually installed rather than automatically installed as dependencies.

### Search installed packages

```bash
apt list --installed | grep <name>
```

or:

```bash
dpkg -l | grep <name>
```

Example:

```bash
apt list --installed | grep nginx
```

---

## 11. Shell Basics

### Print text

```bash
echo "Hello"
```

### Redirect error output

```bash
command 2>/dev/null
```

`2>` redirects standard error.

`/dev/null` discards the output.

### Run another command if the first fails

```bash
command1 || command2
```

`||` means:

> Run `command2` only if `command1` fails.

Example:

```bash
lsb_release -a 2>/dev/null || cat /etc/os-release
```

Try `lsb_release` first; if it fails, use `/etc/os-release`.

---

## 12. Linux Filesystem Basics

Linux has one main filesystem tree:

```text
/
├── boot
├── etc
├── home
├── root
├── usr
├── var
├── tmp
├── dev
├── proc
├── sys
└── run
```

Important directories:

| Directory | Purpose |
|---|---|
| `/` | Root of the filesystem |
| `/home` | Normal users' home directories |
| `/root` | Root user's home directory |
| `/etc` | System configuration |
| `/var` | Logs, caches, and changing data |
| `/usr` | Programs and libraries |
| `/boot` | Boot files |
| `/boot/efi` | UEFI boot files |
| `/tmp` | Temporary files |
| `/dev` | Device files |
| `/proc` | Process/kernel information |
| `/sys` | Kernel/hardware information |
| `/run` | Runtime information |

User home directory:

```text
/home/devops
```

---

## 13. `sudo`

```bash
sudo <command>
```

Runs a command with administrator/root privileges.

Example:

```bash
sudo apt update
```

---

## 14. Useful Quick Reference

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
| Running services | `systemctl --type=service --state=running` |
| All services | `systemctl list-unit-files --type=service` |
| Service status | `systemctl status <service>` |
| SSH status | `systemctl status ssh` |
| Listening ports | `ss -tlnp` |
| Boot time | `systemd-analyze` |
| System errors | `journalctl -p 3 -b --no-pager` |
| Update package lists | `sudo apt update` |
| Available updates | `apt list --upgradable` |
| Install updates | `sudo apt upgrade` |
| Installed packages | `apt list --installed` |
| Manual packages | `apt-mark showmanual` |
| Change password | `passwd` |

---

## Current VM Summary

```text
OS:          Ubuntu 26.04 LTS
Architecture: ARM64 / aarch64
Virtualization: VMware
CPU:         2 vCPUs
RAM:         ~2.6 GiB
Disk:        30 GB
Root LV:     ~13.5 GB
Root usage:  ~45%
Network:     enp2s0
IP:          192.168.187.129
SSH:         Active
Hostname:    d-ops
```

> Keep adding new commands, examples, and notes to this file as you learn.
