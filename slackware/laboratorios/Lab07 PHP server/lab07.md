# Apache HTTP Server and PHP Lab

## Exercise 7.1 Configuring Apache

1. **What are the purpose of lines starting with # in `/etc/httpd/httpd.conf`?**  
   These are comments, used to document the configuration file. They provide instructions or information and are ignored by the system.

2. **Default values of `ServerName` and `DocumentRoot`:**  
   - **ServerName**: `localhost` (or similar, based on configuration). It specifies the hostname used for the server.  
   - **DocumentRoot**: `/srv/httpd/htdocs` (or similar). This is the directory where the web server looks for files to serve.  

3. **Uncommenting `Include /etc/httpd/mod_php.conf`:**  
   This enables PHP support for the Apache server by including the configuration file for the PHP module.

---

## Exercise 7.2 Running Apache

1. **Why do you need to restart `httpd` if you make changes to the configuration?**  
   Restarting ensures that changes in the configuration file are applied to the running server process.

2. **About `ps aux | grep httpd`:**  
   a) **What the commands do:**  
      - `ps aux`: Lists all running processes.  
      - `grep httpd`: Filters the output to show only lines containing "httpd".  
      - `|`: Pipes the output of one command to another.  
      Together, the command displays all running `httpd` processes.  
  
   b) **Expected output:**  
      - If running: Information about the `httpd` processes.  
      - If not running: No results or only the `grep` process itself.

3. **Finding the parent `httpd` process ID:**  
   By running `ps axl | egrep "httpd|PPID"`, locate the **PPID** column for the parent `httpd` process.

---

## Exercise 7.3 Creating HTML Files

1. **What is special about `index.htm` and `index.html` files?**  
   They are default files served by the web server when no specific file is requested.

2. **Permissions and ownership of `index.html`:**  
   - Permissions: Typically `rw-r--r--`.  
   - Owner/Group: Owned by the user and group under which Apache runs.

3. **Creating `test.html`:**  
   - **Source code:**  
     ```html
     <html>
     <head><title>NSE Apache Lab</title></head>
     <body>
     <h1>This is the NSE Apache Lab test page</h1>
     <p>Under construction!</p>
     </body>
     </html>
     ```  
   - **Expected view:** A page with the title "NSE Apache Lab," a header "This is the NSE Apache Lab test page," and a paragraph saying "Under construction!"

---

## Exercise 7.4 Viewing HTML Files Using a Terminal Interface

1. **Difference between CLI and GUI:**  
   - CLI: Command-Line Interface, text-based and operated via commands.  
   - GUI: Graphical User Interface, operated through visual elements like icons and buttons.

2. **What is special about the IP address `127.0.0.1`?**  
   It is the loopback address, representing the local machine.

3. **Viewing `test.html` using `lynx`:**  
   Command: `lynx 127.0.0.1/test.html`.  
   If the file does not load, ensure `httpd` is running, the file is in the correct location, and permissions are set properly.

4. **Optional:** Open the file from a Windows host by navigating to `http://[VM_IP]/test.html`.

---

## Exercise 7.5 Creating and Viewing PHP Files

1. **What does `phpinfo();` do?**  
   It displays information about the PHP environment, including configuration and loaded modules.

2. **Viewing `nse.php` using `lynx`:**  
   Command: `lynx 127.0.0.1/nse.php`.  
   If the source code appears instead, ensure PHP is enabled in `httpd.conf` and restart `httpd`.

---

## Exercise 7.6 Exploring and Adding an Entry to the Hosts File

1. **Adding an entry to `/etc/hosts`:**  
   - Add: `127.0.0.1 www.example.com`  
   - Resulting file:  
     ```
     # For loopbacking 127.0.0.1 localhost
     # This next entry is technically wrong, but good enough to get TCP/IP apps
     # to quit complaining that they can’t verify the hostname on a loopback-only
     # Linux box
     127.0.0.1 darkstar.example.net darkstar
     127.0.0.1 www.example.com
     # End of hosts.
     ```

2. **Testing the hosts file:**  
   Command: `lynx www.example.com`. Verify it resolves correctly.

---

## Exercise 7.7 Optional Exercises

1. **`index.php` vs. `index.html`:**  
   By default, `index.html` is loaded first. To change this, modify the `DirectoryIndex` setting in `httpd.conf` to prioritize `index.php`.

2. **Password-protecting `DocumentRoot`:**  
   a) Create a password file: `htpasswd -c /var/www/.htpasswd user`  
   b) Edit `httpd.conf` to include:  
      ```
      AuthType Basic
      AuthName "Authorization required"
      AuthUserFile /var/www/.htpasswd
      Require valid-user
      ```  
   c) Restart `httpd`. Use `lynx 127.0.0.1` to test the authentication prompt.

---

