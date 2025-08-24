# 🐧 Linux Basics

## 🐧 Lecture: Introduction to Linux

### 1.1 What is Linux?

Linux is a **free, open-source operating system (OS)** based on **UNIX**.

* Unlike Windows or macOS, Linux is built around the idea of **freedom and flexibility**.
* It is widely used in **servers, cybersecurity, cloud systems, IoT devices, and networking**.
* The Linux kernel (the "core" of the OS) was created by **Linus Torvalds in 1991**.

👉 In cybersecurity, Linux is essential because most tools (e.g., Nmap, Metasploit, Wireshark) are built to run on Linux.

---

### 1.2 Why Learn Linux?

* **Cybersecurity & Ethical Hacking:** Most penetration testing tools are Linux-based.
* **Servers & Cloud:** 96% of the world’s top servers run on Linux.
* **Flexibility:** You can modify, script, and automate almost anything.
* **Security:** Linux is more secure and less prone to malware compared to other OS.

---

### 1.3 Linux Distributions (Distros)

A **Linux distribution** is a version of Linux packaged with its own tools, desktop environment, and package manager.

Popular distros:

* **Ubuntu (Debian-based):** Beginner-friendly, widely used.
* **Debian:** Stable, good for servers.
* **CentOS / RHEL:** Used in enterprises and servers.
* **Arch Linux:** Minimal, highly customizable.
* **Kali Linux:** Designed for penetration testing and security research.

👉 For cybersecurity learners, **Kali Linux** or **Parrot Security OS** are commonly recommended.

---

### 1.4 Linux File System Hierarchy

Linux organizes files in a **tree structure** starting from the root directory `/`.

* `/` → Root directory (everything starts here)
* `/home` → User files (like "Documents" in Windows)
* `/etc` → Configuration files
* `/bin` → Essential binary commands (`ls`, `cp`, etc.)
* `/usr` → User applications and libraries
* `/var` → Logs and variable data
* `/tmp` → Temporary files
* `/root` → Home directory for the root (administrator) user

👉 Unlike Windows (`C:\` drive), Linux doesn’t use drive letters. Everything is inside `/`.

---

### 1.5 Shell vs. Terminal

* **Terminal:** The program (window) where you type commands.
* **Shell:** The command-line interpreter that processes your input (e.g., Bash, Zsh).

Example:

* You open a **Terminal app**, and inside it, you interact with the **Bash shell**.

---

### 1.6 Summary

* Linux = Open-source UNIX-like operating system.
* Essential for cybersecurity, networking, and servers.
* Many **distros** exist for different purposes.
* File system hierarchy organizes everything starting from `/`.
* The **shell** interprets commands inside the **terminal**.

---

💡 **Practice Exercise**

1. Open your Linux terminal.
2. Type:

   ```bash
   uname -a
   ```

   → Shows your system info.
3. Navigate through directories:

   ```bash
   cd /
   ls
   ```

   → Explore the Linux root structure.

---


### **2. Essential Linux Commands**

Let’s build a **lecture-style note** for you:

---

# 🖥️ Essential Linux Commands

Learning Linux is all about mastering the command line. These commands form the foundation for interacting with the system, managing files, and navigating directories.

---

## 1. Navigation & Directory Management

* **pwd** → Print Working Directory

  * Shows the current directory you’re in.
  * Example:

    ```
    pwd
    /home/abdul
    ```

* **ls** → List directory contents

  * `ls` → basic list
  * `ls -l` → detailed list with permissions, owner, size, date
  * `ls -a` → include hidden files

* **cd** → Change Directory

  * `cd /etc` → go to `/etc`
  * `cd ..` → move up one directory
  * `cd ~` → go to your home directory

* **tree** → Show directories in tree form (may need install with `sudo apt install tree`)

---

## 2. File & Directory Operations

* **touch** → Create an empty file

  * `touch file.txt`

* **cat** → View file contents

  * `cat file.txt`

* **less / more** → Scroll through a file page by page

  * `less file.txt`

* **head** & **tail** → Show first or last lines of a file

  * `head -n 10 file.txt` → first 10 lines
  * `tail -f logfile.log` → live monitoring of logs

* **cp** → Copy files or directories

  * `cp file1.txt file2.txt`
  * `cp -r dir1 dir2` (recursive copy)

* **mv** → Move or rename files

  * `mv file.txt /home/user/` (move)
  * `mv oldname.txt newname.txt` (rename)

* **rm** → Remove files or directories

  * `rm file.txt`
  * `rm -r folder/` (delete folder recursively — ⚠️ careful!)

* **mkdir** → Make new directory

  * `mkdir myfolder`

* **rmdir** → Remove empty directory

  * `rmdir myfolder`

---

## 3. System Information & Monitoring

* **uname -a** → Show system information
* **whoami** → Current logged-in user
* **date** → Display system date/time
* **uptime** → Show how long system has been running
* **top** → Display active processes (press `q` to quit)
* **htop** (better version of `top`, may need install)

---

## 4. Searching & Finding

* **find** → Search for files/directories

  * `find / -name file.txt`

* **grep** → Search text inside files

  * `grep "error" logfile.log`

* **locate** → Quickly search files (needs `sudo updatedb` first)

  * `locate passwd`

---

## 5. File Permissions & Ownership

* **ls -l** → Shows permissions (e.g., `-rw-r--r--`)
* **chmod** → Change permissions

  * `chmod 755 file.sh`
* **chown** → Change ownership

  * `chown user:user file.txt`

---

## 6. Package Management (Debian/Ubuntu based)

* **apt update** → Update package list
* **apt upgrade** → Upgrade packages
* **apt install packagename** → Install package
* **apt remove packagename** → Uninstall package

---

## 7. Networking Basics

* **ping** → Test connectivity

  * `ping google.com`
* **ifconfig / ip addr** → Show network interfaces (use `ip addr` in newer systems)
* **netstat -tulnp** (or `ss -tulnp`) → Show listening ports
* **curl / wget** → Fetch content from web

---

## 8. Archive & Compression

* **tar** → Create/extract archive

  * `tar -cvf archive.tar folder/` (create)
  * `tar -xvf archive.tar` (extract)
* **gzip / gunzip** → Compress or decompress files

---

## 9. User Management

* **adduser** → Add a new user
* **passwd username** → Change user password
* **who** → List logged-in users
* **su - username** → Switch user

---

## 10. Help & Documentation

* **man command** → Show manual for a command

  * Example: `man ls`
* **command --help** → Quick help

---

✅ These are the **core commands** you’ll use daily. Mastering them means you’ll be comfortable in almost any Linux environment — especially useful in cybersecurity.

---


# 🐧 Lecture: User & Permissions in Linux

Linux is a **multi-user operating system**, which means understanding **users, groups, and permissions** is essential for security and system management.

---

## 1. Users in Linux

* **Root user**

  * The **superuser** with full system control.
  * Home directory: `/root`
  * Can perform any operation, including changing system files.

* **Normal users**

  * Standard users with limited permissions.
  * Home directories: `/home/username`
  * Cannot modify system-critical files without `sudo`.

* **Commands to check users:**

  * `whoami` → shows current logged-in user
  * `id` → shows user ID (UID), group ID (GID), and group memberships
  * `who` → lists logged-in users

---

## 2. Groups

* A **group** is a collection of users.
* Helps manage permissions for multiple users at once.
* Example: `sudo`, `adm`, `staff`, `www-data`
* Commands:

  * `groups` → shows which groups a user belongs to
  * `groupadd groupname` → create a new group
  * `usermod -aG groupname username` → add a user to a group

---

## 3. File Ownership

* Every file/directory has:

  * **Owner** → user who created it
  * **Group** → group associated with the file

* Commands:

  * `ls -l` → view owner and group

    ```
    -rw-r--r-- 1 abdul staff 1234 Aug 24 07:00 file.txt
    ```

    * Owner: `abdul`
    * Group: `staff`

* Change ownership:

  * `chown user file.txt` → change owner
  * `chown user:group file.txt` → change owner and group

---

## 4. File Permissions

* Linux permissions are **read (r), write (w), execute (x)**

* Three categories:

  1. **User (u)** → owner
  2. **Group (g)** → group members
  3. **Others (o)** → everyone else

* Displayed with `ls -l`:

  ```
  -rwxr-xr-- 1 abdul staff 1234 Aug 24 07:00 script.sh
  ```

  * Owner: read, write, execute
  * Group: read, execute
  * Others: read

* Change permissions:

  * Symbolic: `chmod u+x file.sh` → add execute to owner
  * Numeric: `chmod 755 file.sh` → rwx for owner, rx for group/others

---

## 5. Sudo & Privileges

* `sudo` → run a command as root

  ```
  sudo apt update
  ```
* Always use **least privilege principle** — only use root when necessary.

---

## 6. Practical Tips

* Always check permissions before editing critical files:

  ```
  ls -l /etc/passwd
  ```
* Avoid running unnecessary commands as root.
* Group management simplifies access control for multiple users.

---

💡 **Practice Exercises:**

1. Create a new user: `sudo adduser testuser`
2. Create a new group: `sudo groupadd devteam`
3. Add the user to the group: `sudo usermod -aG devteam testuser`
4. Create a file and check its owner:

   ```
   touch project.txt
   ls -l project.txt
   ```
5. Change owner and group: `sudo chown testuser:devteam project.txt`
6. Modify permissions using symbolic and numeric methods:

   ```
   chmod u+rwx project.txt
   chmod 640 project.txt
   ```

---



# 🖥️ Lecture: Process & System Management in Linux

Linux is a **multi-tasking operating system**, meaning it can run multiple processes at the same time. Understanding **processes and system management commands** is crucial for monitoring, troubleshooting, and securing a system.

---

## 1. What is a Process?

* A **process** is a program or task that is currently running.
* Each process has a **Process ID (PID)** and is associated with a user.
* Processes can be **foreground** (interactively running) or **background** (running without blocking the terminal).

---

## 2. Viewing Processes

* **ps** → snapshot of current processes

  ```
  ps
  ps aux   # shows all processes with user and CPU info
  ```
* **top** → interactive real-time process viewer

  * Press `q` to quit
* **htop** → enhanced, colorful top (needs `sudo apt install htop`)

---

## 3. Managing Processes

* **kill** → terminate a process by PID

  ```
  kill 1234
  ```
* **killall** → terminate all processes by name

  ```
  killall firefox
  ```
* **jobs** → list background jobs started in the current shell
* **fg** → bring a background job to the foreground
* **bg** → resume a suspended job in the background

---

## 4. System Information Commands

* **uname -a** → kernel and system info
* **uptime** → system running time and load averages
* **df -h** → disk space usage
* **du -h filename** → size of files/directories
* **free -h** → memory usage
* **dmesg** → kernel messages

---

## 5. Monitoring Resources

* **top / htop** → CPU, memory, swap, and process usage
* **vmstat** → reports virtual memory statistics
* **iostat** → CPU and I/O statistics
* **sar** → system activity report (may require `sudo apt install sysstat`)

---

## 6. Practical Tips

* Use `ps aux | grep process_name` to locate a process PID.
* Always check which processes are consuming high resources (`top` or `htop`).
* Avoid killing system-critical processes unless necessary.
* Regularly monitor disk space (`df -h`) and memory usage (`free -h`).

---

💡 **Practice Exercises:**

1. List all processes: `ps aux`
2. View real-time system processes: `top`
3. Install and run `htop`
4. Start a background process:

   ```
   sleep 100 &
   jobs
   ```
5. Bring it to the foreground: `fg %1`
6. Kill a process by PID: `kill <PID>`
7. Check disk space and memory: `df -h`, `free -h`
8. Display system uptime: `uptime`
9. View kernel messages: `dmesg | tail`

---


# 📦 Lecture: Package Management in Linux

Linux uses **package managers** to install, update, and remove software. Each distribution has its own package system. Understanding this is essential for keeping your system secure and up-to-date.

---

## 1. What is a Package?

* A **package** is a compressed file containing software, dependencies, and metadata.
* Linux uses package managers to **automate installation, updates, and removal**.

---

## 2. Debian/Ubuntu-Based Package Management

**APT (Advanced Package Tool)** is the most common package manager for Debian-based systems (Ubuntu, Kali, Debian).

### Common Commands:

* **Update package list**

  ```
  sudo apt update
  ```
* **Upgrade installed packages**

  ```
  sudo apt upgrade
  ```
* **Install a package**

  ```
  sudo apt install packagename
  ```
* **Remove a package**

  ```
  sudo apt remove packagename
  ```
* **Remove package and config files**

  ```
  sudo apt purge packagename
  ```
* **Search for a package**

  ```
  apt search packagename
  ```

---

## 3. Debian Low-Level Tool: dpkg

* **dpkg** manages `.deb` packages directly.
* Commands:

  * Install a package:

    ```
    sudo dpkg -i package.deb
    ```
  * Remove a package:

    ```
    sudo dpkg -r package_name
    ```
  * List installed packages:

    ```
    dpkg -l
    ```

---

## 4. RedHat/CentOS/Fedora-Based Package Management

* **RPM (RedHat Package Manager)** handles `.rpm` files.

* Commands:

  * Install package: `sudo rpm -ivh package.rpm`
  * Remove package: `sudo rpm -e package_name`
  * Query installed packages: `rpm -qa`

* **YUM / DNF** (high-level managers for dependencies)

  * Install: `sudo yum install packagename`
  * Update: `sudo yum update`
  * Remove: `sudo yum remove packagename`

---

## 5. Practical Tips

* Always **update your package lists** before installing software:

  ```
  sudo apt update
  ```
* Use `apt upgrade` or `yum update` to patch security vulnerabilities.
* When installing `.deb` or `.rpm` manually, check for **dependency errors**.

---

💡 **Hands-On Practice:**

1. Update your package list: `sudo apt update`
2. Upgrade all installed packages: `sudo apt upgrade -y`
3. Install a package (example: `htop`): `sudo apt install htop`
4. Remove a package: `sudo apt remove htop`
5. Search for a package: `apt search curl`
6. Try installing a `.deb` file (if available):

   ```
   sudo dpkg -i package.deb
   sudo apt install -f   # Fix missing dependencies
   ```

---



# 📦 Lecture: File Compression & Archiving in Linux

Linux uses **archives and compression tools** to store multiple files efficiently and save disk space. These skills are essential for backups, transferring files, and managing system data.

---

## 1. Archiving Files with `tar`

* **tar** combines multiple files/directories into a single file (archive), optionally compressing it.
* **Common options:**

  * `c` → create archive
  * `x` → extract archive
  * `v` → verbose (show files being processed)
  * `f` → specify filename
* **Examples:**

  * Create an archive:

    ```
    tar -cvf archive.tar folder/
    ```
  * Extract an archive:

    ```
    tar -xvf archive.tar
    ```
  * Create a compressed archive (gzip):

    ```
    tar -czvf archive.tar.gz folder/
    ```
  * Extract compressed archive:

    ```
    tar -xzvf archive.tar.gz
    ```

---

## 2. Compressing Files

* **gzip** → compress a single file

  ```
  gzip file.txt       # creates file.txt.gz
  gunzip file.txt.gz  # decompress
  ```
* **bzip2** → higher compression than gzip

  ```
  bzip2 file.txt
  bunzip2 file.txt.bz2
  ```

---

## 3. Zip and Unzip

* **zip** → compress multiple files/folders

  ```
  zip archive.zip file1.txt file2.txt folder/
  ```
* **unzip** → extract zip files

  ```
  unzip archive.zip
  ```

---

## 4. Practical Tips

* Use `tar` for Linux-native archiving, especially for directories.
* Use `gzip`/`bzip2` for compressing single large files.
* Use `zip`/`unzip` if sharing files with Windows systems.
* Always verify archive contents before extraction:

  ```
  tar -tf archive.tar
  ```

---

💡 **Hands-On Practice:**

1. Create a folder called `backup_test` and add 3 files inside.
2. Create an archive: `tar -cvf backup.tar backup_test/`
3. Compress it with gzip: `tar -czvf backup.tar.gz backup_test/`
4. List archive contents without extracting: `tar -tzvf backup.tar.gz`
5. Extract the archive to a new folder: `tar -xzvf backup.tar.gz -C extracted/`
6. Compress a single file with gzip: `gzip file1.txt` → then decompress: `gunzip file1.txt.gz`
7. Create a zip archive for Windows: `zip backup.zip file1.txt file2.txt` → unzip it: `unzip backup.zip`

---


# 🌐 Lecture: Networking Basics in Linux

Networking is crucial in Linux, especially for **cybersecurity, system administration, and penetration testing**. Linux provides several commands to view, test, and manage network interfaces and connections.

---

## 1. Check IP Address

* **ifconfig** → displays network interfaces (older systems, may need `sudo apt install net-tools`)

  ```
  ifconfig
  ```
* **ip addr** → modern alternative to `ifconfig`

  ```
  ip addr show
  ```
* Identify IP address, subnet mask, and interface name (e.g., `eth0`, `wlan0`).

---

## 2. Test Connectivity

* **ping** → check connectivity to another host

  ```
  ping google.com
  ping 192.168.1.1
  ```

* Use `Ctrl+C` to stop ping.

* **curl / wget** → fetch content from a URL

  ```
  curl http://example.com
  wget http://example.com/file.txt
  ```

---

## 3. DNS & Hostname

* **nslookup** → query DNS

  ```
  nslookup google.com
  ```
* **dig** → advanced DNS lookup (may need install: `sudo apt install dnsutils`)

  ```
  dig google.com
  ```
* **host** → quick hostname resolution

  ```
  host google.com
  ```

---

## 4. Network Connections

* **netstat** → view active connections (older, may need install)

  ```
  netstat -tulnp
  ```
* **ss** → modern replacement for `netstat`

  ```
  ss -tulnp
  ```
* **lsof -i** → show processes using network ports

---

## 5. Firewall Basics

* **ufw** → uncomplicated firewall (Ubuntu/Kali)

  * Check status: `sudo ufw status`
  * Enable firewall: `sudo ufw enable`
  * Allow port: `sudo ufw allow 22`

---

## 6. Practical Tips

* Always check your IP and interface: `ip addr show`
* Test connectivity to both internal hosts and external websites with `ping`.
* Monitor open ports and active connections regularly.
* Use firewalls to restrict unnecessary access.

---

💡 **Hands-On Practice:**

1. Display your IP addresses: `ip addr show`
2. Ping Google: `ping google.com`
3. Lookup DNS info: `nslookup google.com`
4. Check open ports and listening services: `ss -tulnp`
5. Enable firewall and allow SSH port 22:

   ```
   sudo ufw enable
   sudo ufw allow 22
   sudo ufw status
   ```
6. Use `curl` to fetch the homepage of a website:

   ```
   curl http://example.com
   ```

---


# 📊 Lecture: Logs & Monitoring in Kali Linux

Monitoring logs is crucial for **system administration, cybersecurity, and troubleshooting**. Kali Linux uses **systemd journals** instead of traditional flat log files (`syslog`, `messages`) for system and authentication logs. Service-specific logs are still stored in `/var/log/`.

---

## 1. System Logs: Using `journalctl`

* `journalctl` reads logs from the **systemd journal**, which replaces `syslog` in Kali.

**Common Commands:**

| Command                           | Purpose                                        |                                  |
| --------------------------------- | ---------------------------------------------- | -------------------------------- |
| `sudo journalctl`                 | View all system logs                           |                                  |
| `sudo journalctl -b`              | Show logs from the current boot                |                                  |
| `sudo journalctl --since today`   | Logs from today                                |                                  |
| `sudo journalctl -f`              | Follow logs in real-time (like `tail -f`)      |                                  |
| `sudo journalctl -u service_name` | View logs for a specific service (e.g., `ssh`) |                                  |
| `sudo journalctl _COMM=sshd`      | Show SSH daemon logs                           |                                  |
| \`sudo journalctl \_COMM=sshd     | grep "Failed"\`                                | Filter failed SSH login attempts |

---

## 2. Authentication & Login Monitoring

* Kali tracks authentication and login attempts in the **journal** instead of `auth.log`.
* Useful commands:

```bash
sudo journalctl _COMM=sshd         # View SSH login attempts
sudo journalctl _COMM=sshd | grep "Failed"  # Failed login attempts
sudo journalctl _COMM=sshd | grep "Accepted" # Successful logins
```

---

## 3. Service & Application Logs

* `/var/log/` contains logs for **installed services and applications**. Your Kali system has:

  * `nginx/` → web server logs
  * `apache2/` → Apache logs
  * `postgresql/` → database logs
  * `redis/` → Redis database logs
  * `samba/` → file sharing logs
  * `wazuh-install.log` → Wazuh installation logs
  * `mosquitto/` → MQTT broker logs
  * `macchanger.log` → MAC address change logs
  * `Xorg.0.log` → graphical interface logs
  * `dpkg.log` → package installation history

**Commands to interact with service logs:**

```bash
sudo tail -f /var/log/nginx/error.log       # Monitor Nginx errors in real-time
sudo less /var/log/postgresql/postgresql-*.log  # Scroll PostgreSQL logs
sudo grep "error" /var/log/redis/redis-server.log  # Search Redis errors
```

---

## 4. Monitoring System Resources

Even though `dmesg` isn’t available, you can monitor your system using other commands:

| Command            | Purpose                                                          |
| ------------------ | ---------------------------------------------------------------- |
| `top` or `htop`    | Monitor running processes, CPU & memory usage                    |
| `uptime`           | System running time and load averages                            |
| `df -h`            | Disk usage per filesystem                                        |
| `du -h <file/dir>` | Size of files or directories                                     |
| `free -h`          | Memory usage                                                     |
| `vmstat`           | CPU and memory statistics                                        |
| `iostat`           | CPU and disk I/O stats (install with `sudo apt install sysstat`) |

---

## 5. Practical Tips for Kali Logs

1. **Use `journalctl` as your main tool** for system and authentication logs.
2. **Service logs** in `/var/log/` are checked when troubleshooting specific applications.
3. **Use `grep` to filter logs** for errors, failed logins, or denied access.
4. **Follow logs in real-time** using `sudo journalctl -f` or `tail -f` for service logs.
5. **Check system boot logs**:

```bash
sudo journalctl -b
```

---

## 6. Hands-On Practice (Kali-Specific)

1. Navigate `/var/log` and list logs:

```bash
cd /var/log
ls
```

2. Monitor system logs live:

```bash
sudo journalctl -f
```

3. Check SSH login attempts:

```bash
sudo journalctl _COMM=sshd
sudo journalctl _COMM=sshd | grep "Failed"
sudo journalctl _COMM=sshd | grep "Accepted"
```

4. Monitor service logs (e.g., nginx, PostgreSQL):

```bash
sudo tail -f /var/log/nginx/error.log
sudo less /var/log/postgresql/postgresql-*.log
```

5. Explore package installation history:

```bash
less dpkg.log
```

6. Monitor system resources:

```bash
top
free -h
df -h
```


---

# 🖥️ Lecture: Shell Scripting in Linux

Shell scripting allows you to **automate tasks, execute commands, and build small programs** directly in the Linux shell. For cybersecurity professionals, scripting is essential for automating scans, log analysis, and repetitive tasks.

---

## 1. What is a Shell Script?

* A **shell script** is a file containing a sequence of commands for the shell to execute.
* Typically stored with a `.sh` extension.
* Common shells: `bash` (Bourne Again Shell), `sh`, `zsh`, `ksh`.

---

## 2. Creating a Shell Script

1. Create a file:

```bash
nano myscript.sh
```

2. Start with the **shebang** to specify the shell:

```bash
#!/bin/bash
```

3. Add commands inside:

```bash
#!/bin/bash
echo "Hello, this is my first script!"
date
```

4. Save and exit (`Ctrl+O`, `Enter`, `Ctrl+X`).

---

## 3. Make the Script Executable

```bash
chmod +x myscript.sh
```

Run the script:

```bash
./myscript.sh
```

Or run with the shell explicitly:

```bash
bash myscript.sh
```

---

## 4. Variables in Shell Scripting

* Assign a value:

```bash
name="Abdul"
echo "Hello $name"
```

* Read user input:

```bash
read -p "Enter your name: " user
echo "Hello $user"
```

* Environment variables:

```bash
echo $HOME
echo $USER
```

---

## 5. Conditional Statements

```bash
#!/bin/bash
read -p "Enter a number: " num
if [ $num -gt 10 ]; then
    echo "Number is greater than 10"
else
    echo "Number is 10 or less"
fi
```

---

## 6. Loops

* **For loop:**

```bash
for i in 1 2 3 4 5; do
    echo "Number $i"
done
```

* **While loop:**

```bash
count=1
while [ $count -le 5 ]; do
    echo "Count $count"
    ((count++))
done
```

---

## 7. Practical Tips

1. Always start with `#!/bin/bash` for bash scripts.
2. Use comments with `#` to explain your code.
3. Test commands in the terminal before adding them to the script.
4. Redirect output for logs:

```bash
echo "Task complete" >> ~/script.log
```

---

## 8. Hands-On Practice

1. Create a script `checkip.sh` that shows your IP:

```bash
#!/bin/bash
echo "Your IP address is:"
ip addr show | grep inet
```

2. Make it executable and run it:

```bash
chmod +x checkip.sh
./checkip.sh
```

3. Modify the script to log output to a file:

```bash
./checkip.sh >> ~/iplog.txt
```

4. Create a script to monitor disk usage every minute using a loop:

```bash
#!/bin/bash
while true; do
    df -h >> ~/disklog.txt
    sleep 60
done
```

---



