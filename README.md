# OPERRATING-SYSTEMS-CONCEPTS-

##PROCESS MANAGEMENT 
Process Concept
– Process ID & State
– Process Tree
– Process Control Block
– Context Switching
– Queues
– Viewing Processes
• Process Scheduling
• Process Creation
– Replacing Process Image
– Replication of Processes
– Waiting for Processes
– Process Termination

what is a process ?
Like files, a process is a fundamental abstraction in Unix/Linux
– An executing instance of a program
• A process is an “an address space with one or more threads executing within
that address space, and the required system resources for those threads.”
• The Linux kernel, supporting both preemptive multitasking and virtual
memory, provides a process both a virtualized processor and a virtualized view
of memory.
• Each process consists of one or more threads of execution

### Example :
 Each process has a unique identifier, the process ID (maximum 32768)
• The process ID is represented by the pid_t type, defined in <sys/types.h>
• The getpid( ) system call returns the process ID of the invoking process
• The getppid( ) system call returns the ID of the parent of the invoking process.
#include <sys/types.h>
#include <unistd.h>
#include <stdio.h>
int main() {
printf ("My pid=%d\n", getpid ( ));
printf ("Parent's pid=%d\n", getppid ( ));
return (0);
}
Results:
My pid=6811
Parents pid=6723

## Process state 
As a process executes, it changes state
new: The process is being created
running: Being executed
waiting: The process is waiting for some event to occur
ready: The process is waiting to be assigned to a processor
terminated: The process has finished execution
• State values: TASK_RUNNING, TASK_INTERRUPTIBLE, TASK_UNINTERRUPTIBLE, 
TASK_STOPPED, TASK_ZOMBIE
Example:
![image](https://user-images.githubusercontent.com/93335682/196564595-1c1496a9-b8fe-4ea9-a967-aa293129d92d.png)

A tree of process ?
![image](https://user-images.githubusercontent.com/93335682/196564725-98f33101-cb90-441b-96c6-225fcd8a40f5.png)

# Init process (First process in the Kernel )
The first process that the kernel executes after booting 
the system, called the init process, has the pid 1
• The init process handles
– The remainder of the boot process
– Initializing the system
– Starting various services
– Launching a login program
• The Linux kernel tries four executables, in the following 
order:
– /sbin/init: The preferred and most likely location for the init process.
– /etc/init: Another likely location for the init process.
– /bin/init: A possible location for the init process.
– /bin/sh: The Bourne shell, if it fails to find an init process

# process control Block 
Information associated with each process stored in a block of 
memory known as PCB or Process Descriptor.
– Process ID
– Process state
– Program counter
– CPU registers
– CPU scheduling information
– Memory-management information
– Accounting information
– I/O status information

![image](https://user-images.githubusercontent.com/93335682/196565841-a75afdca-0c31-49a5-93ca-1831d7e9fa42.png)

# Linux Process Table
– a data structure describing all of the processes that are currently loaded
• Viewing processes
– The ps command shows the processes in the system or belonging to a user



what is a Thread ?
A thread is the unit of activity within a process, the abstraction responsible for 
executing code.
• Each thread has
– an id (pid)
– a stack
– state
– program counter 
