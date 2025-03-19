# Lab 9 & 10: Process Management and Software Management in Linux

## Objective
The objective of this lab is to learn how to manage processes using commands like `ps`, `top`, and `kill`, and to understand how to install, update, and remove software using the `apt-get` command in Linux.

---

## Commands and Concepts Used

### 1. Process Management Commands

#### a. **`ps` Command**
The `ps` command is used to display information about active processes.

##### Example 1: Display Processes for the Current User
```bash
ps
```

#### Screenshot:
![image](https://github.com/user-attachments/assets/4f4425f3-a40a-4141-a5c9-c4bdfd870f55)


##### Example 2: Display All Processes
```bash
ps -e
```

#### Screenshot:
![image](https://github.com/user-attachments/assets/9b890aaf-71ba-4dd0-a33e-f939da8e1adb)


##### Example 3: Display Processes in Full Format
```bash
ps -ef
```

#### Screenshot:
![image](https://github.com/user-attachments/assets/2b23d7a5-a3ac-4808-becd-40864de1e5f0)


---

#### b. **`top` Command**
The `top` command provides a real-time view of system processes.

##### Example: Run `top` to Monitor Processes
```bash
top
```

#### Screenshot:
![image](https://github.com/user-attachments/assets/527b0ee8-9fa9-4efa-83c0-69425b955548)


---

#### c. **`kill` Command**
The `kill` command is used to terminate processes.

##### Example 1: Terminate a Process by PID
First, find the PID of the process using `ps` or `top`, then terminate it:
```bash
kill <PID>
```

#### Screenshot:
![image](https://github.com/user-attachments/assets/bf45bdd1-ed97-43f7-9197-6d93cb18d9e3)


##### Example 2: Forcefully Terminate a Process
```bash
kill -9 <PID>
```

#### Screenshot:
![image](https://github.com/user-attachments/assets/b5f3a844-e314-457c-897f-ddc001f69e9e)


---

### 2. Software Management with `apt-get`

#### a. **Installing Software**
To install a software package, use the `apt-get install` command.

##### Example: Install `htop`
```bash
sudo apt-get install htop
```

#### Screenshot:
![image](https://github.com/user-attachments/assets/dee79d8b-71f4-4c08-a760-f212aff93da4)


---

#### b. **Updating Software**
To update the list of available packages and their versions, use:
```bash
sudo apt-get update
```

#### Screenshot:
![image](https://github.com/user-attachments/assets/b34fa92b-6399-4d90-afc2-ddde4e2bfaeb)


To upgrade installed packages to their latest versions, use:
```bash
sudo apt-get upgrade
```

#### Screenshot:
![image](https://github.com/user-attachments/assets/989be8f7-e81d-49ba-a570-8fcddd41f87c)


---

#### c. **Removing Software**
To remove a software package, use the `apt-get remove` command.

##### Example: Remove `htop`
```bash
sudo apt-get remove htop
```

#### Screenshot:
![image](https://github.com/user-attachments/assets/4a68a83b-9105-4499-9af4-1f544d0edbd3)


To remove the package along with its configuration files, use:
```bash
sudo apt-get purge htop
```

#### Screenshot:
![image](https://github.com/user-attachments/assets/4487019b-2c8f-4d9a-b7ae-322fd09bb4f7)


---

### 3. Verifying Software Installation and Removal
To verify if a package is installed, use the `dpkg` command:
```bash
dpkg -l | grep htop
```

#### Screenshot:
![image](https://github.com/user-attachments/assets/a6647d27-51ba-40dd-997c-5cad7e3a17c7)


---

## Conclusion
In this lab, you learned how to:
1. Manage processes using `ps`, `top`, and `kill`.
2. Install, update, and remove software using `apt-get`.

These skills are essential for system administration, process monitoring, and software management in Linux.
