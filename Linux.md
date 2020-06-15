# Linux

[Back to contents](README.md)

## File system

### inode

The **inode** is a data structure in a Unix-style file system that describes a file-system object such as a file or a directory. Each inode stores the attributes and disk block locations of the object's data. File-system object attributes may include metadata (times of last change, access, modification), as well as owner and permission data.

Directories are lists of names assigned to inodes. A directory contains an entry for itself, its parent, and each of its children.

### Links

**Soft Link** (also know as **Symbolic Link** or **Symlink**) is a special type of file that points to another file or directory, very similar to Windows shortcut. You can make links to files and directories, and you can create links on different partitions and with a different inode number than the original. If the *real* copy is deleted, the link will not work.

**Hard Link** is a special type of file which has the same inode information as an original file. That type of links is for files only, not for directories. You cannot link to a file on a different partition with a different inode number. If the *real* copy is deleted, the link will work, because it accesses the underlying data which the real copy was accessing.

![Pictorial representation](pictures/fslinks.jpg)

### File system structure

| Path                  | Description                                       |
| --------------------- | ------------------------------------------------- |
| `/boot`               | files for boot process                            |
| `/root`               | superuser home directory                          |
| `/dev`                | system devices                                    |
| `/etc`                | configuration files                               |
| `/bin`  (`/usr/bin`)  | user commands                                     |
| `/sbin` (`/usr/sbin`) | system commands                                   |
| `/opt`                | third party software                              |
| `/proc`               | running processes (in RAM)                        |
| `/lib` (`/usr/lib`)   | libraries needed by commands and another software |
| `/tmp`                | temporary files                                   |
| `/home`               | users' home directories                           |
| `/var`                | logs                                              |
| `/run`                | system daemons (early start)                      |
| `/mnt`                | external file systems                             |
| `/media`              | cdrom mounts                                      |

## Commands

### File commands

| Command           | Purpose                                                      |
| ----------------- | ------------------------------------------------------------ |
| `ls`              | show list of directory contents                              |
| `ls -al`          | show formatted list with hidden with hidden files and directories |
| `cd DIR`          | change directory to *DIR*                                    |
| `cd`              | change directory to *home*                                   |
| `pwd`             | show present working directory                               |
| `mkdir DIR`       | create directory with name *DIR*                             |
| `rm FILE`         | remove *FILE*                                                |
| `rm -r DIR`       | remove *DIR* recursively                                     |
| `rm -f FILE`      | force remove *FILE*                                          |
| `rm -rf DIR`      | force remove *DIR* recursively                               |
| `cp FILE1 FILE2`  | copy *FILE1* to *FILE2*                                      |
| `cp -r DIR1 DIR2` | copy *DIR1* to *DIR2*, will create *DIR2* if it doesn't exist |
| `mv FILE1 FILE2`  | move or rename *FILE1* to *FILE2*, if *FILE2* is directory will remove *FILE1* here |
| `ln -s FILE LINK` | create symbolic *LINK* to *FILE*                             |
| `touch FILE`      | create empty *FILE*                                          |
| `cat > FILE`      | redirect standard input to *FILE*                            |
| `more > FILE`     | show *FILE*                                                  |
| `head FILE`       | show the first 10 lines of *FILE*                            |
| `tail FILE`       | show the last 10 lines of *FILE*                             |
| `tail -f FILE`    | show the last 10 lines of *FILE* and append data as *FILE* grows |
| `ln FILE`         | create hard link to *FILE*                                   |
| ln -s FILE        | create soft link to *FILE*                                   |

### Process management

### File system rights

### SSH

### Search

| Command                  | Purpose |
| ------------------------ | ------- |
|                          |         |
|                          |         |
|                          |         |
| `find PATH -name "FILE"` |         |
| `locate FILE`            |         |
| `updatedb`               |         |

### System information

### Archives

### Network

### Software installation

### Keyboard shortcuts

### Users

| Command         | Purpose |
| --------------- | ------- |
| `whoami`        |         |
| `passwd USERID` |         |
|                 |         |
|                 |         |
| `exit`          |         |

### Wildcards

A wildcard is a character that can be used as a substitute for any of a class of characters in a search.

| Wildcard | Purpose                              |
| -------- | ------------------------------------ |
| `*`      | represents zero or more characters   |
| `?`      | represents a single character        |
| `[]`     | represents a range of characters     |
| `{}`     | represents an array of terms         |
| `\`      | represents escape character          |
| `^`      | represents the beginning of the line |
| `$`      | represents the end of the line       |

### Miscellaneous

| Command | Purpose |
| ------- | ------- |
|         |         |
| `!!`    |         |
|         |         |
|         |         |
|         |         |

## File types

When you use `ls` command you can see attributes for elements of the file system. First symbol of this attributes is designated for file type. There are several designators:

| Designator | Meaning                |
| ---------- | ---------------------- |
| `-`        | regular file           |
| `d`        | directory              |
| `l`        | link                   |
| `c`        | special file or device |
| `s`        | socket                 |
| `p`        | named pipe             |
| `b`        | block device           |

