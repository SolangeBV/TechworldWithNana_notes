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
- __CTRL + SHIFT + v__: paste copied text in the terminal
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
