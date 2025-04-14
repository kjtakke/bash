**Sessions**

| Command | Description |
| --- | --- |
| `tmux` | Start a new session |
| `tmux new -s session_name` | Start a new session with a specific name |
| `tmux ls` | List all sessions |
| `tmux attach -t session_name` | Attach to a specific session |
| `tmux kill-session -t session_name` | Kill a specific session |
| `tmux kill-session -a` | Kill all sessions except the current one |
| `Ctrl+b` then `$` | Rename the current session |
| `Ctrl+b` then `d` | Detach from the current session |
| `Ctrl+b` then `s` | List all sessions |
| `Ctrl+b` then `(` | Switch to the previous session |
| `Ctrl+b` then `)` | Switch to the next session |

**Windows**

| Command | Description |
| --- | --- |
| `Ctrl+b` then `c` | Create a new window |
| `Ctrl+b` then `,` | Rename the current window |
| `Ctrl+b` then `&` | Close the current window |
| `Ctrl+b` then `p` | Switch to the previous window |
| `Ctrl+b` then `n` | Switch to the next window |
| `Ctrl+b` then `w` | List all windows |
| `Ctrl+b` then `0` to `9` | Switch to a window by number |
| `Ctrl+b` then `l` | Toggle to the last active window |
| `Ctrl+b` then `f` | Find a window by name |
| `Ctrl+b` then `.` | Move the current window to a new number |

**Panes**

| Command | Description |
| --- | --- |%
| `Ctrl+b` then `%` | Split the current pane vertically |
| `Ctrl+b` then `"` | Split the current pane horizontally |
| `Ctrl+b` then `x` | Close the current pane |
| `Ctrl+b` then `o` | Switch to the next pane |
| `Ctrl+b` then `q` | Display pane numbers |
| `Ctrl+b` then `q` then `0` to `9` | Switch to a pane by number |
| `Ctrl+b` then `{` | Move the current pane left |
| `Ctrl+b` then `}` | Move the current pane right |
| `Ctrl+b` then `z` | Toggle zoom for the current pane |
| `Ctrl+b` then `Space` | Toggle between pane layouts |
| `Ctrl+b` then `;` | Toggle to the last active pane |
| `Ctrl+b` then `Ctrl` + arrow key | Resize the current pane in the specified direction |

**Copy Mode**

| Command | Description |
| --- | --- |
| `Ctrl+b` then `[` | Enter copy mode |
| Arrow keys or `h`, `j`, `k`, `l` | Navigate in copy mode |
| `Space` | Start text selection |
| `Enter` | Copy the selected text |
| `Ctrl+b` then `]` | Paste the copied text |
| `/` | Search forward in copy mode |
| `?` | Search backward in copy mode |
| `n` | Repeat the last search forward |
| `N` | Repeat the last search backward |

**Miscellaneous**

| Command | Description |
| --- | --- |
| `Ctrl+b` then `:` | Enter command mode |
| `Ctrl+b` then `?` | List all key bindings |
| `tmux source-file ~/.tmux.conf` | Reload the tmux configuration file |
| `tmux list-keys` | List all key bindings |
| `tmux info` | Show every session, window, pane, etc. |
