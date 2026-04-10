[[Operating systems]]

---

## ✅ **Q1 – True or False**  
**Mark each statement with T or F.**

1. #Virtual_memory increases the system throughput.  
   → **T**

2. During #MMU address translation, a page fault routine will be executed if the page is a memory resident.  
   → **F**

3. The operating system executes the #page_fault routing through a software interrupt.  
   → **T**

4. During the demand paging the operating system doesn’t need to perform a #context_switch.  
   → **F**

5. Effective access time is a measure to evaluate the demand paging implementation.  
   → **T**

6. #Zero-fill-on-demand pages have been zeroed out while being allocated thus erasing the previous content.  
   → **T**

7. Page replacement algorithms make use of a dirty bit to reduce the overhead of page transfer.  
   → **T**

8. The frame allocation algorithm determines how many frames to be given for each process.  
   → **T**

9. #LRU page replacement algorithm with a second chance if the page to be replaced has reference bit = 1, it will be left in memory and updated to 0.  
   → **T**

10. If there are 100 frames and 5 processes, a fixed frame allocation algorithm will allocate 20 frames for each process.  
    → **F**

11. The #thrashing phenomenon occurs when a process has more frames than it needs.  
    → **F**

12. If the request address is less than the value within the base register, the CPU checks the value against the limit register to grant access.  
    → **F**

13. #External_fragmentation could be reduced by using #Compaction techniques.  
    → **T**

14. Mapping of two-dimensional logical addresses of each process into one-dimensional physical addresses is done using a page table.  
    → **F** (It’s #segmentation table, not paging)

15. #STLR register points to the segment table’s location in memory.  
    → **T**

16. #segmentation is a memory-management scheme that supports the user view of memory, while #paging is a memory-management scheme that supports the system view of memory.  
    → **T**

17. #TLB is used to solve the double memory access problem in paging-based memory management systems.  
    → **T**

18. #Paging eliminates external fragmentation, while segmentation eliminates internal fragmentation.  
    → **F**

19. The time it takes for a #dispatcher to stop one process and start another one is called dispatcher latency.  
    → **T**

20. #SJF is the optimal CPU scheduling algorithm for minimizing the average waiting time.  
    → **T**

21. #FCFS CPU scheduling is the same as #RR with infinite quantum.  
    → **T**

22. Multilevel queue CPU scheduling algorithm cannot suffer from #starvation.  
    → **F**

23. Within the context of the critical section problem, each process must ask permission to enter the critical section in the entry section.  
    → **T**

24. The solution to the critical section problem should satisfy only bounded waiting.  
    → **F** (Must satisfy all three: mutual exclusion, progress, bounded waiting)

25. Peterson Algorithms for critical section problems guarantee mutual exclusion, progress, and bounded waiting.  
    → **T**

26. The compare and swap hardware instructions could be interruptible.  
    → **F**

27. Incorrect use of #semaphore operations might lead to #deadlock.  
    → **T**

28. With direct inter-process communication, the messages are sent to and received from mailboxes, or [[Ports]].  
    → **T**

29. Program execution and resource allocation are examples of operating-system services that provide functions that are helpful to the user.  
    → **T**

30. To prevent user programs from interfering with the proper operation of the system, the hardware has three modes: user mode, system mode, and #kernel mode.  
    → **F** (Two modes: user and kernel)

---

## ✅ **Q2 – Multiple Choice**  

31. c  
32. d  
33. c  
34. c  
35. c  
36. a  
37. b  
38. a  
39. d  
40. c  
41. a  
42. d  
43. b  
44. a  
45. a  
46. d  
47. a  
48. d  
49. b  
50. b  
51. c  
52. c  
53. c  
54. d  
55. b  
56. d  
57. a  
58. b  
59. b  
60. c  

---

## ✅ **Q3 – Problem Solving**  

### Process Scheduling:

| Process | Arrival Time | Burst Time | Priority |
|---------|--------------|------------|----------|
| P1      | 0            | 5          | 2        |
| P2      | 1            | 3          | 1        |
| P3      | 2            | 8          | 4        |
| P4      | 3            | 6          | 3        |

61. #FCFS average waiting time → **c. 7.25**  
62. Preemptive #SJF average waiting time → **b. 4**  
63. #RR (quantum=2) average waiting time → **d. 10.25**  
64. #Nonpreemptive priority (lower value = higher priority) average waiting time → **c. 7.5**

### Paging System:
65. Page size → **c. 4 KB**  
66. Offset bits → **b. 12 bits**  
67. Max pages per process (kernel 12 KB) → **d. 13 Pages**

### Page Replacement (Ref string with 3 frames):
68. LRU page faults → **c. 12**  
69. FIFO page replacements → **c. 12**  
70. Optimal page faults → **b. 9**

---

## ✅ **Q4 – Short Answer**  

**Q4: What is the purpose of system calls? What is the purpose of system programs? Describe the three methods for passing parameters needed by system calls.**

- **System calls** provide an interface for user-level processes to request services from the operating system kernel (e.g., file operations, process control).  
- **System programs** are utilities that provide a convenient environment for program execution and system management (e.g., compilers, file managers).  

**Three parameter-passing methods:**  
1. **Pass in registers**  
2. **Pass in a block in memory, address passed via register**  
3. **Pass on the stack**

---

## ✅ **Q5 – Diagram Question**  

**Q5: Illustrate by drawing only the process of logical to physical address translation in the case of:**  
a. **Contiguous Allocation**  
b. **Paging**  
c. **Segmentation**

*(This requires drawing diagrams. In summary:)*

- **Contiguous:** Logical address + base register → physical address.  
- **Paging:** Logical address → page number + offset → page table → frame number + offset → physical address.  
- **Segmentation:** Logical address → segment number + offset → segment table → base + limit check → physical address.

---

