# Linux for DevOps - Complete Guide

## Table of Contents
1. [Introduction to Linux](#introduction-to-linux)
2. [Linux File System](#linux-file-system)
3. [Essential Linux Commands](#essential-linux-commands)
4. [File and Directory Operations](#file-and-directory-operations)
5. [Text Processing](#text-processing)
6. [Process Management](#process-management)
7. [System Monitoring](#system-monitoring)
8. [Network Commands](#network-commands)
9. [File Permissions and Ownership](#file-permissions-and-ownership)
10. [Package Management](#package-management)
11. [System Services](#system-services)
12. [Shell Scripting Basics](#shell-scripting-basics)
13. [Environment Variables](#environment-variables)
14. [Log Management](#log-management)
15. [DevOps Specific Tools](#devops-specific-tools)

## Introduction to Linux

### What is Linux?
- Open-source operating system kernel
- Multi-user, multi-tasking system
- Foundation for many server environments
- Essential for DevOps professionals

### Why Linux for DevOps?
- Most servers run on Linux
- Powerful command-line interface
- Automation-friendly
- Excellent for containerization (Docker, Kubernetes)
- Cost-effective and stable

### Popular Linux Distributions
- **Ubuntu** - User-friendly, good for beginners
- **CentOS/RHEL** - Enterprise-focused
- **Amazon Linux** - Optimized for AWS
- **Alpine** - Lightweight, popular for containers
- **Debian** - Stable and reliable

## Linux File System

### Directory Structure
```
/                   # Root directory
├── bin/           # Essential user binaries
├── boot/          # Boot loader files
├── dev/           # Device files
├── etc/           # Configuration files
├── home/          # User home directories
├── lib/           # Essential shared libraries
├── opt/           # Optional software
├── proc/          # Process information
├── root/          # Root user home directory
├── sbin/          # System binaries
├── tmp/           # Temporary files
├── usr/           # User utilities and applications
└── var/           # Variable data (logs, databases)
```

### Important Directories for DevOps
- `/etc/` - System configuration files
- `/var/log/` - System and application logs
- `/home/` - User directories
- `/opt/` - Third-party applications
- `/tmp/` - Temporary files
- `/proc/` - System information

## Essential Linux Commands

### Navigation Commands
```bash
pwd                 # Print working directory
ls                  # List files and directories
ls -la              # List with details including hidden files
cd /path/to/dir     # Change directory
cd ..               # Go to parent directory
cd ~                # Go to home directory
cd -                # Go to previous directory
```

### File and Directory Operations

#### Creating Files and Directories
```bash
touch filename.txt          # Create empty file
mkdir dirname               # Create directory
mkdir -p dir1/dir2/dir3    # Create nested directories
```

#### Copying and Moving
```bash
cp source destination       # Copy file
cp -r source destination   # Copy directory recursively
mv source destination      # Move/rename file or directory
```

#### Removing Files and Directories
```bash
rm filename                # Remove file
rm -f filename            # Force remove file
rm -r dirname             # Remove directory recursively
rm -rf dirname            # Force remove directory recursively
```

#### Viewing File Contents
```bash
cat filename              # Display entire file content
less filename             # View file page by page
head filename             # Show first 10 lines
head -n 20 filename       # Show first 20 lines
tail filename             # Show last 10 lines
tail -f filename          # Follow file changes (useful for logs)
```

## Text Processing

### grep - Search Text
```bash
grep "pattern" filename           # Search for pattern in file
grep -i "pattern" filename        # Case-insensitive search
grep -r "pattern" directory       # Recursive search in directory
grep -v "pattern" filename        # Invert match (exclude pattern)
grep -n "pattern" filename        # Show line numbers
```

### sed - Stream Editor
```bash
sed 's/old/new/' filename        # Replace first occurrence
sed 's/old/new/g' filename       # Replace all occurrences
sed -i 's/old/new/g' filename    # Edit file in-place
```

### awk - Text Processing
```bash
awk '{print $1}' filename        # Print first column
awk -F: '{print $1}' /etc/passwd # Use custom delimiter
```

### Other Text Tools
```bash
sort filename                    # Sort lines
uniq filename                   # Remove duplicate lines
wc filename                     # Word, line, character count
wc -l filename                  # Line count only
```

## Process Management

### Viewing Processes
```bash
ps                              # Show current user processes
ps aux                          # Show all processes
ps aux | grep processname       # Find specific process
top                            # Real-time process viewer
htop                           # Enhanced process viewer
```

### Managing Processes
```bash
kill PID                       # Terminate process by PID
kill -9 PID                    # Force kill process
killall processname            # Kill all processes by name
nohup command &                # Run command in background
jobs                          # Show background jobs
fg                            # Bring job to foreground
bg                            # Send job to background
```

## System Monitoring

### Disk Usage
```bash
df -h                         # Show disk space usage
du -h                         # Show directory space usage
du -sh *                      # Show size of each item in current directory
```

### Memory Usage
```bash
free -h                       # Show memory usage
cat /proc/meminfo             # Detailed memory information
```

### CPU Information
```bash
lscpu                         # CPU information
cat /proc/cpuinfo             # Detailed CPU information
uptime                        # System uptime and load average
```

### System Information
```bash
uname -a                      # System information
whoami                        # Current username
id                           # User and group IDs
w                            # Who is logged in
last                         # Last login history
```

## Network Commands

### Network Configuration
```bash
ip addr show                  # Show IP addresses
ip route show                 # Show routing table
netstat -tuln                # Show listening ports
ss -tuln                     # Modern alternative to netstat
```

### Network Testing
```bash
ping hostname                 # Test connectivity
curl -I http://example.com    # Check HTTP headers
wget http://example.com/file  # Download files
telnet hostname port          # Test port connectivity
```

## File Permissions and Ownership

### Understanding Permissions
```bash
# Permission format: rwxrwxrwx
# r = read (4), w = write (2), x = execute (1)
# First trio: owner, second: group, third: others

ls -l filename                # View permissions
```

### Changing Permissions
```bash
chmod 755 filename            # rwxr-xr-x
chmod +x filename             # Add execute permission
chmod -w filename             # Remove write permission
chmod u+x filename            # Add execute for user only
```

### Changing Ownership
```bash
chown user:group filename     # Change owner and group
chown user filename           # Change owner only
chgrp group filename          # Change group only
sudo chown root:root filename # Change to root (requires sudo)
```

## Package Management

### Ubuntu/Debian (apt)
```bash
OBOBOBsudo apt update               # Update package list
sudo apt upgrade              # Upgrade installed packages
sudo apt install package     # Install package
sudo apt remove package      # Remove package
sudo apt search package      # Search for package
```
OBOBOB
### CentOS/RHEL (yum/dnf)
```bash
OBOBOBsudo yum update               # Update system
sudo yum install package     # Install package
sudo yum remove package      # Remove package
OBOBOBsudo yum search package      # Search for package
```

OBOBOB## System Services

### systemd (Modern Linux)
```bash
sudo systemctl start service     # Start service
OBOBOBsudo systemctl stop service      # Stop service
sudo systemctl restart service   # Restart service
sudo systemctl enable service    # Enable at boot
sudo systemctl disable service   # Disable at boot
sudo systemctl status service    # Check service status
systemctl list-units            # List all services
```

### Service Logs
```bash
sudo journalctl -u service       # View service logs
sudo journalctl -f              # Follow all logs
sudo journalctl --since "1 hour ago"  # Recent logs
```

## Shell Scripting Basics

### Script Structure
```bash
#!/bin/bash
# This is a comment

# Variables
OBOBOBNAME="DevOps"
OBOBOBecho "Hello, $NAME"

OBOBOB# User input
read -p "Enter your name: " USER_NAME
echo "Hello, $USER_NAME"
OBOBOB
# Conditional statements
OBOBOBif [ "$USER_NAME" = "admin" ]; then
    echo "Admin user detected"
else
    echo "Regular user"
OBOBOBfi

# Loops
for i in {1..5}; do
OBOBOB    echo "Count: $i"
done

# Functions
function greet() {
    echo "Hello, $1"
}
greet "World"
```

### Making Scripts Executable
```bash
chmod +x script.sh            # Make executable
./script.sh                   # Run script
```

## Environment Variables

### Common Environment Variables
```bash
echo $HOME                    # User home directory
echo $PATH                    # Executable search path
echo $USER                    # Current username
echo $PWD                     # Current directory
```

### Setting Environment Variables
```bash
export VAR_NAME="value"       # Set for current session
echo 'export VAR_NAME="value"' >> ~/.bashrc  # Set permanently
source ~/.bashrc              # Reload bash configuration
```

## Log Management

### Important Log Locations
```bash
/var/log/syslog              # System logs
/var/log/auth.log            # Authentication logs
/var/log/nginx/              # Web server logs
/var/log/apache2/            # Apache logs
/var/log/mysql/              # MySQL logs
```

### Viewing Logs
```bash
tail -f /var/log/syslog      # Follow system logs
grep "ERROR" /var/log/app.log # Search for errors
zcat /var/log/app.log.gz     # View compressed logs
```

### Log Rotation
```bash
sudo logrotate -f /etc/logrotate.conf  # Force log rotation
```

## DevOps Specific Tools

### Git Commands
```bash
git clone repository         # Clone repository
git status                   # Check repository status
git add .                    # Stage all changes
git commit -m "message"      # Commit changes
git push origin branch       # Push to remote
git pull                     # Pull latest changes
```

### Docker Commands
```bash
docker ps                    # List running containers
docker images                # List images
docker run image            # Run container
docker exec -it container bash  # Access container shell
docker logs container       # View container logs
```

### SSH and SCP
```bash
ssh user@hostname           # Connect to remote server
ssh-keygen -t rsa          # Generate SSH key pair
scp file user@host:/path   # Copy file to remote server
scp user@host:/path/file . # Copy file from remote server
```

## Best Practices for DevOps

### Security
- Use SSH keys instead of passwords
- Regularly update systems and packages
- Implement proper file permissions
- Use sudo instead of root login
- Monitor system logs regularly

### Automation
- Write shell scripts for repetitive tasks
- Use configuration management tools
- Implement log rotation
- Set up monitoring and alerting
- Use version control for configurations

### Performance
- Monitor system resources regularly
- Clean up temporary files
- Optimize log retention policies
- Use efficient commands and tools
- Implement proper backup strategies

## Useful One-Liners

```bash
# Find large files
find / -type f -size +100M 2>/dev/null

# Monitor real-time network connections
watch -n 1 'netstat -tuln'

# Check disk I/O
iostat -x 1

# Find files modified in last 24 hours
find /path -type f -mtime -1

# Count lines of code
find . -name "*.py" | xargs wc -l

# Check memory usage by process
ps aux --sort=-%mem | head

# Find and kill process by name
pkill -f "process_name"

# Archive and compress directory
tar -czf backup.tar.gz /path/to/directory

# Extract compressed archive
tar -xzf backup.tar.gz

# Check listening ports
lsof -i -P -n | grep LISTEN
```

## Common Troubleshooting Commands

```bash
# Check system resources
top
htop
free -h
df -h

# Network troubleshooting
ping google.com
nslookup domain.com
traceroute google.com

# Service troubleshooting
systemctl status service
journalctl -u service
sudo systemctl restart service

# File system issues
fsck /dev/sdX1
mount | grep /dev/sdX1

# Process issues
ps aux | grep process
lsof | grep filename
strace -p PID
```

---

## Quick Reference Card

| Command | Description |
|---------|-------------|
| `ls -la` | List all files with details |
| `cd ~` | Go to home directory |
| `pwd` | Show current directory |
| `cp -r` | Copy directory recursively |
| `rm -rf` | Remove directory forcefully |
| `chmod 755` | Set file permissions |
| `sudo su -` | Switch to root user |
| `ps aux` | Show all processes |
| `kill -9` | Force kill process |
| `df -h` | Show disk usage |
| `free -h` | Show memory usage |
| `tail -f` | Follow file changes |
| `grep -r` | Recursive search |
| `find /` | Search files system-wide |
| `which cmd` | Find command location |

---

*Remember: Practice these commands in a safe environment before using them in production systems!*
