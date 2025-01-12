An operating system is software that controls the execution of application programs and acts as an interface between applications and computer hardware. 
![[Pasted image 20241223161114.png]]
### OS Kernel Services
A *kernel* is the core of an operating system and is responsible for interfacing with the hardware.
- **Memory management**
	- allocates memory to programs
	- manages *virtual memory*
- **Task management**
	- launches processes (program + state of program)
	- handles interrupts
	- maintains process table (task manager)
	- sets program privilege levels
- **File management**
	- responds to program requests to manage files
	- sets and checks permissions
	- handles *buffering* 
- **Device management**
	- use *device drivers* to respond to program requests to interface with peripherals
### Essential hardware features
- Memory protection - to protect the OS and allow the OS to protect programs from eachother
- Timer - to prevent a job monopolizing the system
- Privileged instructions only executed by OS ie. I/O
- Interrupt compatibility

---
### Scheduling
Scheduling to make effective use of the processor. 
- Memory access and I/O devices are very slow compared to processor sped
- Multiple tasks need to share the machine
- Processor can only do one task at a time
While one task is waiting for an I/O device, another task should be able to use the processor.

![[Pasted image 20241223170020.png]]

##### Context Switching
Context switching is the act of saving the state of a running process, and another process being given processor resources. The **Process Control Block** contains the information a process is in:
- Identifier
- State
- Volatile environment
	- Program Counter
	- Memory Pointers
	- Context Data
- Priority
- I/O status
- Accounting information
##### Types of Scheduling
- Long-term scheduling: adding to the pool of processes to be executed
- Medium-term scheduling: add to processes that are in main memory
- Short-term scheduling: deciding which process will be executed by the processor
- I/O scheduling: deciding which process' pending I/O request will be handled by a peripheral

---
### Memory Management
The memory management function of an operating system keeps track of the status of each memory location that is allocated or free, and makes use of **virtual memory** which employs secondary storage as memory.
##### Swapping
- The operating system stores a queue of processes to execute
- As space becomes available, the processes are loaded from the disk into main memory
- A process may be swapped out if it is *stalled* (ie. waiting for main memory)
##### Partitioning
Distributing a set of processes varying in size:
- **fixed memory partitions**: a logarithmic distribution of partition sizes is best
- **variable memory partitions**: memory is allocated as required however fragmentation occurs, making it difficult to load incoming processes in which data is stored non-contiguously over time and so there is wasted space.
**Logical address**: location relative to beginning of program
**Physical address**: physical location in main memory
**Base address**: starting location of a process
![[Pasted image 20241223172230.png]]

##### Paging
Fixed and variable size memory partitions are inefficient.
- Divide physical memory into equal **frames**
- Divide process into equal **pages** of the same size as frames
- Mapping pages onto frames is inefficient
**Demand paging** refers to each page of a process being brought in only when it is needed.
- Advantages
	- More processes can be maintained in memory
	- More time efficient as unused pages not swapped
- Disadvantages
	- If a page is replaced just before use, must be swapped back in
	- **Thrashing** may occur where processor spends more time swapping pages than executing instructions
A **page fault** refers to an interrupt where a required page is not loaded into main memory.

##### Segmentation
Addressable memory can also be subdivided ingo segments where memory consists of multiple address spaces known as segments that are of variable size. Memory references consist of a (segment number, offset) form of address.
- Simplifies handling of growing data structures
- Higher protection (segment privileges)
- Higher sharing among processes
- Programs altered and recompiled independently without needing to be relinked
##### Virtual Memory
- Pages swapped in and out of memory as required
- Single process offset is not enough: table of offsets for each page mapping onto frames (**page table**)
- Logical addresses refer to a page, and the page table translates base address (logical page) to the physical address (physical frame).


Week 4 Monday, as part of [[Computer Architecture]]