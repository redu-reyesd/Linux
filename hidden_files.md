
# Listing Hidden Files in Linux

## Overview

In Linux, files that start with a dot (.) are considered hidden. This document explains how to list hidden files in a directory.

<iframe width="720" height="425"
src="https://www.youtube.com/embed/tLU6RDqf-7I">
</iframe>

<iframe width="720" height="425"
src="https://www.youtube.com/embed/Bt1mAB1PDC4">
</iframe>

## Listing Hidden Files

To list hidden files in a directory, use the `-a` option with the `ls` command:

```bash
ls -a
```

This command will display all files, including hidden ones.

### Example Usage

1. **List All Files in the Current Directory, Including Hidden Ones**:
   ```bash
   ls -a
   ```

   This command shows all files, including those that are hidden (starting with a dot).

2. **For a More Detailed View, Combine with the `-l` Option**:
   ```bash
   ls -la
   ```

   This command displays a detailed list of all files, including hidden ones, showing permissions, number of links, owner, group, size, and last modified date.

## Output Details

The output of `ls -la` might look like this:

```plaintext
drwxr-xr-x  5 user group 4096 Nov 4 10:00 .
drwxr-xr-x  3 user group 4096 Nov 4 09:00 ..
-rw-r--r--  1 user group  123 Nov 4 10:00 .hiddenfile
-rw-r--r--  1 user group  456 Nov 4 10:00 regularfile.txt
```

- **`.`**: Represents the current directory.
- **`..`**: Represents the parent directory.
- **`.hiddenfile`**: A hidden file in the current directory.
- Other files will be listed normally.

## Practice Exercises

1. List all files, including hidden ones, in your home directory.
2. Use the `ls -la` command to view detailed information about all files in a specific directory.
3. Create a hidden file in your directory and verify it is listed with `ls -a`.

## Additional Resources

- [The Hidden Files in Your Linux Home Directory, Explained](https://www.howtogeek.com/the-hidden-files-in-your-linux-home-directory-explained/#:~:text=On%20Linux%E2%80%94and%20similar%20OSes,know%20them%20as%20%22dotfiles.%22)
- [Linux Command Line Cheat Sheet](https://www.geeksforgeeks.org/linux-commands-cheat-sheet/)

