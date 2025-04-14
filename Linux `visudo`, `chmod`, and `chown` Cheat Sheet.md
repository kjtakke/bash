### Linux `visudo`, `chmod`, and `chown` Cheat Sheet

#### `visudo` Commands
| Command | Description |
|---------|-------------|
| `sudo visudo` | Opens the sudoers file for safe editing. |
| `sudo visudo -f /etc/sudoers.d/custom` | Edits a custom sudoers file instead of `/etc/sudoers`. |
| `%sudo ALL=(ALL) ALL` | Grants all users in the `sudo` group full root privileges. |
| `username ALL=(ALL) ALL` | Grants full sudo privileges to a specific user. |
| `username ALL=(ALL) NOPASSWD:ALL` | Allows a user to run sudo commands without a password. |
| `username ALL=(ALL) /path/to/command` | Restricts sudo access to a specific command. |
| `%groupname ALL=(ALL) ALL` | Grants sudo privileges to a specific group. |
| `Defaults:username !requiretty` | Allows a user to execute sudo commands without a TTY session. |
| `Defaults timestamp_timeout=10` | Sets sudo timeout (in minutes) before requiring a password again. |
| `Defaults insults` | Enables humorous responses for incorrect passwords. |
| `sudo -l` | Lists the sudo privileges of the current user. |

---

#### `chmod` Permissions
| Command | Description |
|---------|-------------|
| `chmod 777 file` | Full permissions to everyone (`rwxrwxrwx`). |
| `chmod 755 file` | Owner full (`rwx`), group & others read/execute (`r-xr-xr-x`). |
| `chmod 644 file` | Owner read/write (`rw-`), group & others read (`r--r--r--`). |
| `chmod 600 file` | Owner read/write (`rw-`), no access for group & others. |
| `chmod 400 file` | Owner read-only (`r--`), no access for group & others. |
| `chmod 000 file` | No permissions for anyone. |
| `chmod +x file` | Adds execute (`x`) permission to a file. |
| `chmod -x file` | Removes execute (`x`) permission from a file. |
| `chmod -R 755 folder` | Recursively sets permissions on a folder and its contents. |

**Symbolic Mode Examples**
| Command | Description |
|---------|-------------|
| `chmod u+x file` | Adds execute (`x`) permission for the owner. |
| `chmod g-w file` | Removes write (`w`) permission from the group. |
| `chmod o+r file` | Adds read (`r`) permission for others. |
| `chmod u=rwx,g=rx,o=r file` | Sets specific permissions for owner, group, and others. |

---

#### `chown` Commands
| Command | Description |
|---------|-------------|
| `chown user file` | Changes ownership of a file to `user`. |
| `chown user:group file` | Changes both owner and group of a file. |
| `chown :group file` | Changes the group ownership of a file. |
| `chown -R user:group folder` | Recursively changes ownership of a folder and its contents. |
| `chown --from=current_user new_user file` | Changes ownership only if the current owner matches. |
| `chown --reference=ref_file target_file` | Changes ownership to match a reference file. |