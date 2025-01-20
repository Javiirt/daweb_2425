### **Exercise 4.1: Exploring currently running processes**

#### **Enunciado:**
1. Find out the total number of processes currently running.
2. Identify the 10 most CPU-intensive processes and give a brief description of what each of them does.

#### **Respuestas:**
1. To find the total number of running processes, execute:
   ```bash
   ps aux | wc -l
   ```
   This command counts all lines returned by `ps aux`, each representing a running process.

2. To find the 10 most CPU-intensive processes, execute:
   ```bash
   ps aux --sort=-%cpu | head -n 11
   ```
   Example output:
   ```
   USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
   root       123  75.3  1.2 125000 5000 ?        R    12:00   0:15 some_daemon
   ```
   Descriptions of top processes:
   - **Process 1:** System process handling disk I/O.
   - **Process 2:** SSH daemon managing remote connections.
   - **Process 3:** Database engine performing a query.
   (Provide descriptions based on the `COMMAND` column and `man` pages.)

---

### **Exercise 4.2: Exploring network processes**

#### **Enunciado:**
1. Execute `nmap localhost`. Write down all processes returned and explain their purpose.

#### **Respuestas:**
1. To execute the scan, run:
   ```bash
   nmap localhost
   ```
   Example output:
   ```
   PORT   STATE SERVICE
   22/tcp open  ssh
   80/tcp open  http
   ```
   - **22/tcp (ssh):** Handles secure shell connections.
   - **80/tcp (http):** Manages web server traffic.

---

### **Exercise 4.3: Exploring UNIX signals**

#### **Enunciado:**
1. Execute `kill -l` and summarize the signals (numbers 1–9 and 5 more between 10–31).

#### **Respuestas:**
1. Execute the command:
   ```bash
   kill -l
   ```
   Signal summary:
   | **Number** | **Name**   | **Description**                  |
   |------------|------------|----------------------------------|
   | 1          | SIGHUP     | Hangup                           |
   | 2          | SIGINT     | Interrupt from keyboard          |
   | 3          | SIGQUIT    | Quit from keyboard               |
   | 9          | SIGKILL    | Kill signal                      |
   | 15         | SIGTERM    | Termination signal               |

---

### **Exercise 4.4: Processes and networking**

#### **Enunciado:**
1. Enable FTP and Telnet in `/etc/inetd.conf`. Restart `inetd`. Test with `ftp localhost` and `telnet localhost`.
2. Disable FTP in `/etc/inetd.conf`, restart `inetd`, and test.
3. What are SFTP and SSH? Why is Telnet discouraged in real-world usage?

#### **Respuestas:**
1. **Enable FTP and Telnet:**
   - Edit `/etc/inetd.conf`:
     ```bash
     sudo nano /etc/inetd.conf
     ```
     Uncomment lines for FTP and Telnet services.
   - Restart `inetd`:
     ```bash
     sudo kill -HUP $(pidof inetd)
     ```
   - Test FTP and Telnet:
     ```bash
     ftp localhost
     telnet localhost
     ```

2. **Disable FTP:**
   - Comment out the FTP line in `/etc/inetd.conf`.
   - Restart `inetd` and test again as above.

3. **SFTP and SSH:**
   - **SFTP:** Secure FTP using SSH for encrypted transfers.
   - **SSH:** Secure Shell for encrypted remote connections.
   - **Telnet:** Insecure protocol; data (including passwords) is transmitted in plain text.

---

### **Exercise 4.5: Optional Exercises**

#### **Enunciado:**
1. Combine `pidof` with `kill -HUP` to restart `inetd` in one command.
2. Can you FTP as root? Is it advisable? Why (or why not)?
3. From a Windows machine, FTP and Telnet to the Slackware VM.

#### **Respuestas:**
1. Restart `inetd` in one command:
   ```bash
   kill -HUP $(pidof inetd)
   ```

2. **FTP as root:**
   - Possible but not advisable due to high security risks. FTP transmits data unencrypted, exposing the root credentials.

3. **Windows FTP/Telnet:**
   - Use a Windows FTP/Telnet client to connect to the VM. Example:
     ```bash
     ftp <VM_IP_ADDRESS>
     telnet <VM_IP_ADDRESS>
     
