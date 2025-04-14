# SED

| Command | Description | Example |
|---------|-------------|---------|
| `s/pattern/replacement/` | Substitute the first occurrence of a pattern in a line | `sed 's/foo/bar/' file.txt` |
| `s/pattern/replacement/g` | Substitute all occurrences in a line | `sed 's/foo/bar/g' file.txt` |
| `s/pattern/replacement/gi` | Case-insensitive substitution | `sed 's/foo/bar/gi' file.txt` |
| `s/pattern/replacement/3` | Replace only the 3rd occurrence in a line | `sed 's/foo/bar/3' file.txt` |
| `s/pattern/replacement/gw file` | Save replaced lines to a file | `sed 's/foo/bar/gw output.txt' file.txt` |
| `N; s/pattern/replacement/` | Match across multiple lines (using `N` to join) | `sed 'N; s/\n/ /' file.txt` |
| `/pattern/d` | Delete lines matching a pattern | `sed '/foo/d' file.txt` |
| `10d` | Delete the 10th line | `sed '10d' file.txt` |
| `1,10d` | Delete lines 1-10 | `sed '1,10d' file.txt` |
| `$d` | Delete the last line | `sed '$d' file.txt` |
| `d` | Delete all lines (clear file content) | `sed 'd' file.txt` |
| `p` | Print matched lines (use with `-n` to suppress default output) | `sed -n '/foo/p' file.txt` |
| `q` | Quit after the first match (useful for efficiency) | `sed '/foo/q' file.txt` |
| `10q` | Stop processing after 10 lines | `sed '10q' file.txt` |
| `a\ text` | Append text after a line | `sed '5a\ New Line' file.txt` |
| `i\ text` | Insert text before a line | `sed '5i\ New Line' file.txt` |
| `c\ text` | Replace an entire line | `sed '5c\ Replaced Line' file.txt` |
| `y/abc/xyz/` | Translate characters (like `tr`) | `sed 'y/abc/xyz/' file.txt` |
| `:label` `N` `s/\n/ /` `t label` | Loop to remove newlines between lines | `sed ':a;N;$!ba;s/\n/ /g' file.txt` |
| `s/^\s*//` | Remove leading spaces | `sed 's/^[ \t]*//' file.txt` |
| `s/\s*$//` | Remove trailing spaces | `sed 's/[ \t]*$//' file.txt` |
| `s/\s\+/ /g` | Replace multiple spaces with a single space | `sed 's/[ \t]\+/ /g' file.txt` |
| `/pattern/!d` | Keep only lines matching a pattern | `sed '/foo/!d' file.txt` |
| `/pattern/=` | Print line numbers of matches | `sed -n '/foo/=' file.txt` |
| `= ` | Print line numbers of all lines | `sed '=' file.txt` |
| `s/$begin:math:text$.*$end:math:text$/\U\1/` | Convert to uppercase | `sed 's/$begin:math:text$.*$end:math:text$/\U\1/' file.txt` |
| `s/$begin:math:text$.*$end:math:text$/\L\1/` | Convert to lowercase | `sed 's/$begin:math:text$.*$end:math:text$/\L\1/' file.txt` |
| `s/\b$begin:math:text$.$end:math:text$/\u\1/g` | Capitalise first letter of each word | `sed 's/\b$begin:math:text$.$end:math:text$/\u\1/g' file.txt'` |
| `-i` | Edit file in place (overwrite) | `sed -i 's/foo/bar/g' file.txt` |
| `-i.bak` | Edit in place with a backup | `sed -i.bak 's/foo/bar/g' file.txt` |
| `-e` | Use multiple commands | `sed -e 's/foo/bar/' -e 's/baz/qux/' file.txt` |
| `-f script.sed` | Run commands from a file | `sed -f script.sed file.txt` |

## Useful Multi-Line Commands
```sh
# Remove blank lines
sed '/^$/d' file.txt

# Remove trailing whitespace
sed 's/[[:space:]]*$//' file.txt

# Replace multiple spaces with a single space
sed 's/[[:space:]]\+/ /g' file.txt

# Print lines between two patterns
sed -n '/START/,/END/p' file.txt

# Remove lines between two patterns
sed '/START/,/END/d' file.txt

# Number only non-empty lines
sed '/./=' file.txt | sed 'N; s/\n/ /'

# Convert CSV to TSV (replace commas with tabs)
sed 's/,/\t/g' file.csv