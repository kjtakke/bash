# Sudo

| Command | Description |
|---------|-------------|
| `sudo <command>` | Run a command as superuser (root). |
| `sudo -i` | Open a root shell with root's environment. |
| `sudo -s` | Open a root shell with the user's environment. |
| `sudo -u <user> <command>` | Run a command as a specific user. |
| `sudo -k` | Invalidate the cached credentials (force re-authentication). |
| `sudo -v` | Refresh sudo authentication timeout without running a command. |
| `sudo -l` | List available sudo privileges for the current user. |
| `sudo !!` | Re-run the last command with sudo. |
| `sudo -n <command>` | Run a command without prompting for a password (fails if authentication is needed). |
| `sudo -E <command>` | Preserve the user’s environment when running a command. |
| `sudo -H <command>` | Set `$HOME` to the target user's home directory. |
| `sudo -b <command>` | Run a command in the background. |
| `sudo EDITOR=nano visudo` | Edit the sudoers file using nano (replace `nano` with preferred editor). |
| `sudo shutdown -h now` | Shutdown the system immediately. |
| `sudo shutdown -r now` | Restart the system immediately. |
| `sudo reboot` | Reboot the system. |
| `sudo apt update && sudo apt upgrade -y` | Update and upgrade packages (Debian-based systems). |
| `sudo yum update` | Update packages (RHEL-based systems). |
| `sudo dnf update` | Update packages (Fedora-based systems). |
| `sudo pacman -Syu` | Update packages (Arch Linux). |
| `sudo chown user:group <file>` | Change ownership of a file or directory. |
| `sudo chmod 755 <file>` | Change file permissions. |
| `sudo systemctl restart <service>` | Restart a system service. |
| `sudo systemctl stop <service>` | Stop a system service. |
| `sudo systemctl start <service>` | Start a system service. |
| `sudo systemctl enable <service>` | Enable a service to start on boot. |
| `sudo systemctl disable <service>` | Disable a service from starting on boot. |
| `sudo netstat -tulpn` | Show all listening ports and their associated processes. |
| `sudo journalctl -xe` | View system logs for troubleshooting. |
| `sudo dmesg` | View kernel log messages. |
| `sudo mount /dev/sdX /mnt` | Mount a device manually. |
| `sudo umount /mnt` | Unmount a mounted device. |
| `sudo fdisk -l` | List disk partitions. |
| `sudo kill -9 <PID>` | Force kill a process by its process ID. |
| `sudo pkill <process>` | Kill all processes with the specified name. |
| `sudo useradd <username>` | Create a new user. |
| `sudo passwd <username>` | Set or change a user's password. |
| `sudo usermod -aG <group> <username>` | Add a user to a group. |
| `sudo visudo` | Edit the sudoers file safely. |
| `sudo nano /etc/sudoers` | Edit the sudoers file (dangerous if incorrect syntax is used). |

This cheat sheet provides a quick reference for common `sudo` commands, covering administration, package management, user management, and system maintenance.