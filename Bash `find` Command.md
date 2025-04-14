# Bash `find` Command 

| Command | Description |
|---------|-------------|
| `find /path -name "filename"` | Find a file by name (case-sensitive). |
| `find /path -iname "filename"` | Find a file by name (case-insensitive). |
| `find /path -type f` | Find all files in a directory. |
| `find /path -type d` | Find all directories in a directory. |
| `find /path -name "*.txt"` | Find all `.txt` files in a directory. |
| `find /path -maxdepth 1 -name "*.txt"` | Find `.txt` files in the specified directory only (no subdirectories). |
| `find /path -mindepth 2 -name "*.txt"` | Find `.txt` files in subdirectories only (ignore the root of the path). |
| `find /path -type f -empty` | Find empty files. |
| `find /path -type d -empty` | Find empty directories. |
| `find /path -size +10M` | Find files larger than 10MB. |
| `find /path -size -500k` | Find files smaller than 500KB. |
| `find /path -size 50M` | Find files exactly 50MB in size. |
| `find /path -mtime -7` | Find files modified in the last 7 days. |
| `find /path -mtime +30` | Find files modified more than 30 days ago. |
| `find /path -mmin -60` | Find files modified in the last 60 minutes. |
| `find /path -mmin +1440` | Find files modified more than 24 hours ago. |
| `find /path -atime -1` | Find files accessed in the last 24 hours. |
| `find /path -atime +10` | Find files not accessed in the last 10 days. |
| `find /path -cmin -30` | Find files changed in the last 30 minutes. |
| `find /path -ctime +5` | Find files changed more than 5 days ago. |
| `find /path -user username` | Find files owned by a specific user. |
| `find /path -group groupname` | Find files belonging to a specific group. |
| `find /path -perm 755` | Find files with exact `755` permissions. |
| `find /path -perm -4000` | Find files with the SUID bit set. |
| `find /path -perm -2000` | Find files with the SGID bit set. |
| `find /path -perm -1000` | Find files with the sticky bit set. |
| `find /path -executable` | Find executable files. |
| `find /path -name "*.log" -delete` | Find and delete all `.log` files. **Use with caution!** |
| `find /path -type d -name "backup" -exec rm -r {} \;` | Find and delete directories named "backup". **Use with caution!** |
| `find /path -type f -exec chmod 644 {} \;` | Change permissions of all files to `644`. |
| `find /path -type d -exec chmod 755 {} \;` | Change permissions of all directories to `755`. |
| `find /path -name "*.log" -exec mv {} /backup/ \;` | Move all `.log` files to `/backup/`. |
| `find /path -type f -print0 | xargs -0 rm` | Delete all files found (efficient and safe). |
| `find /path -name "*.txt" -o -name "*.log"` | Find files with `.txt` OR `.log` extensions. |
| `find /path $begin:math:text$ -name "*.jpg" -o -name "*.png" $end:math:text$ -delete` | Find and delete image files (`.jpg` or `.png`). **Use with caution!** |
| `find /path -type f ! -name "*.txt"` | Find all files except `.txt` files. |
| `find /path -type f -not -name "*.txt"` | Another way to exclude `.txt` files. |
| `find /path -newer file.txt` | Find files modified more recently than `file.txt`. |
| `find /path -anewer file.txt` | Find files accessed more recently than `file.txt`. |
| `find /path -cnewer file.txt` | Find files changed more recently than `file.txt`. |
| `find /path -type f -exec grep "search_text" {} \;` | Find files containing `search_text`. |
| `find /path -type f -exec grep -l "search_text" {} \;` | Find files containing `search_text` (show filenames only). |
| `find /path -type f -exec grep -il "search_text" {} \;` | Case-insensitive search for `search_text`. |
| `find /path -type f -name "*.log" -mtime +30 -exec rm {} \;` | Find and delete `.log` files older than 30 days. **Use with caution!** |
| `find /path -type f -size +100M -exec du -h {} \;` | Find files larger than 100MB and display their sizes. |
| `find /path -type f -exec md5sum {} \;` | Generate MD5 checksums for all files. |
| `find /path -type f -exec sha256sum {} \;` | Generate SHA-256 checksums for all files. |

This cheat sheet provides useful `find` commands for searching, filtering, modifying, and managing files efficiently in a Bash environment.