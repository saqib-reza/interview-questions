## Operating System


<details>
<summary>What is an operating system?</summary><br><b>

From the book "Operating Systems: Three Easy Pieces":

"responsible for making it easy to run programs (even allowing you to seemingly run many at the same time), allowing programs to share memory, enabling programs to interact with devices, and other fun stuff like that".
</b></details>

#### Operating System - Process

<details>
<summary>Can you explain what is a process?</summary><br><b>

A process is a running program. A program is one or more instructions and the program (or process) is executed by the operating system.
</b></details>

<details>
<summary>If you had to design an API for processes in an operating system, what would this API look like?</summary><br><b>

It would support the following:

* Create - allow to create new processes
* Delete - allow to remove/destroy processes
* State - allow to check the state of the process, whether it's running, stopped, waiting, etc.
* Stop - allow to stop a running process
</b></details>

<details>
<summary>How a process is created?</summary><br><b>

* The OS is reading program's code and any additional relevant data
* Program's code is loaded into the memory or more specifically, into the address space of the process.
* Memory is allocated for program's stack (aka run-time stack). The stack also initialized by the OS with data like argv, argc and parameters to main()
* Memory is allocated for program's heap which is required for dynamically allocated data like the data structures linked lists and hash tables
* I/O initialization tasks are performed, like in Unix/Linux based systems, where each process has 3 file descriptors (input, output and error)
* OS is running the program, starting from main()
</b></details>

<details>
<summary>True or False? The loading of the program into the memory is done eagerly (all at once)</summary><br><b>

False. It was true in the past but today's operating systems perform lazy loading, which means only the relevant pieces required for the process to run are loaded first.
</b></details>

<details>
<summary>What are different states of a process?</summary><br><b>

* Running - it's executing instructions
* Ready - it's ready to run, but for different reasons it's on hold
* Blocked - it's waiting for some operation to complete, for example I/O disk request
</b></details>

<details>
<summary>What are some reasons for a process to become blocked?</summary><br><b>

  - I/O operations (e.g. Reading from a disk)
  - Waiting for a packet from a network
</b></details>

<details>
<summary>What is Inter Process Communication (IPC)?</summary><br><b>

Inter-process communication (IPC) refers to the mechanisms provided by an operating system that allow processes to manage shared data.
</b></details>

<details>
<summary>What is "time sharing"?</summary><br><b>

Even when using a system with one physical CPU, it's possible to allow multiple users to work on it and run programs. This is possible with time sharing, where computing resources are shared in a way it seems to the user, the system has multiple CPUs, but in fact it's simply one CPU shared by applying multiprogramming and multi-tasking.
</b></details>

<details>
<summary>What is "space sharing"?</summary><br><b>

Somewhat the opposite of time sharing. While in time sharing a resource is used for a while by one entity and then the same resource can be used by another resource, in space sharing the space is shared by multiple entities but in a way where it's not being transferred between them.<br>
It's used by one entity, until this entity decides to get rid of it. Take for example storage. In storage, a file is yours, until you decide to delete it.
</b></details>

<details>
<summary>What component determines which process runs at a given moment in time?</summary><br><b>

CPU scheduler
</b></details>

#### Operating System - Memory

<details>
<summary>What is "virtual memory" and what purpose does serve?</summary><br><b>

Virtual memory combines your computer's RAM with temporary space on your hard disk. When RAM runs low, virtual memory helps to move data from RAM to a space called a paging file. Moving data to paging file can free up the RAM, so your computer can complete its work. In general, the more RAM your computer has, the faster the programs run.
https://www.minitool.com/lib/virtual-memory.html
</b></details>

<details>
<summary>What is demand paging?</summary><br><b>

Demand paging is a memory management technique where pages are loaded into physical memory only when accessed by a process. It optimizes memory usage by loading pages on demand, reducing startup latency and space overhead. However, it introduces some latency when accessing pages for the first time. Overall, it’s a cost-effective approach for managing memory resources in operating systems. 
</b></details>

<details>
<summary>What is copy-on-write?</summary><br><b>
Copy-on-write (COW) is a resource management concept, with the goal to reduce unnecessary copying of information. It is a concept, which is implemented for instance within the POSIX fork syscall, which creates a duplicate process of the calling process.

The idea:
1. If resources are shared between 2 or more entities (for example shared memory segments between 2 processes), the resources don't need to be copied for every entity, but rather every entity has a READ operation access permission on the shared resource. (the shared segments are marked as read-only) 
(Think of every entity having a pointer to the location of the shared resource, which can be dereferenced to read its value)
2. If one entity would perform a WRITE operation on a shared resource, a problem would arise, since the resource also would be permanently changed for ALL other entities sharing it.
(Think of a process modifying some variables on the stack, or allocatingy some data dynamically on the heap, these changes to the shared resource would also apply for ALL other processes, this is definitely an undesirable behaviour)
3. As a solution only, if a WRITE operation is about to be performed on a shared resource, this resource gets COPIED first and then the changes are applied.
</b></details>

<details>
<summary>What is a kernel, and what does it do?</summary><br><b>

The kernel is part of the operating system and is responsible for tasks like:

  * Allocating memory
  * Schedule processes
  * Control CPU
</b></details>

<details>
<summary>True or False? Some pieces of the code in the kernel are loaded into protected areas of the memory so applications can't overwrite them.</summary><br><b>

True
</b></details>

<details>
<summary>What is POSIX?</summary><br><b>

POSIX (Portable Operating System Interface) is a set of standards that define the interface between a Unix-like operating system and application programs.
</b></details>

<details>
<summary>Explain what is Semaphore and what its role in operating systems.</summary><br><b>

A semaphore is a synchronization primitive used in operating systems and concurrent programming to control access to shared resources. It's a variable or abstract data type that acts as a counter or a signaling mechanism for managing access to resources by multiple processes or threads.
</b></details>

<details>
<summary>What is cache? What is buffer?</summary><br><b>

Cache: Cache is usually used when processes are reading and writing to the disk to make the process faster, by making similar data used by different programs easily accessible.
Buffer: Reserved place in RAM, which is used to hold data for temporary purposes.
</b></details>

## Virtualization

<details>
<summary>What is Virtualization?</summary><br><b>

Virtualization uses software to create an abstraction layer over computer hardware, that allows the hardware elements of a single computer - processors, memory, storage and more - to be divided into multiple virtual computers, commonly called virtual machines (VMs).
</b></details>

<details>
<summary>What is a hypervisor?</summary><br><b>

Red Hat: "A hypervisor is software that creates and runs virtual machines (VMs). A hypervisor, sometimes called a virtual machine monitor (VMM), isolates the hypervisor operating system and resources from the virtual machines and enables the creation and management of those VMs."

Read more [here](https://www.redhat.com/en/topics/virtualization/what-is-a-hypervisor)
</b></details>

<details>
<summary>What types of hypervisors are there?</summary><br><b>

Hosted hypervisors and bare-metal hypervisors.
</b></details>

<details>
<summary>What are the advantages and disadvantges of bare-metal hypervisor over a hosted hypervisor?</summary><br><b>

Due to having its own drivers and a direct access to hardware components, a baremetal hypervisor will often have better performances along with stability and scalability.

On the other hand, there will probably be some limitation regarding loading (any) drivers so a hosted hypervisor will usually benefit from having a better hardware compatibility.
</b></details>

<details>
<summary>What types of virtualization are there?</summary><br><b>

Operating system virtualization
Network functions virtualization
Desktop virtualization
</b></details>

<details>
<summary>Is containerization is a type of Virtualization?</summary><br><b>

Yes, it's a operating-system-level virtualization, where the kernel is shared and allows to use multiple isolated user-spaces instances.
</b></details>

<details>
<summary>How the introduction of virtual machines changed the industry and the way applications were deployed?</summary><br><b>

The introduction of virtual machines allowed companies to deploy multiple business applications on the same hardware, while each application is separated from each other in secured way, where each is running on its own separate operating system.
</b></details>

#### Virtual Machines

<details>
<summary>Do we need virtual machines in the age of containers? Are they still relevant?</summary><br><b>

Yes, virtual machines are still relevant even in the age of containers. While containers provide a lightweight and portable alternative to virtual machines, they do have certain limitations. Virtual machines still matter because they offer isolation and security, can run different operating systems, and are good for legacy apps. Containers limitations for example are sharing the host kernel.
</b></details>
