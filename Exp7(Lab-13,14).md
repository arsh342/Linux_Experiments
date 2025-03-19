# Lab 13 & 14: File Ownership and Permissions in Linux

## Objective
The objective of this lab is to understand and implement file ownership and permission management in Linux using the `chown` and `chmod` commands along with their various options.

---

## Commands and Concepts Used

### 1. File Ownership Management with `chown`

The `chown` command is used to change the owner and/or group of files and directories.

#### a. **Basic `chown` Usage**

##### Example 1: Change File Owner
```bash
sudo chown operator1 testfile.txt
```

#### Screenshot:
![image](https://github.com/user-attachments/assets/5180c4bf-7b80-4789-9651-bd4b85689a7e)


##### Example 2: Verify Ownership Change
```bash
ls -l testfile.txt
```

#### Screenshot:
![image](https://github.com/user-attachments/assets/05b695b7-9169-4722-bc48-3679d2107961)


---

#### b. **Changing Both Owner and Group**

##### Example: Change Owner and Group Simultaneously
```bash
sudo chown operator1:operator2 testfile.txt
```

#### Screenshot:
![image](https://github.com/user-attachments/assets/36b1d0ba-44f4-436c-8ad6-56a1715e78ed)


---

#### c. **Using the `-R` Option for Recursive Changes**

##### Example: Change Ownership Recursively for a Directory
```bash
sudo chown -R operator1:operator1 testdirectory/
```

#### Screenshot:
![image](https://github.com/user-attachments/assets/1aa4aa0f-770b-4860-abf8-7c12dc017223)


---

#### d. **Using the Reference Option**

##### Example: Copy Ownership from Reference File
```bash
sudo chown --reference=referencefile.txt targetfile.txt
```

#### Screenshot:
![image](https://github.com/user-attachments/assets/1d6b0bbc-ab54-4c4c-8911-ba7bdffa9859)


---

### 2. File Permissions Management with `chmod`

The `chmod` command is used to change file access permissions for owner, group, and others.

#### a. **Numeric Mode (Octal) Permission Setting**

##### Example 1: Set Read, Write, Execute Permissions for Owner Only
```bash
chmod 700 testfile.txt
```
This sets read (4), write (2), and execute (1) permissions for the owner (7), and no permissions for group or others (0).

#### Screenshot:
![image](https://github.com/user-attachments/assets/53c97a62-c501-4624-8c71-f11d29afc4f6)


##### Example 2: Set Read and Write for Owner, Read for Group and Others
```bash
chmod 644 testfile.txt
```
This sets read and write permissions (6) for the owner, and read-only permissions (4) for both group and others.

#### Screenshot:
![image](https://github.com/user-attachments/assets/f44d734f-9b27-4e48-9101-face963bbfdb)


---

#### b. **Symbolic Mode Permission Setting**

##### Example 1: Add Execute Permission for Owner
```bash
chmod u+x testfile.txt
```

#### Screenshot:
![image](https://github.com/user-attachments/assets/f877ae16-302b-4e59-ad33-6fe14e2fe4ca)


##### Example 2: Remove Write Permission for Group
```bash
chmod g-w testfile.txt
```

#### Screenshot:
![image](https://github.com/user-attachments/assets/50fc2288-1e1d-4a20-b587-0ae20ffa8600)


##### Example 3: Add Read Permission for Others
```bash
chmod o+r testfile.txt
```

#### Screenshot:
![image](https://github.com/user-attachments/assets/58800496-f8eb-4c47-9a74-d378d6fce47e)


##### Example 4: Set Multiple Permissions at Once
```bash
chmod u+rwx,g+rx,o+r testfile.txt
```

#### Screenshot:
![image](https://github.com/user-attachments/assets/52bed58c-b34e-43cf-944a-039550631cff)


---

#### c. **Using the `-R` Option for Recursive Changes**

##### Example: Change Permissions Recursively
```bash
chmod -R 755 testdirectory/
```

#### Screenshot:
![image](https://github.com/user-attachments/assets/081dffcb-6df9-46eb-8fea-5cc9b13d8892)


---

#### d. **Special Permissions**

##### Example 1: Set SUID Permission
```bash
chmod u+s testfile.txt
```
SUID (Set User ID) allows a user to execute a file with the permissions of the file owner.

#### Screenshot:
![image](https://github.com/user-attachments/assets/ce9241f2-07ca-4d77-ab9a-bb0e46ab44f5)


##### Example 2: Set SGID Permission
```bash
chmod g+s testdirectory/
```
SGID (Set Group ID) on a directory causes new files created in the directory to inherit the group of the directory.

#### Screenshot:
![image](https://github.com/user-attachments/assets/cc38d7b4-c3c3-4a11-aae0-a26b6872f057)


##### Example 3: Set Sticky Bit
```bash
chmod +t testdirectory/
```
The sticky bit on a directory prevents users from deleting files owned by other users.

#### Screenshot:
![image](https://github.com/user-attachments/assets/4c5e22ea-f005-44eb-8810-c26545e2b8ac)


---

### 3. Combining `chown` and `chmod`

##### Example: Change Ownership and Permissions in Sequence
```bash
sudo chown operator1:operator2 testfile.txt
chmod 750 testfile.txt
```

#### Screenshot:
![image](https://github.com/user-attachments/assets/dd1ceb6f-c2c7-46d8-a475-4526a0667eac)


---

### 4. Using Advanced Options

#### a. **Using the `--preserve-root` Option**

The `--preserve-root` option prevents recursive operations on `/` (root directory).

```bash
sudo chmod --preserve-root -R 777 /directory
```

#### Screenshot:
![image](https://github.com/user-attachments/assets/40a69bad-5c63-40a6-93ed-f6467b67137a)


---

#### b. **Using the `-v` (Verbose) Option**

The `-v` option outputs a diagnostic message for every file processed.

```bash
chmod -v 644 testfile.txt
```

#### Screenshot:
![image](https://github.com/user-attachments/assets/fa22bdcf-5ff9-4f90-aba0-b88cc32ad71a)


---

#### c. **Using the `-c` (Changes) Option**

The `-c` option reports only when a change is made.

```bash
chmod -c 644 testfile.txt
```

#### Screenshot:
![image](https://github.com/user-attachments/assets/5e372c40-714f-436e-bede-b58e86e7cff6)


---

## Permission and Ownership Verification

### 1. **Verifying Permissions and Ownership**

#### Example: Using `ls -l` to View Permissions and Ownership
```bash
ls -l testfile.txt
```

#### Screenshot:
![image](https://github.com/user-attachments/assets/e3747001-ae3f-4b80-9cb0-a8c85f2d148d)


#### Understanding the Output:
- First character: File type (- for regular file, d for directory)
- Next three characters: Owner permissions (r=read, w=write, x=execute)
- Next three characters: Group permissions
- Last three characters: Others permissions
- Username and group name show ownership

---

## Permission Calculator Reference

### Numeric Permissions

| Number | Permission Type | Symbol |
|--------|-----------------|--------|
| 0      | No Permission   | ---    |
| 1      | Execute         | --x    |
| 2      | Write           | -w-    |
| 3      | Write + Execute | -wx    |
| 4      | Read            | r--    |
| 5      | Read + Execute  | r-x    |
| 6      | Read + Write    | rw-    |
| 7      | Read + Write + Execute | rwx |

---

## Conclusion

In this lab, you learned how to:
1. Change file and directory ownership using the `chown` command
2. Modify file and directory permissions using the `chmod` command
3. Apply recursive changes to directories and their contents
4. Set special permissions (SUID, SGID, and Sticky Bit)
5. Verify permission and ownership changes

These skills are essential for managing file security, controlling access to resources, and maintaining a secure Linux environment.
