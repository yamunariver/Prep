| Command | Description |
|--------|-------------|
| `ps` | Displays currently running processes. Common usage: `ps aux` (shows all processes). |
| `top` | Real-time view of system processes and resource usage (like Task Manager). |
| `htop` | An enhanced version of `top` with a better UI (may need to be installed). |
| `pidof [processname]` | Shows the PID of a running process, e.g., `pidof firefox`. |
| `kill [PID]` | Terminates a process by its PID. |
| `killall [processname]` | Kills all processes with the specified name. |
| `nice` | Starts a process with a specific priority (niceness level). |
| `renice` | Changes the priority of a running process. |
| `bg` | Resumes a suspended process in the background. |
| `fg` | Brings a background process to the foreground. |
| `jobs` | Lists background jobs in the current shell session. |
| `strace [command]` | Traces system calls and signals of a process. Useful for debugging. |
| `ps -ef` | Shows a full-format list of all processes. |
| `watch -n 1 'ps aux'` | Repeats the `ps aux` command every second (good for monitoring). |
