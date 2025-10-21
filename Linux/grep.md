Here’s a clear and practical summary of **`grep` command parameters (options)** and their **usage** in Linux 👇

---

### 🔹 Basic Syntax

```bash
grep [options] PATTERN [file...]
```

**Example:**

```bash
grep "error" /var/log/syslog
```

Searches for the word **“error”** inside `/var/log/syslog`.

---

### 🔹 Commonly Used `grep` Options

| Option         | Meaning                                             | Example                                   |                 |
| :------------- | :-------------------------------------------------- | :---------------------------------------- | --------------- |
| `-i`           | Ignore case (case-insensitive search)               | `grep -i "error" log.txt`                 |                 |
| `-r` or `-R`   | Recursive search in directories                     | `grep -r "timeout" /var/log`              |                 |
| `-v`           | Invert match (show lines *not* matching pattern)    | `grep -v "INFO" app.log`                  |                 |
| `-n`           | Show line number                                    | `grep -n "fail" syslog`                   |                 |
| `-c`           | Count the number of matching lines                  | `grep -c "fail" syslog`                   |                 |
| `-l`           | List only filenames with matches                    | `grep -l "fail" *.log`                    |                 |
| `-L`           | List filenames *without* matches                    | `grep -L "fail" *.log`                    |                 |
| `-w`           | Match whole word only                               | `grep -w "up" status.txt`                 |                 |
| `-x`           | Match whole line only                               | `grep -x "OK" result.txt`                 |                 |
| `-A NUM`       | Show *NUM* lines **after** match                    | `grep -A 2 "error" syslog`                |                 |
| `-B NUM`       | Show *NUM* lines **before** match                   | `grep -B 2 "error" syslog`                |                 |
| `-C NUM`       | Show *NUM* lines **around** match                   | `grep -C 2 "error" syslog`                |                 |
| `-E`           | Use extended regex (same as `egrep`)                | `grep -E "fail                            | error" log.txt` |
| `-F`           | Interpret pattern as fixed string (same as `fgrep`) | `grep -F "a.b" file.txt`                  |                 |
| `-q`           | Quiet mode (no output, just exit code)              | `grep -q "success" file && echo "Found!"` |                 |
| `--color=auto` | Highlight matches in color                          | `grep --color=auto "error" log.txt`       |                 |

---

### 🔹 Useful Combined Examples

1. **Count case-insensitive errors:**

   ```bash
   grep -i -c "error" /var/log/syslog
   ```

2. **Find IP addresses in logs:**

   ```bash
   grep -Eo "([0-9]{1,3}\.){3}[0-9]{1,3}" access.log
   ```

   (`-o` prints only the matching part of the line.)

3. **Show matching lines with context:**

   ```bash
   grep -A 2 -B 2 "failed" /var/log/auth.log
   ```

4. **Recursive search ignoring binary files:**

   ```bash
   grep -rI "password" /etc
   ```

---

Would you like me to show **examples with real-world Linux log files** (e.g., `/var/log/syslog`, `/var/log/auth.log`)?
That will help you learn by seeing practical use cases.
