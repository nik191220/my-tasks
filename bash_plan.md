## **Step 1 — Basics of Shell & Bash**

**Topics:**

-   What is a shell? What is Bash?
    
-   Difference between interactive shell and script execution.
    
-   How to create a `.sh` file.
    
-   `chmod` and making a script executable.
    
-   Running scripts: `./script.sh` vs `bash script.sh`.
    
-   Shebang (`#!/bin/bash` or `#!/usr/bin/env bash`).
    

**Questions to answer:**

-   How do I create and run a shell script?
    
-   What does the first line `#!/bin/bash` do?
    
-   Why might a script fail to run with `./script.sh`?
    

---

## **Step 2 — Basic Syntax & Commands**

**Topics:**

-   Comments (`#`).
    
-   Printing output: `echo`, `printf`.
    
-   Variables: definition, usage, quoting (`"`, `'`, and unquoted).
    
-   Command substitution: `` `command` `` and `$(command)`.
    
-   Reading user input: `read`.
    
-   Using exit codes (`$?`).
    

**Questions to answer:**

-   How do I store and print a variable?
    
-   What is the difference between `"variable"` and `'variable'`?
    
-   How do I capture the output of a command into a variable?
    

---

## **Step 3 — Working with Files & Paths**

**Topics:**

-   Common commands in scripts: `ls`, `cat`, `cp`, `mv`, `rm`, `mkdir`, `touch`.
    
-   Relative vs absolute paths.
    
-   Using wildcards (`*`, `?`).
    
-   Checking file existence: `[ -f file ]`, `[ -d dir ]`.
    
-   Using `basename` and `dirname`.
    

**Questions to answer:**

-   How can I check if a file exists before trying to read it?
    
-   How do I create a directory only if it doesn’t exist?
    

---

## **Step 4 — Conditional Logic**

**Topics:**

-   `if`, `elif`, `else`, `fi`.
    
-   Test operators: `-eq`, `-ne`, `-lt`, `-gt`, `-le`, `-ge` for numbers; `=` and `!=` for strings.
    
-   File test operators: `-f`, `-d`, `-e`, `-s`, `-r`, `-w`, `-x`.
    
-   Logical operators: `&&`, `||`, `!`.
    

**Questions to answer:**

-   How do I write a script that checks if a directory exists and creates it if not?
    
-   What’s the difference between `=` and `==` in Bash?
    

---

## **Step 5 — Loops**

**Topics:**

-   `for` loops (over lists, over output of commands, using `{1..10}` syntax).
    
-   `while` loops.
    
-   `until` loops.
    
-   Breaking and continuing loops (`break`, `continue`).
    

**Questions to answer:**

-   How do I loop over all `.txt` files in a directory?
    
-   How do I read a file line-by-line in a loop?
    

---

## **Step 6 — Functions**

**Topics:**

-   Defining and calling functions.
    
-   Local vs global variables.
    
-   Returning values (`return` vs `echo`).
    
-   Using `$1`, `$2`, `$@`, `$*` for function parameters.
    

**Questions to answer:**

-   How do I write a function that takes two arguments and prints their sum?
    
-   What is the difference between `"$@"` and `"$*"`?
    

---

## **Step 7 — Script Arguments & Parameters**

**Topics:**

-   Positional parameters `$1`, `$2`, `$@`.
    
-   `$0` (script name), `$#` (argument count).
    
-   Shifting parameters (`shift`).
    
-   Default values for arguments.
    

**Questions to answer:**

-   How do I make my script require exactly two arguments?
    
-   How can I set a default value if the user didn’t provide one?
    

---

## **Step 8 — Error Handling & Debugging**

**Topics:**

-   Checking exit status with `$?`.
    
-   `set -e`, `set -u`, `set -o pipefail`.
    
-   Using `trap` to handle signals.
    
-   Adding debug output with `set -x`.
    

**Questions to answer:**

-   How do I stop a script when a command fails?
    
-   How can I trap `CTRL+C` to clean up before exiting?
    

---

## **Step 9 — Working with Text & Data**

**Topics:**

-   Pipes (`|`) and redirects (`>`, `>>`, `<`, `2>`, `&>`).
    
-   `grep`, `awk`, `sed`, `cut`, `sort`, `uniq`, `wc`.
    
-   String manipulation: `${var%pattern}`, `${var#pattern}`, `${var/pattern/replacement}`.
    

**Questions to answer:**

-   How do I extract the first column from a CSV file?
    
-   How do I replace all spaces in a string with underscores?
    

---

## **Step 10 — Best Practices**

**Topics:**

-   Writing readable scripts (indentation, comments).
    
-   Quoting variables to avoid word-splitting.
    
-   Using `#!/usr/bin/env bash` for portability.
    
-   Avoiding hardcoding paths.
    
-   Logging.
    

**Questions to answer:**

-   How do I make a script both readable and safe?
    
-   What’s the purpose of double-quoting variables?
    

---

## **1\. Backup Script for a Folder**

**Goal:** Automate creating a timestamped backup of a folder.

**What to do:**

-   The script should take **two arguments**:
    
    1.  Path to the folder you want to back up.
        
    2.  Path to the directory where the backup should be saved.
        
-   The script should:
    
    -   Check if the source folder exists. If not, show an error and exit.
        
    -   Create the backup directory if it doesn’t exist.
        
    -   Create a `.tar.gz` archive of the folder with a timestamp in the filename (e.g., `backup_2025-08-14_15-30.tar.gz`).
        
    -   Print a message showing where the backup was saved.
        

**Example run:**

```bash
./backup.sh /home/user/documents /home/user/backups
```

Result:  
`/home/user/backups/backup_2025-08-14_15-30.tar.gz`

---

## **2\. File Organizer by Extension**

**Goal:** Sort all files in a given folder into subfolders based on their file extension.

**What to do:**

-   The script should take **one argument**: path to the folder to organize.
    
-   For each file:
    
    -   Detect its extension (e.g., `.txt`, `.jpg`, `.sh`).
        
    -   Create a folder named after the extension (without the dot), e.g., `txt`, `jpg`, `sh`.
        
    -   Move the file into that folder.
        
-   Ignore directories and hidden files.
    

**Example run:**

```bash
./organize.sh /home/user/downloads
```

Result:

```markdown
downloads/
  txt/
    notes.txt
  jpg/
    photo.jpg
  sh/
    script.sh
```

---

## **3\. Simple Log Monitor**

**Goal:** Watch a log file in real-time and alert when a specific word appears.

**What to do:**

-   The script should take **two arguments**:
    
    1.  Path to the log file.
        
    2.  Word to search for (case-insensitive).
        
-   It should:
    
    -   Check if the file exists.
        
    -   Use `tail -f` to follow the log file.
        
    -   Whenever the given word appears in a new line, print `ALERT: Found "<word>"` in red text.
        

**Example run:**

```bash
./log_monitor.sh /var/log/syslog error
```

Output example:

```vbnet
ALERT: Found "error"
```

(in red when printed)

---

## **4\. Disk Usage Report**

**Goal:** Generate a readable report of the largest files in a directory.

**What to do:**

-   The script should take **one argument**: path to the directory.
    
-   It should:
    
    -   Check if the directory exists.
        
    -   Use `du` and `sort` to find the top 5 largest files/directories inside.
        
    -   Save the report to a file named `disk_report.txt` in the current directory.
        
    -   Print the report on screen as well.
        

**Example run:**

```bash
./disk_report.sh /home/user
```

Example output:

```arduino
Largest files in /home/user:
1. 1.2G /home/user/video.mp4
2. 800M /home/user/backup.tar.gz
...
```

---

## **5\. Bulk Rename Files**

**Goal:** Rename all files in a folder by adding a prefix.

**What to do:**

-   The script should take **two arguments**:
    
    1.  Path to the folder.
        
    2.  Prefix string.
        
-   It should:
    
    -   Loop through all files in the folder.
        
    -   Add the prefix to each filename (e.g., `prefix_filename.txt`).
        
    -   Skip directories.
        

**Example run:**

```bash
./rename_files.sh /home/user/photos holiday_
```

Result:

```
photos/
  holiday_IMG001.jpg
  holiday_IMG002.jpg
```

---

If you do these, you’ll practice:

-   Arguments (`$1`, `$2`)
    
-   Conditionals (`if`, `[ -f ]`, `[ -d ]`)
    
-   Loops (`for`, `while`)
    
-   Command substitution
    
-   File operations
    

---
