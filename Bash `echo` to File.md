# Bash `echo` to File 

| Command | Description |
|---------|-------------|
| `echo "Hello World"` | Print "Hello World" to the terminal. |
| `echo "Hello World" > file.txt` | Write "Hello World" to `file.txt` (overwrite if file exists). |
| `echo "Hello World" >> file.txt` | Append "Hello World" to `file.txt`. |
| `echo -n "Hello World" > file.txt` | Write without a newline at the end. |
| `echo -e "Line1\nLine2" > file.txt` | Write with newline (`\n`) between lines. |
| `echo -e "Col1\tCol2" > file.txt` | Write with tab (`\t`) between columns. |
| `echo -e "Hello\bWorld" > file.txt` | Write "HelloWorld" by removing `\b` (backspace). |
| `echo "Text" | tee file.txt` | Write "Text" to `file.txt` and print to terminal. |
| `echo "Text" | tee -a file.txt` | Append "Text" to `file.txt` and print to terminal. |
| `echo "$(date)" > file.txt` | Write the current date/time to `file.txt`. |
| `echo "User: $USER" > file.txt` | Write an environment variable to a file. |
| `echo 'echo "Hello"' > script.sh` | Write a command into a script file. |
| `echo 'export PATH="$PATH:/custom/path"' >> ~/.bashrc` | Append an export command to `.bashrc`. |
| `echo -e "Multi-line\nExample" > file.txt` | Write multiple lines using `\n`. |
| `cat > file.txt <<EOF`<br>`Hello`<br>`World`<br>`EOF` | Create a file with multiple lines using a **heredoc**. |
| `cat <<EOF >> file.txt`<br>`Append this text`<br>`EOF` | Append multiple lines to a file. |
| `echo '$(ls -l)' > file.txt` | Write the output of a command as plain text. |
| `echo "$(ls -l)" > file.txt` | Write the actual output of `ls -l` to a file. |
| `echo "Escape \$VAR" > file.txt` | Write `$VAR` as literal text (`\$VAR`). |

**Notes:**  
- `>` overwrites the file.  
- `>>` appends to the file.  
- `tee` allows writing to a file while displaying output.  
- `-e` enables escape sequences like `\n` and `\t`.  
- Single quotes (`'`) prevent variable expansion; double quotes (`"`) allow it.  