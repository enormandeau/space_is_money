# Space is Money
Tools to manage disk space usage on \*NIX systems, including the powerfull
**ncdu**, and how to use them.

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
**ncdu** can be downloaded from here : [https://dev.yorhel.nl/ncdu](https://dev.yorhel.nl/ncdu)

To install on your computer it, run the following (you may need to adapt for the version number):
```bash
tar xvfz ncdu-1.12.tar.gz
cd ncdu-1.12
./configure
make
sudo make install
```

If you need to install on a server where you do not have administrative rights,
it may be easier to ask the system admin to do it for you.


### Using ncdu
To launch **ncdu**, open a bash terminal and move to a folder where you want to learn more about
disk space usage, then simply type `ncdu` in the terminal. You will be presented with a window that
looks like this:

```
ncdu 1.12 ~ Use the arrow keys to navigate, press ? for help       
--- /home/username/Desktop/ncdu-1.12 ------------------------------
  196.0 KiB [##########]  configure                                
  184.0 KiB [######### ] /src
   52.0 KiB [##        ]  aclocal.m4
   36.0 KiB [#         ] /deps
   32.0 KiB [#         ]  Makefile.in
   24.0 KiB [#         ]  depcomp
   16.0 KiB [          ]  ncdu.1
   16.0 KiB [          ]  install-sh
   16.0 KiB [          ] /doc
    8.0 KiB [          ]  compile
    8.0 KiB [          ]  missing
    8.0 KiB [          ]  ChangeLog
    4.0 KiB [          ]  config.h.in
    4.0 KiB [          ]  configure.ac
    4.0 KiB [          ]  README
    4.0 KiB [          ]  COPYING
    4.0 KiB [          ]  Makefile.am

 Total disk usage: 620.0 KiB  Apparent size: 529.3 KiB  Items: 46  
```

You can navigate the folders and files by using either the arrow keys or,
for the true 1337 among you, the **vim** movement keys. In the example screen
presented above, pressing `down` and then `right` would bring us in the **src**
foldler.

#### Where the big files and folders are
By default, **ncdu** shows the biggest folder or file at the top and then the
rest by decreasing order of disk space used. This is very useful to find what
files and folders are using the most space. In our example, we can see that the
**configure** (196.0 KiB) and **src** (184.0 Kib) folders take up most of the
space taken by the whole folder (620.0 KiB, seen at the bottom).

#### Displaying more/different information
You can change what information is displayed in the **ncdu** window with the following
keys:
- **g**: Change/remove the file size information style. Press multiple times to cycle.
- **c**: Show/hide the number of files in folders.
- **t**: Put folders before files. Press again to cancel.
- **a**: Toggle between apparent size and disk usage.
- **e**:  Show/hide hidden or excluded files.
- **i**:  Show information about selected item.
- **r**:  Recalculate the current directory.

#### Sorting
You can sort the folders and files in a different order than the default (by file
size) by using the following keys:
- **s**: file size (default). Press again to reverse order.
- **n**: file name. Press again to reverse order.
- **C**: number of items. Press again to reverse order.

#### How to find the nest of files
Sometimes, we run programs that create crazy amounts of files. By pressing **c** to
show the file number by folder ane **C** to sort by number of files, we can locate
these problematic folders and take appropriate action, whether to delete them or
compress them into an archive.

#### Switching to bash
Once we have identified a problematic folder, **ncdu** makes it easy to jump right in
that folder to solve the problem. Instead of copying the path, exiting **ncdu**, moving
into the folder of interest, taking action and then opening **ncdu** again, we can
switch to a bash session by simply pressing the `b` key. The present working directory
will be the directory we were visualizing in the **ncdu** window. We can then remove,
compress or archive files and folders as needed. When we are done, pressing `Ctrl-D` or
typing `exit` will bring us back to our **ncdu** session.

### Getting help

#### Interactive help
During a session, you can press the question mark (`?`) key to open the interactive
help menu. It is quite simple and looks like this:

```
ncdu 1.12 ~ Use the arrow keys to navigate, press ? for help       
--- /home/labolb/Desktop/ncdu-1.12 --------------------------------
  196.0 KiB [##########]  configure
  1┌───ncdu help─────────────────1:Keys───2:Format───3:About──┐    
   │                                                          │
   │       up, k  Move cursor up                              │
   │     down, j  Move cursor down                            │
   │ right/enter  Open selected directory                     │
   │  left, <, h  Open parent directory                       │
   │           n  Sort by name (ascending/descending)         │
   │           s  Sort by size (ascending/descending)         │
   │           C  Sort by items (ascending/descending)        │
   │           d  Delete selected file or directory           │
   │           t  Toggle dirs before files when sorting       │
   │           g  Show percentage and/or graph                │
   │                        -- more --                        │
   │                                         Press q to close │
   └──────────────────────────────────────────────────────────┘
    4.0 KiB [          ]  Makefile.am

 Total disk usage: 620.0 KiB  Apparent size: 529.3 KiB  Items: 46  
 ```
 
 You can navigate the 3 subsections (1:Keys, 2:Format and 3:About) with the `left` and
 `right` keys and scroll up and down with, you guessed it, the `up` and `down` arrows.
 The **vim** keys work here too. To quit the help menu, simply press the `q` key.

#### The Manual
**ncdu**'s manual can be found here: [https://dev.yorhel.nl/ncdu/man](https://dev.yorhel.nl/ncdu/man)
but, frankly, pretty much all you need to know is covered here or in the interactive help menu.

## License
This work is licensed under the Creative Commons Attribution-ShareAlike 4.0 International License. To view a copy of this license, visit http://creativecommons.org/licenses/by-sa/4.0/.
