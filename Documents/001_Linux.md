# Linux (Linux Mint)
###### Abstraction

## Components/Subsystems/Modules/Packages Organized in Layers/Levels
<table>
    <tr>
        <th>Overall</th>
    </tr>
    <tr>
        <td>User</td>
    </tr>
    <tr>
        <td>Applications?User Processes?: Web browsers, Games</td>
    </tr>
    <tr>
        <td>Operating System: Linux</td>
    </tr>
    <tr>
        <td>Hardware: Memory</td>
    </tr>
</table>

<table>
    <tr>
        <th>Linux System</th>
    </tr>
    <tr>
        <td>Processes/User Processes: Graphical User Interface, Servers, Shell</td>
    </tr>
    <tr>
        <td>Linux Kernel: System Calls, Process Management, Memory Management, Device Drivers</td>
    </tr>
    <tr>
        <td>Hardware: Processor (CPU), Main Memory (RAM), Devices:: Disks, Network Ports</td>
    </tr>
</table>

###### Kernel
*   The core of the OS
*   Residing in memory
*   Tells CPU what to do
*   Manages the hardware
*   Acts primarily as an interface between the hardware and any running program

###### Kernel vs. User Processes
|Kernel|User Processes|
|------|--------------|
|Runs in kernel mode|run in user mode|
|Usrestricted access to the processor and main memory|Restrict access to a subset of memory and safe CPU operations|

###### Kernel Space
*   The area that only the kernel can access

###### User Space
*   The parts of main memory that the user processes can access.

###### Main Memory
*   A big storage area for a bunch of 0s and 1s
    *   Each 0 or 1 is called a **bit**
*   The running kernel and processes reside in main memory
*   All input and output from peripheral devices flows through main memory
*   A CPU reads its instructions and data from main memory and writes data back to the main memory
    *   A CPU is just an operator on main memory

**State**
*   A state is a particulay arrangement of bits
*   Refer to state in abstract terms
    *   The process is waiting for input
    *   The process is performing Stage 2 of its startup

**Image**
*   Refers to a particular physical arrangement of bits

## The Kernel
*   Process management
    *   Determining which processes are allowed to use the CPU
*   Memory management
    *   Keep track of all memory
*   Device drivers
    *   Acts as an interface between hardware and processes
*   System calls and support
    *   Processes normally use system call to communicate with the kernel
### Process Management
*   Start
*   Pause
*   Resume
*   Terminate

**Multitasking**
*   The system appears to be running multiple processes at the same time

**Consider a system with a one-core CPU**
*   Only one process may actually use the CPU at any given time

**Context Switch**: The act of one process giving up control of the CPU to another process
>   A process is running in user mode and its **time slice** is up
*   The CPU (the actual hardware) interrupts the current process based on an internal timer, switchs in to kernel mode, and hands control back to the kernel
*   The kernel records the current state of the CPU and memory, which will be essential to resuming the process that was just interrupted
*   The kernel performs any tasks that might have come up during the preceding time slice (such as collecting data from input and output (I/O) operations)
*   The kernel is now ready to let another process run. The kernel analyzes the list of processes that are ready to run and choose one
*   The kernel prepares the memory for this new process and then prepares the CPU
*   The kernel tells the CPU how long the time slice for the new process will last
*   The kernel switches the CPU into user mode and hands control of the CPU to the process

The kernel runs between process time slices during a context switch

### Memory Management
*   The kernel must have its private area in memory that user processes can't access
*   Each user process needs its own section of memory
*   One user process may not access the private memory of another process
*   User processes can share memory
*   Some memory in user processes can be read-only
*   The system can use more memory than is physically present by using disk space as auxiliary

>   Modern CPUs include a memory management unit (MMU) that enables a memory access scheme called virtual memory

>   The implementation of a **memory address map** is called a **page table**

### Devices Drivers and Management
*   Devices drivers have traditionally been part of a kernel

### System Calls and Support
*   Other than init, all user processes on a Linux system start as a result of fork(), and most of the time, you also run exec() to start a new program instead of running a copy of existing process

*   Pseudo-devices look like devices to user processes, but they are implemented purely in software
    *   Usually in the kernel
    *   for example, /dev/random

## User Space




## Update
    sudo apt-get update
    sudo apt-get dist-upgrade
    
## Install Software
    
    sudo apt-get install -y Package Name List