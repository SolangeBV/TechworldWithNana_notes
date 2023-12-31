# Techworld With Nana - Notes

## Module 1 - Introduction to DevOps
- Roles and responsibilities of a DevOps Engineer:
  -> handle the release of new code in production (e.g. deploy it)
  -> avoid downtime when upgrading an application that is in production, or if a server fails
  -> handle huge traffic (e.g.: millions of requests)
- Technical knowledge of an Operations Engineer:
  - Operating Systems, mostly Linux
  - Command-line
  - Automated scripts
  - Monitoring tools (that monitor the IT infrastructure)
- A DevOps Engineer is the intermediary between developers and IT operations
- They have a subsets of skills from both sides


## Module 2 - Operating Systems & Linux Basics
### 2.1) Introduction to Operating Systems
- Operating System:
  - The intermediary between applications and the hardware (CPU, memory, storage, I/O devices) needed for those applications to run
  - Allocates resources among applications
  - Isolates the content of different applications so that these don't interfere with each other
- A process is a small unit that operates on a computer (e.g. starting an application)
- A pc with one CPU can process only one process at the time (CPU is switching so fast that you don't notice it)
- Multi-core computers contain multiple CPUs (aka multiple processors) -> faster computers
- RAM = Rapid Access Memory (aka the working memory needed by running applications)
- Memory Swapping: the OS clears the memory storage for the application, saves it into a secondary memory (the storage), and loads the new processes data into that clear memory (NB: this process takes time)
- Storage: persists data long-term (aka the hard drive of a computer)
- Operating Systems are also responsible for Security and Networking (managing users and permissions, assigning ports and IP addresses)
- Structure of an OS:
  - Kernel (e.g. Linux, Darwin)
    - this part loads first when turning on a computer
    - manages the hardware components (CPU, Memory, RAM, I/O Devices)
    - Device Drivers are programs that allow external devices to interact with the computer
    - Kernel is a program
    - Consists of device drivers, dispatcher, scheduler, File System, ...
  - Application Layer (e.g. Ubuntu, Mint, CentOS, Debian, Android, macOS, iOS)
    - Different application layers have different graphics, programming languages, compilers, ...
  - User Apps
- Computers for running applications that the public can access to are powered by Server Operating Systems, which usually have no GUI or I/O Devices (-> access to them only via a command line)

### 2.2) Introduction to Virtualization & Virtual Machines
- Virtual Machine: it makes it possible to install an OS on top of another OS
- Hypervisor: makes it possible to host multiple virtual computers on a physical computer (e.g. VirtualBox)
- VirtualBox creates a virtual CPU, a virtual RAM and virtual storage for each virtual machine (these resources come all from the hardware of the physical computer)
- Virtual Machines are completely isolated
- Type 1 Hypervisor: installed directly onto the hardware -> used for servers
- Type 2 Hypervisor: installed onto the host OS -> used for Personal Computers
- Benefits of virtualization: abstraction of the Operating System from the hardware (before: if the hardware is damaged, you lose your entire application, data, configurations and OS, after with virtualization: you can make copies of the Virtual Machine Image)
- Backups of Virtual Machine Images are called Snapshots

### 2.4) Linux File System
- Windows:
  - Multiple root folders (aka discs or drives)
- Linux:
  - Hierarchical Tree Structure
  - One root folder
- Folders under the root folder in Linux:
  - __root__: reserved for the root user
  - __home__: reserved for all other users (so that can have their own data, programs and configurations)
  - __bin__: stands for binary, contains executables for most essential user commands (available system-wide), eg) copy command
  - __sbin__: binaries for different commands, system binaries, need the permission of a super-user to be executed, eg) creating users
  - __lib__: libraries for those binary commands
  - __usr__: used to be the user home directory, now containing the same commands from the root folder (bin, sbin, lib, ...) -> created historically to hold the data that could not fit into the folders under the root folder
  - /usr/local: contains programs that YOU install on the computer and that will be available for ALL users
  - If you need to install programs only for your users, then do that in the home directory
  - __opt__: optional folder, contains third-party programs that need to be installed all in one place and not divided into lib and bin folders (eg: IDE programs)
  - __boot__: contains files required for booting (NB: <u>never</u> touch this folder)
  - NB: the afore-mentioned folders are read-only!
  - __etc__: contains system information that can be writable (like user passwords or configuration files)
  - __dev__: location of device files (eg: webcam, keyboard, hard drive, ..), apps and drivers will have access to this folder and <u>not</u> the user
  - __var__: contains files to which the system writes data during the course of its aoperation (eg: logs, cache)
  - __tmp__: contains temporary resources needed for some processes
  - __media__: contains subdirectories where removable media devices are mounted to when they are inserted into the computer (eg: a USB, a disc)
  - __mnt__: sys admins mount temporary file systems here
  - Hidden files: there are some in the home directory. You can see them by choosing "show hidden files" on the menu
    - Hidden files are called dotfiles because their name starts with a dot
    - To create a hidden folder: name it with a dot before the name
    
### 2.5) Introduction to Command Line Interface
eg) nana@nana-ubuntu:~$
- nana: the username logged in the computer
- nana-ubuntu: the computer name (or server name) for that CLI
- The tilde (~) stands for home directory
- The $ stands for a regular user (and not a root (aka admin) user -> then it would be #)

### 2.6) Basic Linux Commands
__Commonly used commands__
- __pwd__: print working directory (to see which folder we are in)
- __ls__: list folders and files (located in the working directory)
- __ls absolute/path/of/the/target/directory__: list folders and files located in a directory different from the working directory
- __cd__: move to another directory
- __mkdir__: create a directory in the working dir
- __touch [filename.extension]__: create a file in the working dir
- __rm [filename.extension]__: remove file
- __rm -r [folderName]__: remove folder (-r stands for recursive, because it will delete all the files within that folder too)
- __cd /__: move to root folder
- __clear__: clean up terminal history
- Everything in Linux is a file! Text documents, pictures, directories, commands, ...
- __mv [filename] [newFilename]__: rename the file to a new filename
- __cp -r [folderName] [name of copy folder]__: copy a folder and make a copy of it
- __cp [fileName] [copyFileName]__: copy a file and make a copy of it
- __ls -R [folderName]__: list all the files in the chosen directory and in its subdirectories
- __history__: displays all the commands that we have executed in the current session
- __CTRL + r__: goes through search history and finds all commands starting with the letters that you type
- __CTRL + c__: stops the current command
- __SHIFT + CTRL + v__: paste copied text in the terminal
- __ls -a__: display hidden files (-a stands for "all")
- __cat [filename]__: display contents of a file (cat stands for "concatenate")
  
__Display OS Information__
- __uname -a__: show system and kernel
- __cat /etc/os-release__: version information
- __lscpu__: detailed info about the CPU
- __lsmem__: memory information

__Execute commands as superuser__
- sudo -> allows regular users to run programs with the security privileges of the superuser or root (just on that line)
- __sudo adduser [userName]__: example of using a command that only superusers can use
- __su - [otherUser]__: switch to user otherUser

### 2.7) Package Manager - Install Software
__Package Manager__
- We need a package manager in Linux to install/uninstall/update programs (program data are split into different folders, unlike in Windows)
- Manages and resolves all required dependencies
- There is already a Package Manager bundled in Linux -> __APT__ (Advance Package Tool)
- __sudo apt search openjdk__: to install Java on our Linux computer
- __sudo apt remove <package_name>__: to remove an installed package
  NB: make sure you uninstall all the dependencies installed together with the package (you have to do this manually)
  eg) you remove java (sudo apt remove openjdk-17-hre-headless) and then you remove the dependency installed with it (sudo apt remove openjdk-11-jre-headless)
- __APT-GET__ is another package manager already available in Ubuntu
- APT vs APT-GET: APT is more user-friendly (eg: it has a progress bar) but it as fewer command options, while APT-GET achieves the same as APT, but you need to use more command options to achieve the same as in APT
- APT-GET does not have the search command
- __Where do these packages come from?__ -> online repositories (eg: at.archive.ubuntu.com/ubuntu)
  These sources are listed in /etc/apt/sources.list
- NB: always upgrade the package index before upgrading or installing new packages -> sudo apt update (this refreshes the state of the repository that the distribution is using)
- NB: there are packages that are not available in these official repositories -> we need to use an alternative way to install software, eg:
  1) Ubuntu Software Center
  2) Snap Package Manager
  3) Add Repository to official list of reops (add-apt-repository)

__Ubuntu Software Center__
- This works like Playstore in an android phone
__Snap Package Manager__
- Previously it was called "snappy"
- It is a package manager already bundled in ubuntu (try to tap "snap" in a terminal window)
- The packages it installs already contain the needed dependencies
- To install Visual Studio Code with snap, type "sudo snap install --classic code"
- APT vs Snap
  - APT shares dependencies among packages, while Snap has self-contained dependencies in each package
  - Snap supports universal Linux packages, while APT is for only specific Linux distributions (like Ubuntu)
  - Snap updates automatically, while APT needs manual updates
- Use Snap as an alternative to APT, but choose APT first
__Add Repository to official list of repos__
- Add repo into /etc/apt/sources.list
  eg: sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bio..."
- Then install package as usual with APT
  eg: apt install <package name>
- NB: verify these repositories first, as they might not be secure

- NB: other distributions use different package managers^^
- If a distribution is in the same category of another distribution, then they will use the same package manager
- Examples of categories: __Debian based__ (Ubuntu, Debian, Mint -> they all use APT and APT-GET), __Red Hat based__ (RHEL, CentOS, Fedora -> they all use YUM)
- Different package managers might have access to different versions of a package (older/newer)

### 2.8) Vi & Vim Text Editor
- Vim is a Command Line Interface UNIX text editor
- Linux Command Line has a built-in text editor called Vim (aka improved version of Vi)
- Why do we need Vim?
  - Faster in CLI than in a text editor
  - Supports multiple formats
  - Needed when working on a remote server (Vim is the only option available)
- __vim <filename.extension>__: open file with vim
- Vim has two modes:
  - Command Mode:
    - Default mode
    - Here you cannot edit the text
    - Whatever you type is interpreted as a command
    - Navigate, search, delete, undo, ...
  - Insert/Edit Mode:
    - Allows you to enter text
- __i__: switch from command to insert mode
- __esc key__: switch from insert to command mode
- __wq__: save the file (Write Quit)
- __:q!__: to close the file and discard the changes (aka, close without saving)
- __vim [filename].[extension]__: creates a new file and opens it
- __dd__: do delete a line (make sure to be in command mode and with the cursor on the line you want to delete)
- __d10__: delete next 10 lines, including the one with the cursor in it
- __u__: undo the last changes
- __A__: jump to the end of the line and switch to insert mode (aka: do this when you are in command mode)
- __0__: jump to the start of the line and stay in command mode
- __$__: jump to the end of the line and stay in command mode
- __12G__: jump to a certain line (in this case, to the 12th line of the file)
- __/nginx__: to go in search mode (make sure to be in command mode) and look for a word (in this case, nginx)
- __n__: jump to the next match of the search results
- __N__: jump to the previous match of the search results
- __:%s/oldString/newString__: to replace all the occurrences of a word (note that s stands for String, because we are replacing strings)

### 2.9) Linux Accounts & Groups
- 3 User Categories:
  - Root User: unrestricted permissions (aka superuser) -> there is only __one__ per computer
  - User: user we create to login and that will have a directory in the home directory
  - Service: relevant on Linux Server distributions (eg: a web application server or a database server that will be started by a service user)
- How to manage permissions:
  - User Level -> give permissions to User directly
  - Group Level -> give permissions to all users within a certain group
- /etc/passwd: stores user account information (username:password:userId:groupId:userIdInfo:homeDirectory:pathOfShell)
- __sudo adduser [username]__: add a user
- __sudo passwd [username]__: to set a new password for a certain user
- __su - [username]__: to login as another user
- __su -__: to login as the root user
- __sudo groupadd [groupName]__: to create a new group
- __cat /etc/group__: to print all groups
- adduser + addgroup + deluser + delgroup -> you don't have to insert all the information yourself -> use these for manual insertions
- useradd + groupadd + userdel + groupdel -> you have to insert all the information yourself -> use it for automated tasks (like scripts)
- __sudo usermod -g [group] [username]__: change the primary group of a user
- A user can get on primary group and multiple secondary groups
- __sudo usermod -G [group1], [group2] [username]__: to assign a user to one or multiple secondary groups
- __sudo usermod -aG [group] [username]__: to append a new secondary group to the already existing groups of a user
- __man ls__: to access the Linux manual pages to access all possible commands
- __groups__: to see all groups the logged user belongs to
- __groups [username]__: to see all groups a certain user belongs to
- __exit__: to logout from the current session and login into the previous session (aka previous user)
- __sudo gpasswd -d [username] [group]: to remove a user from a group

### 2.10) File Ownership & Permissions
- 
