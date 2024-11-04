


# Viewing and Changing File Permissions in Linux

## Overview

Understanding file permissions is crucial for managing access to files and directories in Linux. This document outlines how to view and change file permissions effectively.

<iframe width="720" height="425"
src="https://www.youtube.com/embed/LnKoncbQBsM">
</iframe>

<iframe width="720" height="425"
src="https://www.youtube.com/embed/ngJG6Ix5FR4">
</iframe>

## Viewing Permissions

To view file permissions, use the `ls -l` command:

```bash
ls -l filename
```

The output displays permissions in the format:

```
-rwxr-xr--
```

- The first character indicates the file type (`-` for a regular file, `d` for a directory).
- The next three characters represent the owner's permissions, the next three represent the group's permissions, and the last three represent others' permissions.

### Example Usage

1. **View Permissions of a File**:
   ```bash
   ls -l myfile.txt
   ```

   ![](./img/permissions1.png)
   This command shows the detailed permissions for `myfile.txt`.

## Changing Permissions

To change file permissions, use the `chmod` command. Permissions can be set using either symbolic (rwx) or octal (numeric) notation.

### Symbolic Notation

```bash
chmod u+x filename   # Adds execute permission for the owner
chmod g-w filename   # Removes write permission for the group
chmod o=r filename   # Sets read permission for others
```

### Octal Notation

```bash
chmod 755 filename   # Sets rwxr-xr-x permissions
chmod 644 filename   # Sets rw-r--r-- permissions
```

### Example Usage

1. **Add Execute Permission for Owner**:
   ```bash
   chmod u+x myscript.sh
   ```

   This command allows the owner of `myscript.sh` to execute the script.

2. **Remove Write Permission from Group**:
   ```bash
   chmod g-w myfile.txt
   ```

   This command removes write access from the group for `myfile.txt`.

3. **Set Permissions Using Octal Notation**:
   ```bash
   chmod 755 mydirectory
   ```

   This sets `mydirectory` to `rwxr-xr-x`, allowing full access for the owner and read-execute access for the group and others.

## Output Details

The `ls -l` output provides key information about file permissions. Here’s an example with explanations:

```plaintext
-rwxr-xr-- 1 user group 4096 Nov 4 10:00 myfile.txt
```

- **`-rwxr-xr--`**: The permission string.
- **`1`**: The number of links to the file.
- **`user`**: The owner of the file.
- **`group`**: The group associated with the file.
- **`4096`**: The size of the file in bytes.
- **`Nov 4 10:00`**: The date and time of the last modification.
- **`myfile.txt`**: The name of the file.

## Practice Exercises

1. List the permissions of a specific file.
2. Change permissions to allow the owner to read and write but not execute.
3. Set a directory to be accessible only by the owner.
4. Use octal notation to set a file's permissions to read-only for everyone except the owner.

## Additional Resources

- [Linux Permissions Explained: A Beginner’s Guide to File Security Commands](https://www.r-bloggers.com/2024/10/linux-permissions-explained-a-beginners-guide-to-file-security-commands/)
- [Linux file permissions explained](https://www.redhat.com/en/blog/linux-file-permissions-explained)

