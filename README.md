
# Linux Learning Repository

Welcome to my Linux learning journey! This repository serves as my documentation as I explore the world of Linux. Each day, I'll be documenting new concepts, commands, and tips that I learn.

## Day 1: Introduction to Bash Commands

### Basic Commands

1. **`pwd` - Print Working Directory:**
   - Display the current working directory.

   ```bash
   pwd
   ```

2. **`ls` - List Files:**
   - List the files and directories in the current directory.

   ```bash
   ls
   ```

3. **`cd` - Change Directory:**
   - Move to a different directory.

   ```bash
   cd /path/to/directory
   ```

### File and Directory Operations

4. **`mkdir` - Make Directory:**
   - Create a new directory.

   ```bash
   mkdir new_directory
   ```

5. **`touch` - Create Empty File:**
   - Create a new empty file.

   ```bash
   touch new_file.txt
   ```

6. **`cp` - Copy:**
   - Copy files or directories.

   ```bash
   cp source_file destination
   ```

7. **`mv` - Move/Rename:**
   - Move files or directories, or rename them.

   ```bash
   mv old_name new_name
   ```

8. **`rm` - Remove:**
   - Delete files or directories. Be careful, as this operation is irreversible.

   ```bash
   rm file.txt
   ```

### File Content Manipulation

9. **`cat` - Concatenate and Display:**
   - Display the content of a file.

   ```bash
   cat filename.txt
   ```

10. **`echo` - Output:**
    - Print text to the terminal.

    ```bash
    echo "Hello, Linux!"
    ```

11. **`nano` - Simple Text Editor:**
    - Open a text file for editing.

    ```bash
    nano filename.txt  
    ```

### Miscellaneous Commands

12. **`man` - Manual Pages:**
    - Access the manual pages for a command to get detailed information.

    ```bash
    man ls
    ```

13. **`history` - Command History:**
    - Display a list of recently executed commands.

    ```bash
    history
    ```
## 1. User Creation

### Add a User
```bash
sudo adduser [username]
```

### Set Password for a User
```bash
sudo passwd [username]
```

## 2. User Modification

### Change User Password
```bash
passwd [username]
```

### Modify User Details
```bash
sudo usermod -c "New User Name" [username]
```

### Add User to a Group
```bash
sudo usermod -aG [group] [username]
```

### Remove User from a Group
```bash
sudo deluser [username] [group]
```

## 3. User Deletion

### Delete User
```bash
sudo deluser [username]
```

### Delete User and Home Directory
```bash
sudo deluser --remove-home [username]
```

## 4. User Information

### Display User Information
```bash
id [username]
```

### Display Logged-In Users
```bash
who
```

### Display Last Login Information
```bash
last [username]
```

## 5. Switching Users

### Switch to Another User
```bash
su [username]
```

### Switch to Root User
```bash
sudo su
```

## 6. Password Policies

### Lock User Account
```bash
sudo passwd -l [username]
```

### Unlock User Account
```bash
sudo passwd -u [username]
```

## 7. File Permissions

### Check File Ownership
```bash
ls -l [filename]
```

### Change File Ownership
```bash
sudo chown [username] [filename]
```

### Change File Permissions
```bash
chmod [permissions] [filename]
```

These commands provide a foundation for managing user accounts in a Linux/Unix system. User management is an essential part of system administration to ensure proper access control and security. Always refer to the manual pages (`man [command]`) for detailed information and options.
```
