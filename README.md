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

### 2.3) Setup Linux Ubuntu VM
