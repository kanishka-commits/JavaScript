# OS Fundamentals Q&A 🚀  


## 📌 Table of Contents
1. [Processes & Threads](#1-processes--threads)  
2. [Scheduling & CPU Management](#2-scheduling--cpu-management)  
3. [Memory Management](#3-memory-management)  
4. [Deadlocks & Concurrency](#4-deadlocks--concurrency)  
5. [File Systems & I/O](#5-file-systems--io)  
6. [Synchronization & IPC](#6-synchronization--ipc)  
7. [General OS Concepts](#7-general-os-concepts)  

---

## 1. Processes & Threads

- **Q1. Process vs Thread?**  
  - Process → independent program with its own memory.  
  - Thread → lightweight execution inside a process, shares heap/code, own stack.  

- **Q2. What is context switching?**  
  - Saving current process state → loading next process state.  
  - Enables multitasking, but costly.  

- **Q3. What happens when you run a program?**  
  - Compile → Executable → Loader loads → OS creates process → Execution begins at `main()`.  

- **Q4. Multitasking vs Multiprocessing vs Multithreading?**  
  - Multitasking → CPU time-slicing.  
  - Multiprocessing → Multiple CPUs/cores.  
  - Multithreading → Multiple threads in one process.  

- **Q5. Can two threads share memory?**  
  - Yes → share **heap + code**, but separate **stacks**.  
    - Stack = Fast, temporary storage (function-local variables).
    - Heap = Flexible, long-lived storage (objects, dynamic memory).

---

## 2. Scheduling & CPU Management

- **Q6. Scheduling algorithm?** → OS policy to decide which process gets CPU.  

- **Q7. FCFS vs SJF vs Round Robin?**  
  - FCFS → First come, first served.  
  - SJF → Shortest burst first.  
  - RR → Fixed time slice per process.  

- **Q8. Priority scheduling & starvation?**  
  - High-priority runs first.  
  - Starvation = low-priority waits forever → solved via **Aging**. (Gradually increase the priority of a waiting process over time, thus every process eventually gets CPU time) 

- **Q9. Preemptive vs Non-preemptive?**  
  - Preemptive → OS can stop a process (e.g., RR).  
  - Non-preemptive → Process runs till done (e.g., FCFS).  

---

## 3. Memory Management

- **Q10. Stack vs Heap?**  
  - Stack → function calls, locals.  
  - Heap → dynamic memory.  

- **Q11. Virtual memory?**  
  - Abstraction → each process gets logical memory space.  

- **Q12. Paging vs Segmentation?**  
  - Paging → fixed-size blocks.  
  - Segmentation → variable-size logical blocks.  

- **Q13. Page fault?**  
  - Accessing a page not in RAM → OS loads from disk.  

- **Q14. Thrashing?**  
  - Too many page faults → CPU spends time swapping, not executing.  

---

## 4. Deadlocks & Concurrency

- **Q15. Deadlock?** → Processes wait forever for each other’s resources.  

- **Q16. Coffman’s 4 conditions:**  
  1. Mutual exclusion  
  2. Hold & wait  
  3. No preemption  
  4. Circular wait  

- **Q17. Deadlock vs Starvation vs Livelock?**  
  - Deadlock → all stuck.  
  - Starvation → some never execute.  
  - Livelock → keep changing state, no progress.  

- **Q18. Handling deadlocks?**  
  - Prevention, Detection + Recovery, Avoidance (Banker’s Algo).  

- **Q19. Mutex vs Semaphore vs Monitor?**  
  - Mutex → one thread at a time.  
  - Semaphore → counter for multiple resources.  
  - Monitor → abstraction with locks + condition vars.  

---

## 5. File Systems & I/O

- **Q20. File management?** → OS uses file system metadata (inodes/FAT).  

- **Q21. Absolute vs Relative path?**  
  - Absolute → full path from root.  
  - Relative → from current directory.  

- **Q22. Inode?** → Stores file metadata (size, perms, owner, blocks).  

- **Q23. Buffering vs Caching?**  
  - Buffering → temp storage during transfer.  
  - Caching → keep frequently accessed data.  

- **Q24. Polling vs Interrupt-driven I/O?**  
  - Polling → CPU keeps checking device.  
  - Interrupt → device notifies CPU.  

---

## 6. Synchronization & IPC

- **Q25. IPC methods?** → Pipes, Shared Memory, Message Queues, Sockets.  

- **Q26. Cooperating vs Independent process?**  
  - Cooperating → affects/is affected.  
  - Independent → no effect on others.  

- **Q27. IPC in same machine vs across network?**  
  - Same → Shared memory, Pipes.  
  - Network → Sockets.  

- **Q28. Semaphore real-world use?**  
  - Controlling multiple printers for many users.  

---

## 7. General OS Concepts

- **Q29. Kernel types?**  
  - Monolithic → all services in kernel.  
  - Microkernel → minimal kernel, rest in user space.  

- **Q30. System call?** → Program requests OS service (e.g., `fork()`, `open()`).  

- **Q31. User mode vs Kernel mode?**  
  - User → limited access.  
  - Kernel → full access.  

- **Q32. Ctrl+C in terminal?**  
  - Sends **SIGINT** signal → process terminates unless handled.  

- **Q33. Compilation vs Linking vs Loading vs Execution?**  
  - Compilation → source → object code.  
  - Linking → combine objects + libs.  
  - Loading → load into RAM.  
  - Execution → CPU runs it.  

---
