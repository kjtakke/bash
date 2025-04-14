# Bash `watch` and `tail` 

| Command | Description |
|---------|-------------|
| `watch command` | Runs `command` repeatedly every 2 seconds and displays output. |
| `watch -n 5 command` | Runs `command` every 5 seconds. |
| `watch -d command` | Highlights differences between updates. |
| `watch -t command` | Runs `command` without displaying the header. |
| `watch -g command` | Exits when output changes. |
| `watch -b command` | Beeps when output changes. |
| `watch -c command` | Uses a coloured display. |
| `watch -x command args` | Allows running a command with arguments. |

## `tail` Commands

| Command | Description |
|---------|-------------|
| `tail file.txt` | Shows the last 10 lines of `file.txt`. |
| `tail -n 20 file.txt` | Shows the last 20 lines. |
| `tail -f file.txt` | Follows the file, displaying new lines as they are added. |
| `tail -F file.txt` | Similar to `-f`, but also handles file rotation. |
| `tail -q file1 file2` | Suppresses headers when following multiple files. |
| `tail -c 50 file.txt` | Shows the last 50 bytes of the file. |
| `tail -n +5 file.txt` | Starts displaying from line 5 onward. |
| `tail -f file.txt | grep "error"` | Follows the file and filters for "error". |

## Combined Usage

| Command | Description |
|---------|-------------|
| `watch -n 2 tail -n 20 file.txt` | Displays the last 20 lines every 2 seconds. |
| `watch -d tail -f file.txt` | Highlights changes in a continuously updated file. |
| `tail -f /var/log/syslog & watch -d "ls -l /var/log/syslog"` | Monitors log updates while tracking file changes. |
