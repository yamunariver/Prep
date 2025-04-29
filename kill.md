| Signal | Number | Name     | Description |
|--------|--------|----------|-------------|
| `-1`   | `SIGHUP`   | Hang up | Often used to reload a process configuration (e.g., `kill -1 nginx`). |
| `-2`   | `SIGINT`   | Interrupt | Sent when you press `Ctrl+C` in the terminal. Gracefully stops a process. |
| `-9`   | `SIGKILL`  | Kill | Immediately and forcefully terminates the process. Cannot be caught or ignored. |
| `-15`  | `SIGTERM`  | Terminate | Politely asks the process to stop. Can be caught and handled. (default for `kill`) |
| `-18`  | `SIGCONT`  | Continue | Resumes a stopped process. Often used with `fg`/`bg`. |
| `-19`  | `SIGSTOP`  | Stop | Suspends a process (like pressing `Ctrl+Z`). Cannot be caught. |
| `-20`  | `SIGTSTP`  | Terminal Stop | Like `SIGSTOP`, but **can be caught** by the process. Triggered by `Ctrl+Z`. |
