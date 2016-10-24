# space_is_money
Tools to manage disk space usage on *NIX systems

## How much space is available
```bash
df -h
```

## Space taken by files or folders
```bash
du -sch /PATH/TO/FOLDER

# Example for current folder:
du -sch *

# List by file size (if `sort -h` is available on your system):
du -sch * | sort -h
```

You can add an alias `sp='du -sch * | sort -h` in your `~/.bashrc` file.

## Finding the mother load with ncdu
**ncdu** is a useful program to manage disk space usage on \*NIX systems.
You can use it to find what folder take the most space or contains the
highest number of files. When using **ncdu**, you can navigate folders in
real time while tracking space usage. When you locate a folder that takes
too much space, for example because it contains a high number of big,
un-compressed files, you can switch to **bash** temporarily and solve the
problem before coming back to **ncdu**.

The following sub-sections describe how to install and use **ncdu**.

### Installation

### Using ncdu
