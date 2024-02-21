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
- __sudo chown [username]:[groupname] [filename.extension]__: to change the user owner and/or the group owner of a file
- __sudo chgrp [groupname] [filename.extension]__: to change the group owner of a file
- __ls -l__: list all the files in the working dir with extra information (permissions and ownership)
- fileTypes:
  - __-__: regular file
  - __d__: directory
  - __c__: character device file
  - __l__: symbolic link
- permissions:
  - __r__: read
  - __w__: write
  - __x__: execute (run a script or a command or any executable file)
  - __-__: no permission
- __Modifying permissions__:
  - __sudo chmod -x [filename]__: removes the execute (-x) permission for all the owners of a file (you can also write a-x, with "a" stands for "all")
  - __sudo chmod g-w [filename]__: remove the execute (-x) permission of the group owner (g) of a file
  - if removing a permission for the user owner, then use __u__ instead of __g__
  - if removing a permission for the other owner, then user __o__ instead of __g__
  - __sudo chmod g+x [filename]__: to add a permission (use the plus sign instead of the minus sign)
  - __sudo chmod g=rwx [filename]__: to add multiple permissions of a file for (in this case) the group owner
  - __sudo chmod g=rw- [filename]__: to remove multiple permission of a file for (in this case) the group owner
  - __sudo chmod 777 [filename]__: to define permission blocks for all the owners (there are numbers from 0 to 7 that represent a different set of permissions, like 7 for rwx or 1 for --x)
  - __ls -la__ : modifying permissions for hidden files

### 2.11) Pipes & Redirects
- The output of one program can become the input of another program
- The pipe command (|) pipes the output of the previous command as an input to the next command
- eg: cat /var/log/syslog | less 
- __less__ is a command that displays the contents of a file or a command output, one page at a time (you can move pages by typing on the spacebar or on __b__, then closing the program by typing __q__)
- __history | grep sudo__: filter all commands that contain "sudo" (Globally Search for Regular Expression)
- __history | grep "sudo chmod"__: to filter all commands that contain a phrase (note the quotation marks)
- __ls /usr/bin | grep java__: to list all files that have a java extension or have "java" in their name
- __history | grep sudo > sudo-commands.txt__: to save the results of the last command into a file
- __cat sudo-commands.txt > sudo-rm-commands.txt__: to copy the contents of a file into a new file
- __history | grep rm > sudo-rm-commands.txt__: to overwrite commands in an already existing file
- __history | grep rm >> sudo-rm-commands.txt__: to append more commands to an already existing file (note the double >>)
- It is possible to write multiple separate commands on the same line, as long as they are separated by a semicolon (;) -> they will be executed in the same order as they are written

### 2.12) Introduction to Shell Scripting
- Allows to run the same series of commands in the same order on another server -> all written in a file (aka, a shell script)
- A shell (.sh) script is a file full of Linux (or UNIX-like) commands
- __Shell__: the program that interprets and executes the various commands that we type in the terminal
  - it translates our command so that the OS Kernel can understand it
- __sh__: (aka Bourne Shell), a Shell implementation
  - used to be the default Shell
- __Bash__: (aka Bourne again Shell), another Shell implementation
  - improved version of sh
  - currently the default Shell for most UNIX like systems -> usually Shell and Bash are often used interchangeably
  - Bash is a shell program and a programming language
    
__Shebang__
- __touch setup.sh__: example of creating a bash script file
- We might have multiple shell program on the system -> how does the OS know which shell to use? -> By writing a Shebang line
- eg: #!/bin/bash _or_ #!/bin/sh _or_ #!/bin/zsh (written at the beginning of the .sh file)
- The Shebang line points to a file under /bin which is going to act as the interpretor of the .sh file we are writing
- __sudo chmod u+x setup.sh__: create user permissions to run the file -> now it is an executable file
- __./setup.sh__: to execute all the commands in the script file
- __bash setup.sh__: another way to execute all the commands in the script file

### 2.13) Shell Scripting - Concepts & Syntax
__Variables__
- It is possible to use variables in a script file
  - eg: file_name=config.yaml (__NB__: there must be __no spaces__ around the "=" sign)
  - eg: echo "using file $file_name to configure something"
- It is also possible to store the result of a command in a variable and reference it multiple times in the .sh file
  - eg: config_files=$(ls config)
  - eg: echo "here all all configuration files: $config_files"

__Conditional Statements__
- eg: The example below checks if "config" is a directory
- eg: if [-d "config"]
      then
        echo "reading config directory contents"
      else
        echo "config dir not found. Creating one"
        mkdir config
      fi
  - Note that _fi_ is just "if" but backwards and it tells the program that the if statement is concluded
  - It is also possible to user _elif_ for else if statements

  __Basic Operators__
  - __-f file__: checks if file is an ordinary file
  - __-r file__: checks if a file is readable
  - __-u file__: checks if a user id is set for a file
  - __-eq 10__: checks if a variable is numeric and is equal to 10 (in this case)

  __Passing arguments to a Script__
  - How can we provide values externally to a script?
  - -> use positional parameters
  - eg: user_group=$1
  - Now add parameters to the commandline that starts the sh file
  - eg: _./setup.sh admin_
  - __NB__: you can use positional parameters from 1 to 9

  __Read User Input__
  - Another way to provide values to the bash script externally
  - __read -p "Please enter your password: " user_pwd__: saves the password in the variable user_pwd
  - __-p__ stands for prompt
  - What do we do if we don't know in advance how many parameters we will be given?
    - __$*__: this stores all the provided parameters in a single variable
    - __$#__: this stores the number of parameters

  __Loops in Linux__
  - Types of loops in Linux:
    - while loop
    - for loop
    - until loop
    - select loop
  - eg: for param in $*
          do
            echo $param
          done
  - Note that the intentation is just aesthetic (as in java), not functional (as in python)
  - eg: while true
        do
          statement(s)
          if [condition]
          then
            break
          fi
        done
  
__Arithmetic operations__
- __$((2 + 4))__: note that we use double parentheses to tell the script file that the two variables are numbers and _not_ strings

__Portability__
- Comparing strings in Posix (and therefore Bash too): =
- Comparing strings in Bash: ==
- If statements in Posix (and therefore Bash too): [
- If statements in Bash: [[
- __NB__: if you use the Bash version, you will lose portability

__Alternatives to Bash Scripting__
- Another programming language (like Python)
- A configuration tool (like Ansible)

### 2.14) Shell Scripting - Basic Concepts & Syntax
__Functions__
- function_name () {
  list of commands
  }
- To define a function:
  ```bash
  function score_sum {
    sum=0
  while true
  do
    read -p "enter a score: " score

    if ["$score" == "q"]
    then
      break
    fi

    sum=$(($sum+$score))
    echo "total score: $sum"

  done

  }
  ```
- __score_sum__: to execute the function
- To pass parameters to a function:
  ```bash
  function create_file() {
    file_name=$1
    touch $file_name
  }
  ```
- __#__: commenting a line
- __NB__: do not user more than 5 input parameters in a function, otherwise split it into smaller functions
- __result=$(sum 2 10)__: example of storing the result of a function in a variable
- __sum 2 10
  result=$?__: this is another way of storing the result of a function in a variable ($? captures the value returned by the last command)

### 2.15) Environment Variables
- Each user in an Operating System has its own environment (eg: theme, shell program, default editor, default web browser)
- These configurations are saved in the user's environments only
- Environment variables are KEY=value pairs
- eg: SHELL=/bin/bash
      HOME=/home/nana
      USER=nana
- __printenv__: access all environment variables for the logged user
- __printenv USER__: to access a specific environment variable (in this case, USER)
- __echo $USER__: to reference environment variables in CLI or bash scripts
- It is possible to create our own environment variables, for example, to store credentials
- Every programming language has ways to access to environment variables
- __export DB_USERNAME=dbuser__: to create/rename a custom environment variable
- __unset DB_NAME__: to delete environment variables
- __NB__: the _export_ command is used to set variables that will last only during the current terminal session
- What to use instead to set environment variables permanently? -> in the .bashrc file in your home directory
  - __export DB_USERNAME=dbuser__: write this in the .bashrc file
  - __source .bashrc__: to reload the .bashrc file (in the CLI terminal)
    
__Persisting environment variables (system-wide)__
- in the /etc folder within the home directory, there is a file (called _environment_) that stores all the environment shared by all users
- The PATH environment variable contains the list of directories containing executable files, all separated by _:_
  - It tells the shell which directories to search in for the executable in response to our executed command
  - eg: to execute the _ls_ command, we don't need to write "/usr/bin/ls", but instead we only write "ls" and the system knows where to find the command
  - it is also possible to add a command only for our user -> add the PATH variable in .bashrc file with the location of the command we created appended to the global path (PATH=$PATH:/home/nana)

### 2.16) Networking Basics
- __LAN__: Local Area Network -> collection of devices connected together in one physical location
- Each device has a unique __IP__ address (Internet Protocol)
- Devices communicate via these IP addresses
- IP addresses are composed of 32 bits (4 groups of 8 bits)
- IP addresses range from 0.0.0.0 to 255.255.255.255
- __Switch__: a tool in the LAN that helps devices communicate. It knows all IP addresses of all devices
- How to talk to devices outside LAN (eg: open facebook)? -> __Router__
- __Router__: a device that sits between a LAN and outside networks (Wide Area Network)
- __Gateway__: IP address of the Router
- Devices in the LAN belong to the same IP address range
- __Subnet__: logical subdivision of an IP network
- Example of IP address range: 192.168.0.0 255.255.255.0 (only the last number will change within the subnet)
- Another example of IP address range: 192.168.0.0 255.255.0.0 (the last __two__ will change within the subnet)
- __CIDR__: Classless Inter-Domain Routing, another way to represent IP ranges
  eg: 192.168.0.0/16 -> the first 2 octets (16 bits) are fixed
- Any device needs 3 pieces of data for communication: IP Address, Subnet, Gateway
- IP addresses within a LAN are __not__ visible to the outside network or internet
- The address of a device within a LAN is replaced with the IP address of the router -> NAT (Network Address Translation)

__Firewall__
- By default, a device within the LAN (eg: a server) is not directly accessible from outside the LAN -> everything outside the LAN communicates with the router
- A firewall is a system that prevents unauthoriyed access from entering a private network
- Using Firewall Rules, you can define which requests are allowed
  - eg: define which IP addresses in the LAN are accessible
  - eg: define which IP addresses outside the LAN can access the server
  - eg: which ports are accessible on the server

__Port__
- Every device has a set of ports
- Ports are like a set of doors to the same building
- You can allow specific ports (doors) and specific IP addresses (guests)
- Different applications listen on specific ports -> only these ports are available to access that application
- Default ports: 80 (Web Servers), 3306 (MySQL databases), 5432 (PostreSQL databases)
- __NB__: ports are unique on each device -> you can't start two applications on a device that share the same port

__Domain Name Service (DNS)__
- www.facebook.com runs on different computers, each identified by a different IP address -> that's why we don't type the IP address
- Humans remember names more easily than a set of numbers -> that's why we use DNS
- Under the hood, that name is translated into an IP address
- The service that does this translation is DNS
- These names are divided into different domains that follow a hierarchical structure
  - _Root Domains_, with names from a to m
  - _Top Level Domains_, like .mil, .edu, .com, .org, .net, .gov, .it, .de, .us, ...
  - _Subdomain_, optional, another word separated by a dot before the official name of the website (eg: courses.nana.com, workshops.nana.com, bootcam.nana.com)
- Who regulates these names? Internet Corportation for Assigned Names and Numbers (ICANN)
- Each computer has a DNS client installed in it that is responsible to retrieve (and store as cache) the IP address that corresponds to that name

__Networking Commands__
- __ifconfig__: information about your network
- __netstat__: active internet connections established on your machine (aka, which applications on your computers are actively running and on which port they are listening)
- __ps aux__: current running processes and programs
- __nslookup__: to retrieve the IP address of any domain name
- __ping__: checks whether a service or application is accessible

### 2.17) SSH Secure Shell
- How to access a remote server to copy a script file onto it and execute it? -> secure shell
- SSH: a computer protocol that gives users a secure way to access a computer over the internet
- SSH refers also to the suite of utilites that implement that protocol
- Two ways to authenticate to a remote server with SSH:
  - with Username and Password
  - SSH key pair
- __Private Key__: secret key (imagine a physical key). It is stored securely on the client machine
- __Public Key__: public (imagine a door lock). It is installed on the remote server and can be shared
- Each client will have a different set of SSH key pair. Each public key will be installed onto the remote server
- It is also possible to create a SSH key pair for services, like Jenkins
- Most Operating Systems will have an SSH service installed and running on port 22
- __NB__: In firewall rule we allow access only on a single port, meaning we allow access only to a single application and not to the entire computer the application is running on
- __NB__: When we connect with an SSH service (and not only through a port), we have access to the entire computer -> we need to restrict access to specific IP addresses with the firewall

__Connect to a remote server via SSH (username and password)__
```bash
ssh root@64.225.198.160
```
- root -> the username
- 64.225.198.160 -> the IP address of the remote server we want to connect to
- after this, type the password you have configured in the remote server
  
__Connect to a remote server via SSH (SSH key pair)__
- While we are connected to the remote server, we have ccess the .ssh hidden folder
- __ssh-keygen -t rsa__: to create a SSH key pair
- Now under .ssh we have two new files: id_rsa (private key) and id_rsa.pub (public key)
- On the remote server modify the file _authoriyed_keys_ under .ssh and add the contents of id_rsa.pub
- __exit__: to logout from the remote server
- Now connect to the host again
```bash
ssh root@64.225.198.160
```
- Now we are no longer prompted for a password because (under the hood) we used the SSH keys
- The command above actually stands for __ssh -i .ssh/id_rsa root@64.225.198.160__, but we can type the shorter version when the private key is named and located as shown in the command

__Copy a file from the local machine to the remote server__
- __scp test.sh root@64.225.198.160:/root__: stands for secure copy (scp [filename] [username]@[server IP address]/[location on the server])
- longer version of this command: __scp -i .ssh/id_rsa test.sh root@64.225.198.160:/root__

## Module 3 - Version Control with Git
### 2.1) Introduction to Version Control and Git
- Code is hosted centrally on the internet -> code repository
- Best practice: push and pull often from remote repository -> Continuous Integration

### 3.2) Basic Concepts of Git
- Git is the most popular version control tool
- SVN: another version control tool

Working Directory
-> git add
Staging Area
-> git commit
Local Repository
-> git push
Remote Repository

### 3.3) Setup Git Repository Remote and Local
- GitHub and GitLab are different platforms that can host your repository
- Companies have their own company git servers (e.g. Bitbucket)
- To clone the remote repository into your own local repository, you´ll need to install a Git Client (either a UI client or a Git Command Line Tool)
- I will also need to authenticate myself to GitHub/GitLab -> add an SSH key to the git client

### 3.4) Working with Git
- 

