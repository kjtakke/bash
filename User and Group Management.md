# User and Group Management

## User Management

| Command | Description |
|---------|-------------|
| `whoami` | Show current username. |
| `id` | Display user ID (UID) and group ID (GID). |
| `who` | Show who is logged in. |
| `w` | Display active user sessions. |
| `users` | List logged-in users. |
| `finger <username>` | Show information about a user (may need installation). |
| `sudo useradd -m <username>` | Create a new user with a home directory. |
| `sudo passwd <username>` | Set or change a user’s password. |
| `sudo userdel -r <username>` | Delete a user and their home directory. |
| `sudo usermod -l <newname> <oldname>` | Rename a user. |
| `sudo usermod -aG <group> <username>` | Add a user to a group (append). |
| `sudo usermod -g <group> <username>` | Change a user’s primary group. |
| `sudo usermod -d /new/home <username>` | Change a user’s home directory. |
| `sudo usermod -s /bin/bash <username>` | Change a user’s default shell. |

## Group Management

| Command | Description |
|---------|-------------|
| `groups <username>` | Show groups a user belongs to. |
| `getent group <groupname>` | Show group details. |
| `sudo groupadd <groupname>` | Create a new group. |
| `sudo groupdel <groupname>` | Delete a group. |
| `sudo gpasswd -a <username> <group>` | Add a user to a group. |
| `sudo gpasswd -d <username> <group>` | Remove a user from a group. |
| `sudo usermod -aG <group> <username>` | Add a user to a secondary group. |
| `sudo usermod -g <group> <username>` | Change a user’s primary group. |

## Permission Management

| Command | Description |
|---------|-------------|
| `ls -l` | View file permissions. |
| `chmod u+x file` | Add execute permission to the user (owner). |
| `chmod g-w file` | Remove write permission for the group. |
| `chmod o+r file` | Add read permission for others. |
| `chmod 755 file` | Set permissions: owner (rwx), group (r-x), others (r-x). |
| `chown user file` | Change file owner. |
| `chown user:group file` | Change file owner and group. |
| `chgrp group file` | Change file group ownership. |

## Switching and Running as Another User

| Command | Description |
|---------|-------------|
| `su - <username>` | Switch to another user (requires password). |
| `sudo -i` | Switch to root user. |
| `sudo -u <username> command` | Run a command as another user. |

## Viewing and Managing Logged-in Users

| Command | Description |
|---------|-------------|
| `who` | Show logged-in users. |
| `w` | Display active user sessions. |
| `whoami` | Show current username. |
| `last` | Show login history. |
| `pkill -u <username>` | Kill all processes of a user. |
| `sudo kill -9 <PID>` | Kill a specific process. |
| `sudo pkill -9 -u <username>` | Forcefully log out a user. |

## Sudo Privileges Management

| Command | Description |
|---------|-------------|
| `sudo visudo` | Edit sudoers file safely. |
| `<username> ALL=(ALL:ALL) ALL` | Give full sudo privileges. |
| `<username> ALL=(ALL) NOPASSWD: ALL` | Allow sudo without a password. |
| `%<groupname> ALL=(ALL) ALL` | Give a group sudo access. |

## User Account Locking and Expiration

| Command | Description |
|---------|-------------|
| `sudo passwd -l <username>` | Lock a user account. |
| `sudo passwd -u <username>` | Unlock a user account. |
| `sudo chage -l <username>` | Show password aging information. |
| `sudo chage -E YYYY-MM-DD <username>` | Set account expiration date. |
| `sudo chage -M 30 <username>` | Force password change every 30 days. |

This cheat sheet covers essential commands for managing users, groups, permissions, and access control in Linux.