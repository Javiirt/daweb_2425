# Linux Systems and Shell Scripting Exercises

## **Exercise 3.1: Creating an Executable Bash Script**

### **Enunciado**
1. Using `vi` (or another terminal text editor such as `emacs`), create a script called `test.sh` in your home directory with the following contents:
   ```bash
   #!/bin/bash
   clear
   echo "Hello World"
   ```
   
2. Make sure the script is executable, then run it by executing: `./test.sh`.

3. A student executed the following command:
   ```bash
   chmod 777 test.sh
   ```
   Explain why giving 777 permissions to a file is a bad idea.

### **Comandos Usados**
```bash
cd ~
vi test.sh
# Escribir el contenido del script en vi
echo -e "#!/bin/bash\nclear\necho \"Hello World\"" > test.sh
chmod +x test.sh
./test.sh
```

---

## **Exercise 3.2: Creating New Users**

### **Enunciado**
Create two new user accounts:
- Username: `bob`, Password: `bob`
- Username: `smith`, Password: `smith`

### **Comandos Usados**
```bash
useradd -d /home/bob bob
mkdir /home/bob
chown bob:bob /home/bob
passwd bob 

useradd -d /home/smith smith
mkdir /home/smith
chown smith:smith /home/smith
passwd smith 
```

---

## **Exercise 3.3: Creating a Shared Executable Script**

### **Enunciado**
1. Create a publicly readable and writable directory with the path `/home/ncs` and set the appropriate permissions.
2. Create a bash script in this directory called `hello.sh` which should print a message saying "Hello World".
3. Execute this script.
4. Note down the owner/group ownerships and the file permissions of this script.

### **Comandos Usados**
```bash
mkdir /home/ncs
chmod 777 /home/ncs

cd /home/ncs
echo -e "#!/bin/bash\necho \"Hello World\"" > hello.sh
chmod +x hello.sh
./hello.sh
ls -l hello.sh
```

---

## **Exercise 3.4: Accessing Files from Different User Accounts**

### **Enunciado**
#### Parte a) Log in as `bob`:
1. Navigate to the directory `/home/ncs`. What do you see in this directory?
2. Execute `./hello.sh`. Does it succeed? Why (not)?
3. Create a script called `bob.sh`, which should print the message "Hello this is Bob" when executed.
4. Execute `./bob.sh` and explain the result you get.

#### Parte b) Log in as `smith`:
1. Navigate to the directory `/home/ncs`. What do you see in this directory?
2. Execute `./hello.sh` and `./bob.sh`. Explain the results you get.

### **Comandos Usados**
```bash
# Parte a: Bob
su - bob
cd /home/ncs
ls
./hello.sh

echo -e "#!/bin/bash\necho \"Hello this is Bob\"" > bob.sh
chmod +x bob.sh
./bob.sh

# Parte b: Smith
su - smith
cd /home/ncs
ls
./hello.sh
./bob.sh
```

---

## **Exercise 3.5: Optional Exercises**

### **Enunciado**
1. Create a group called `sysadmins`, and add `bob` and `smith` as members. Change the group owner of `/home/ncs`, `/home/ncs/hello.sh`, and `/home/ncs/bob.sh` to this group. Verify if both `bob` and `smith` can execute both scripts now.
2. Disable `smith`'s user account without deleting it or its files.

### **Comandos Usados**
```bash

groupadd sysadmins
usermod -aG sysadmins bob
usermod -aG sysadmins smith
chown :sysadmins /home/ncs
chown :sysadmins /home/ncs/hello.sh
chown :sysadmins /home/ncs/bob.sh
chmod 770 /home/ncs /home/ncs/hello.sh /home/ncs/bob.sh

# Verificar acceso como bob y smith
su - bob
cd /home/ncs
./hello.sh
./bob.sh

su - smith
cd /home/ncs
./hello.sh
./bob.sh

# Deshabilitar smith
usermod -L smith