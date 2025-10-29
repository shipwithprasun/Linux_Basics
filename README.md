# Linux Command Line Study Guide

## 1. Introduction

The Linux command line (shell / terminal) is a powerful interface for interacting with your system. Being comfortable with it will help you navigate file systems, manage processes, scripts, networking, compression, permissions, and much more. Tutorials such as the ones on the Ubuntu site and the DigitalOcean community show how mastering a handful of commands gives you 80 % coverage of daily tasks. ([Ubuntu][1])

---

## 2. First Time on the Terminal

### 2.1 Basic navigation & identity

| Command  | Description                                                  | Example                                 |
| -------- | ------------------------------------------------------------ | --------------------------------------- |
| `pwd`    | Print Working Directory – shows your current directory path. | `pwd` → `/home/you`                     |
| `whoami` | Shows the current user.                                      | `whoami` → `you`                        |
| `date`   | Displays current date/time.                                  | `date` → `Wed Oct 29 10:15:00 IST 2025` |
| `clear`  | Clears the terminal screen.                                  | `clear`                                 |

### 2.2 Listing directories

| Command  | Description                                                      | Example  |
| -------- | ---------------------------------------------------------------- | -------- |
| `ls`     | List files/directories in current directory.                     | `ls`     |
| `ls -lt` | List with long format (`-l`) sorted by modification time (`-t`). | `ls -lt` |

*(Use these to get comfortable with where you are, who you are, what the time is — small things that build confidence.)*

---

## 3. File & Directory Management

Here are key commands with examples and use-cases.

### 3.1 Viewing / creating / deleting files

| Command                               | Description                                                | Example             |
| ------------------------------------- | ---------------------------------------------------------- | ------------------- |
| `cat <file>`                          | Output the entire file contents to screen.                 | `cat notes.txt`     |
| `less <file>`                         | View file one page at a time (good for large files).       | `less large.log`    |
| `more <file>`                         | Similar to `less`, older pager.                            | `more file.txt`     |
| `touch <file_name>`                   | Create an empty file or update timestamp. ([Wikipedia][2]) | `touch newfile.txt` |
| `rm <file_name>`                      | Remove (delete) a file. Use with caution.                  | `rm oldfile.txt`    |
| `vi <file_name>` / `nano <file_name>` | Open file for editing in text editor (`vi` or `nano`).     | `vi config.txt`     |

### 3.2 Directory operations and moving files

| Command                    | Description                                                    | Example                                     |              |                 |
| -------------------------- | -------------------------------------------------------------- | ------------------------------------------- | ------------ | --------------- |
| `mkdir <dir_name>`         | Create a new directory.                                        | `mkdir projects`                            |              |                 |
| `rmdir <dir_name>`         | Remove an empty directory.                                     | `rmdir oldfolder`                           |              |                 |
| `rm -rf <dir_name>`        | Remove directory **and its contents recursively** (dangerous). | `rm -rf backup/old`                         |              |                 |
| `cd /path/folder`          | Change current directory to given path.                        | `cd /home/you/projects`                     |              |                 |
| `cd ..`                    | Move up one level in directory structure.                      | `cd ..`                                     |              |                 |
| `cp <file> /dest/path`     | Copy a file to a destination directory.                        | `cp report.txt ~/backups/`                  |              |                 |
| `cp fileA fileB`           | Copy and rename in one step.                                   | `cp old.txt new.txt`                        |              |                 |
| `mv <file> /dest/path`     | Move (or rename) a file to destination or new name.            | `mv draft.txt final.txt`                    |              |                 |
| `mv fileA fileNewName`     | Rename a file.                                                 | `mv oldname.txt newname.txt`                |              |                 |
| `head -5 file`             | View first 5 lines of a file.                                  | `head -5 access.log`                        |              |                 |
| `tail -5 file`             | View last 5 lines of a file.                                   | `tail -5 access.log`                        |              |                 |
| `sort file`                | Sort file lines in ascending order.                            | `sort names.txt`                            |              |                 |
| `sort -r file`             | Sort file lines in **reverse** order.                          | `sort -r names.txt`                         |              |                 |
| `sort file \| uniq`        | Sort then remove duplicates (via pipe).                        | `sort items.txt \| uniq`                    |              |                 |
| `split -l 3 file`          | Split a file into smaller files each of 3 lines.               | `split -l 3 bigfile.txt`                    |              |                 |
| `grep "word" file`         | Search for “word” in file, print matching lines.               | `grep "ERROR" log.txt`                      |              |                 |
| `egrep "word1|word2" file` |Extended grep: match either word1 or word2. 		      | `egrep "WARN | ERROR" log.txt` |
| `ls file*`                 | Wildcard listing: all filenames that start with “file”.        | `ls file*`                                  |              |                 |
| `touch file{1..5}`         | Create files `file1`, `file2`, `file3`, `file4`, `file5`.      | `touch file{1..5}`                          |              |                 |
| `shuf file`                | Shuffle the lines of a file (randomize).                       | `shuf list.txt`                             |              |                 |
| `wc -l file`               | Count number of lines in file.                                 | `wc -l data.csv`                            |              |                 |
| `cmp fileA fileB`          | Compare two files byte-by-byte.                                | `cmp f1.bin f2.bin`                         |              |                 |
| `diff -u fileA fileB`      | Show unified diff (line‐based) between fileA and fileB.        | `diff -u version1.txt version2.txt`         |              |                 |
| `find /path/ -name <file>` | Search for files by name recursively. ([Wikipedia][3])         | `find /var/log -name "*.log"`               |              |                 |
| `updatedb`                 | Rebuild database for `locate`.                                 | `sudo updatedb`                             |              |                 |
| `locate <file>`            | Quickly locate files using database.                           | `locate config.yaml`                        |              |                 |

### 3.3 Use-case examples

* **Use-case 1**: You want to backup all `.txt` files in a folder:

  ```bash
  mkdir ~/backup_txt
  cp *.txt ~/backup_txt/
  ```
* **Use-case 2**: You modified a log file and want to see only the last 10 lines:

  ```bash
  tail -10 application.log
  ```
* **Use-case 3**: You received a large CSV and you only want the unique sorted values in the second column:

  ```bash
  cut -d',' -f2 data.csv | sort | uniq > unique_second_column.txt
  ```

---

## 4. Utility Commands

These help you understand commands, see history, etc.

| Command             | Description                                                          | Example                |
| ------------------- | -------------------------------------------------------------------- | ---------------------- |
| `history`           | Show previous commands you’ve executed.                              | `history`              |
| `help`              | Built-in help for shell commands.                                    | `help cd`              |
| `man <command>`     | View the manual (“man page”) for a command. ([docs.icer.msu.edu][4]) | `man grep`             |
| `which <command>`   | Find the path to the executable of a command.                        | `which python3`        |
| `bc`                | Basic calculator in terminal.                                        | `echo "10/3" \| bc -l` |
| `cal`               | Display a calendar for current month (or specific year/month).       | `cal 2025`             |
| `uptime`            | Show how long system has been running + load.                        | `uptime`               |
| `script`            | Start recording terminal session to a file.                          | `script session.log`   |
| `alias l="ls -ltr"` | Create a shortcut alias: here `l` runs `ls -ltr`.                    | `alias l="ls -ltr"`    |

### Use-case

* You’re writing a bash script and you want to know how many commands you have used before:

  ```bash
  history | wc -l
  ```

---

## 5. Compress & Decompress

| Command                              | Description                                                       | Example                            |
| ------------------------------------ | ----------------------------------------------------------------- | ---------------------------------- |
| `gzip -k file`                       | Compress `file` into `file.gz`, keep original (`-k`).             | `gzip -k report.txt`               |
| `gzip -d file.gz` / `gunzip file.gz` | Decompress gzipped file.                                          | `gunzip report.txt.gz`             |
| `tar -czf myfiles.tar.gz myfiles/`   | Create a tarball compressed with gzip (c=create, z=gzip, f=file). | `tar -czf archive.tar.gz project/` |
| `tar -xzf myfiles.tar.gz`            | Extract from a tar.gz archive (x=extract).                        | `tar -xzf archive.tar.gz`          |
| `zip myfiles.zip file1 file2`        | Create a ZIP archive.                                             | `zip docs.zip file1.txt file2.txt` |
| `unzip -l myfiles.zip`               | List contents of a ZIP archive.                                   | `unzip -l docs.zip`                |

### Use-case

* You need to send a project folder via email:

  ```bash
  tar -czf project.zip project_folder/
  ```
* You need to extract someone’s archive:

  ```bash
  unzip files.zip -d destination_folder/
  ```

---

## 6. Download Files & Internet

| Command                                            | Description                                                                                | Example                                                |
| -------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------ |
| `wget URL_of_file`                                 | Download file from internet.                                                               | `wget https://example.com/file.tar.gz`                 |
| `wget -O opt_file.txt URL_of_file`                 | Download to a specific filename.                                                           | `wget -O latest-data.csv https://example.com/data.csv` |
| `curl http://numbersapi.com/random`                | Fetch data from URL using curl.                                                            | `curl http://numbersapi.com/random`                    |
| `apt` / `yum` / `dnf`                              | Package managers for installing/updating software (varies by distro). ([GeeksforGeeks][5]) | `sudo apt install httpd`                               |
| `rpm -qa \| grep app`                              | Query RPM database to see installed packages.                                              | `rpm -qa \| grep httpd`                                |
| `dnf list installed` / `apt search <package_name>` | List installed packages or search for packages.                                            | `apt search nginx`                                     |
| `systemctl start/stop service_name`                | Start/stop services under systemd.                                                         | `sudo systemctl start nginx`                           |
| `systemctl list-units --type=service --all`        | List all services and their statuses.                                                      | `systemctl list-units --type=service --all`            |

### Use-case

* **Use-case**: You discover a software you want to install:

  ```bash
  sudo apt update
  sudo apt install git
  ```
* **Use-case**: You download a remote script and execute it:

  ```bash
  wget https://example.com/install.sh -O install.sh
  chmod +x install.sh
  ./install.sh
  ```

---

## 7. Environment Variables

| Command                                  | Description                               | Example                                                 |
| ---------------------------------------- | ----------------------------------------- | ------------------------------------------------------- |
| `printenv`                               | Print all environment variables.          | `printenv`                                              |
| `export JAVA_HOME="/usr/lib/jvm/java_v"` | Set `JAVA_HOME` environment variable.     | `export JAVA_HOME="/usr/lib/jvm/java-11-openjdk-amd64"` |
| `export PATH=$JAVA_HOME/bin:$PATH`       | Add `JAVA_HOME/bin` to existing `PATH`.   | `export PATH=$JAVA_HOME/bin:$PATH`                      |
| `source ~/.bash_profile`                 | Reload the shell profile (apply changes). | `source ~/.bash_profile`                                |

### Use-case

* You installed a new JDK and you want your terminal sessions to see it:

  ```bash
  export JAVA_HOME="/usr/lib/jvm/java-17"
  export PATH=$JAVA_HOME/bin:$PATH
  ```

  Then test:

  ```bash
  java -version
  ```

---

## 8. Text Processing

| Command                            | Description                                               | Example                              |
| ---------------------------------- | --------------------------------------------------------- | ------------------------------------ |
| `awk -F , '{print $2}' file.csv`   | Use `awk`, set field separator (`,`), print 2nd column.   | `awk -F, '{print $2}' data.csv`      |
| `cut -c1-2 file.txt`               | Extract characters 1 to 2 of each line.                   | `cut -c1-2 report.txt`               |
| `sed -n '5p' file.txt`             | Use `sed` to print only line 5.                           | `sed -n '5p' file.txt`               |
| `sed -n 's/from/to/g' file.txt`    | Use `sed` to globally replace “from”→“to”.                | `sed -n 's/ERROR/WARNING/g' log.txt` |
| `tr [:lower:] [:upper:] <file.txt` | Translate lowercase to uppercase.                         | `tr [:lower:] [:upper:] <names.txt`  |
| `tr [:punct:] Z <file.txt`         | Replace all punctuation characters with `Z`.              | `tr [:punct:] Z <example.txt`        |
| `truncate -s 100M file.txt`        | Truncate or shrink-/grow a file to size 100MB.            | `truncate -s 100M dummy.bin`         |
| `echo "ABCDE" \| fold -w1`         | Break string into width 1 (i.e., one character per line). | `echo "HELLO" \| fold -w1`           |

### Use-case

* **Use-case**: You have a CSV with many columns, you just need column3:

  ```bash
  awk -F, '{print $3}' data.csv > col3.txt
  ```
* **Use-case**: You want to replace all ERROR keywords in log:

  ```bash
  sed -i 's/ERROR/WARNING/g' application.log
  ```

---

## 9. User & Permission Management

| Command                        | Description                                                       | Example                                    |
| ------------------------------ | ----------------------------------------------------------------- | ------------------------------------------ |
| `su <user_name>`               | Switch to another user account.                                   | `su admin`                                 |
| `exit`                         | Exit from current shell / logout.                                 | `exit`                                     |
| `sudo yum install httpd`       | (With root privileges) install httpd using yum.                   | `sudo yum install httpd`                   |
| `ssh user@hostname`            | Connect to remote machine via SSH.                                | `ssh jdoe@192.168.1.10`                    |
| `scp file user@hostname:/tmp/` | Secure-copy file to remote machine.                               | `scp report.pdf jdoe@10.0.0.5:/home/jdoe/` |
| `ls -ltr`                      | Long listing, sorted by time (often used to inspect permissions). | `ls -ltr /etc`                             |
| `chmod a+rwx file.txt`         | Change file permissions: all users (a) read/write/execute.        | `chmod a+rwx script.sh`                    |
| `chown root file.txt`          | Change owner of file to root.                                     | `chown root config.conf`                   |
| `chgrp paul file.txt`          | Change file’s group to “paul”.                                    | `chgrp paul data.csv`                      |
| `useradd <username>`           | Add a new user.                                                   | `sudo useradd alice`                       |
| `passwd <user>`                | Set/change password for user.                                     | `sudo passwd alice`                        |
| `groupadd <group>`             | Add a new group.                                                  | `sudo groupadd devteam`                    |
| `id username`                  | Show user’s UID, GID, groups.                                     | `id alice`                                 |
| `userdel <user>`               | Delete a user.                                                    | `sudo userdel bob`                         |
| `groupdel <group>`             | Delete a group.                                                   | `sudo groupdel interns`                    |
| `at`, `crontab`                | Schedule one-time (`at`) or recurring jobs (`crontab`).           | `crontab -e`                               |

---

## 10. Memory & System Information

### 10.1 Memory / disk usage

| Command | Description                              | Example           |
| ------- | ---------------------------------------- | ----------------- |
| `free`  | Show memory usage (RAM + swap).          | `free -h`         |
| `top`   | Interactive process & system monitoring. | `top`             |
| `du`    | Disk usage of files/directories.         | `du -sh /var/log` |
| `df`    | Disk filesystem usage.                   | `df -h`           |

### 10.2 System info

| Command    | Description                                          | Example                 |
| ---------- | ---------------------------------------------------- | ----------------------- |
| `hostname` | Get or set system’s hostname.                        | `hostname` → `server01` |
| `lscpu`    | Display CPU architecture info.                       | `lscpu`                 |
| `arch`     | Show machine architecture. ([Wikipedia][6])          | `arch` → `x86_64`       |
| `lsblk`    | List block devices (disks/partitions).               | `lsblk`                 |
| `uname -a` | Print all system information (kernel, architecture). | `uname -a`              |

---

## 11. Process Management

| Command                       | Description                                    | Example                |
| ----------------------------- | ---------------------------------------------- | ---------------------- |
| `ps -ef \| grep java`         | See all processes; filter for “java”.          | `ps -ef \| grep mysql` |
| `pgrep chron`                 | Find PID(s) of process named “chron”.          | `pgrep chron`          |
| `kill -9 PID`                 | Force-kill process with PID.                   | `kill -9 1234`         |
| `pkill httpd`                 | Kill processes by name.                        | `pkill httpd`          |
| `jobs`                        | List background jobs in current shell.         | `jobs`                 |
| `bg`                          | Resume a suspended job in background.          | `bg %1`                |
| `fg`                          | Bring a background job to foreground.          | `fg %1`                |
| `nohup ./script >/dev/null &` | Run `script` in background, immune to hangups. | `nohup backup.sh &`    |

---

## 12. Networking

| Command                     | Description                                | Example                       |
| --------------------------- | ------------------------------------------ | ----------------------------- |
| `ifconfig`                  | (Legacy) show network interfaces.          | `ifconfig`                    |
| `ip addr show`              | Modern alternative to `ifconfig`.          | `ip addr show`                |
| `ping www.google.com`       | Test connectivity to host.                 | `ping -c 4 www.google.com`    |
| `telnet IP Port`            | Connect via telnet (check port open).      | `telnet 192.168.1.1 80`       |
| `netstat -putan \| grep 80` | Show network connections & filter port 80. | `netstat -putan \| grep :443` |
| `traceroute host`           | Trace route path to host.                  | `traceroute example.com`      |

---

## 13. System Control

| Command    | Description                        | Example                |
| ---------- | ---------------------------------- | ---------------------- |
| `reboot`   | Reboot the system (requires root). | `sudo reboot`          |
| `shutdown` | Shutdown/power off the system.     | `sudo shutdown -h now` |

---

## 14. Firewall Settings

| Command                             | Description                                             | Example                                  |
| ----------------------------------- | ------------------------------------------------------- | ---------------------------------------- |
| `firewall-cmd --list-all`           | List all firewall rules & zones (on firewalld systems). | `sudo firewall-cmd --list-all`           |
| `firewall-cmd --add-port=20201/tcp` | Open TCP port 20201 (temporary until reload).           | `sudo firewall-cmd --add-port=20201/tcp` |

---

## 15. Putting It All Together: Practical Scenarios

### Scenario A: Clean up log files older than 7 days and archive

```bash
cd /var/log/myapp
find . -type f -mtime +7 -name '*.log' -print \
    \| xargs tar -czf ../old_logs_$(date +%F).tar.gz
```

### Scenario B: Download weekly data, process column, and upload results

```bash
cd ~/data_pipeline
wget -O raw_weekly.csv https://example.com/data/week_$(date +%V).csv
awk -F, '{print $3}' raw_weekly.csv | sort | uniq > col3_unique.txt
scp col3_unique.txt user@remote:/data/weekly/
```

### Scenario C: Monitor disk usage and alert if > 80%

```bash
if [ $(df -h / | grep / | awk '{print $5}' | sed 's/%//') -gt 80 ]; then
  echo "Disk usage above 80%" | mail -s "Alert" admin@example.com
fi
```

---

## 16. Tips & Best Practices

* Use `man <command>` and `--help` to explore options. ([docs.icer.msu.edu][4])
* Use pipes (`|`) and redirection (`>`, `>>`) to chain commands and save output.
* Be very careful with `rm -rf` — test paths with `ls` first.
* Use appropriate permissions; never run everything as root unless needed.
* Keep your shell history (`history`) for reference and audit.
* Use wildcards (`*`, `?`) sensibly and test before executing destructive commands.
* Keep backups of important data before batch operations.
* Practice: create small experiments and gradually combine commands.

---

## 17. Summary

You’ve now got a comprehensive set of commands grouped by functionality, each with explanation and example. As you practice them you’ll gain speed and confidence with the Linux terminal. Use this guide as your reference and even extend it with your own favorite commands and workflows.

[1]: https://ubuntu.com/tutorials/command-line-for-beginners?utm_source=chatgpt.com "The Linux command line for beginners - Ubuntu"
[2]: https://en.wikipedia.org/wiki/Touch_%28command%29?utm_source=chatgpt.com "Touch (command)"
[3]: https://en.wikipedia.org/wiki/Find_%28Unix%29?utm_source=chatgpt.com "Find (Unix)"
[4]: https://docs.icer.msu.edu/Linux_Command_Line_Interface_for_Beginners_II/?utm_source=chatgpt.com "Linux Command Line for Beginners II"
[5]: https://www.geeksforgeeks.org/linux-unix/linux-tutorial/?utm_source=chatgpt.com "Linux/Unix Tutorial - GeeksforGeeks"
[6]: https://en.wikipedia.org/wiki/Cd_%28command%29?utm_source=chatgpt.com "Cd (command)"
