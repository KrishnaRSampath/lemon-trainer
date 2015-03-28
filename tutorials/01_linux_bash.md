# Linux File System and Bash Command Line
In this tutorial we will explore the Linux file system and some Bash command line tools.

---

## Create a Workspace

When working in a Linux environment for the first time, the file system and directory tree may be difficult to fully comprehend. The distribution of tools, files, and services throughout the tree - and in combination with user and group permissions - may feel like a redefinition of logical structure.

Nowhere is this more true than with a typical MongoDB installation on Ubuntu, as will be completed in [a further tutorial](./03_mongodb_install.md). The main database components - the datastore itself, the configuration and log files - are all stored in different locations across the directory tree. Interaction, however, is thankfully given shortcuts in the shell with a set of commands that call to those locations as necessary.

In addtion to the database components, there is the matter of the project itself, the web application you will build and run from this server. The application files also need a place to live, owned by our own user account, that we will call our workspace.

Create a workspace directory, then clone this ```lemon-trainer``` repository from GitHub:
```
$ mkdir ~/workspace
$ cd ~/workspace
$ git clone https://github.com/AmundsenJunior/lemon-trainer.git
$ cd lemon-trainer
```

---

## Bash Commands

### Navigating the Filesystem
For most commands, you can pass directory paths and file names as arguments to run the command upon. Directory paths can be relative to your current location, or absolute. An absolute path will always start at root (```/```), the very top of the Linux directory tree.

(e.g., ```cat lemon-trainer/app-examples/views/index.html``` goes three levels down into subdirectories)
e.g., ```cat /etc/mongodb.conf``` goes into the ```etc/``` subdirectory of the root directory, ```/```)

```ls``` lists directory contents, both files and subdirectories.
  ```ls -a``` will list directory contents including hidden files.

```cd``` changes to the directory given.
  ```cd ~/workspace``` enters the ```workspace``` subdirectory of your user home directory. The tilde is short for the ```/var/username``` location.

```pwd``` displays the current directory ("pwd" stands for present working directory).

```.``` refers to the current directory.

```..``` refers to the directory one level up. For example, if we are in ```~/workspace/lemon-trainer/```, typing ```cd ..``` would move us into ```~/workspace/```. It can be strung together to refer to multiple levels up (e.g., ```cd ../../```).

### Manipulating files and directories

```cp``` copies a file (keeping the original intact), while ```mv``` moves or replaces the original file. Both commands can act upon:
  * a file or files,
  * within the current directory or from one location to another,
  * with the same file name or to a new name.

  ```
  $ cp 01_linux_bash.md 01_linux_bash.md.copy
  $ cp lemon-trainer/mongo_install.sh tutorials/
  $ mv tutorials/* ./
  ```
  
  ```cp -R``` recognizes the ```-R``` recursive argument, and will apply the action on all subdirectories and files. 

```mkdir``` creates a new directory. If the directory doesn't yet exist, a ```cp``` or ```mv``` command will not work.

```rm``` deletes a file.
  ```rm -R``` will recursively delete a directory (including all subdirectories and files).
  ***NOTE:** Be cautious with the ```-R``` argument. Be certain of your location in the file system and of deleting all the subdirectory contents. There is no Recycle Bin in Linux with this command.*

### Reading and searching files

```cat``` outputs the contents of a file to the Terminal. If the file is longer than the height of your Terminal window, you'll have to scroll up to view it all. In that instance, better to use...

```less```, which outputs a file contents, automatically paginated to the height of the Terminal window. Use ```ENTER``` to scroll down one line at a time, or ```SPACEBAR``` to move one "page" at a time. Press ```Q``` to exit the viewer.

```tail``` outputs the last lines of a file. By default, it outputs the last 10 lines, so use the ```-NUMBER``` argument to output a different number of lines. This is a very useful tool for checking log files that frequently update in the background.
  ```
  $ tail -20 /var/log/mongodb/mongodb.log
  ```

```grep``` searches a file for a text pattern (e.g., a word) and prints out the lines in which that pattern appears:
  ```
  $ grep -e update ~/workspace/lemon-trainer/tutorials/00_virtualbox_ubuntu.md
  ```

### Creating and writing to files

```touch```

```tee```

```nano```

```vim```

### User and group permissions

```whoami```

```sudo```

```chown```

```ls -l```

### Utilizing the shell

```export``` (environment variables)

pipe |

redirection < and >

tab completion

help (-h or --help on some installed utilities/applications, with no arguments for Bash commands)

```man```

```echo```
