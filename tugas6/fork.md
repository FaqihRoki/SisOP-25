# TUGAS SISTEM OPERASI 6

---

![Image](https://github.com/user-attachments/assets/838b068c-4d85-452a-aca6-352d279fbd3f)

#### Dosen Pengampu :
**Dr. Ferry Astika Saputra ST, M.Sc**

#### Disusun oleh :
**Abdullah Faqih**
**(3124521026)**
D3-LA IT-A

<br>


# FORK: PARENT - CHILD PROCESS

## Assignment:
- Access and clone repository: [github.com/ferryastika/operatingsystem.git](https://github.com/ferryastika/operatingsystem.git)
- Describe and visualize the process trees resulting from the execution of the following code:
  - `fork01.c`
  - `fork02.c`
  - `fork03.c`
  - `fork04.c`
  - `fork05.c`
  - `fork06.c`

## 1. fork01.c
This program implements **First-Come, First-Served (FCFS) Scheduling** to calculate waiting time and turnaround time based on user-provided burst times.

### Process Tree Visualization:
```
Main()
│
├── Input Number of Processes
│
├── Loop to Input Burst Times
│   ├── P1: Burst Time
│   ├── P2: Burst Time
│   ├── P3: Burst Time
│
├── Calculate Waiting Time (WT)
│   ├── P1: WT = 0
│   ├── P2: WT = BT[P1]
│   ├── P3: WT = BT[P1] + BT[P2]
│
├── Calculate Turnaround Time (TAT)
│   ├── P1: TAT = BT[P1] + WT[P1]
│   ├── P2: TAT = BT[P2] + WT[P2]
│   ├── P3: TAT = BT[P3] + WT[P3]
│
└── Calculate average WT and TAT → Output Data → Finish
```

## 2. fork02.c
This program uses the `fork()` system call to create a child process from a running parent process.

### Process Tree Visualization:
```
Parent Process (PID X) 
│
├── Fork() → Creates Child Process (PID Y)
│
├── Parent Process: Displays PID X and value of x
│    ├── x = 5, x = 6, x = 7, ...
│
├── Child Process: Displays PID Y and value of x
│    ├── x = 5, x = 6, x = 7, ...
│
└── Both processes run **forever** in while(1) loop
```
> **Note:** Both processes run **indefinitely** in the `while(1)` loop. They run concurrently but independently.

## 3. fork03.c
This program creates a child process from the parent, where each process prints its ID for five iterations with a two-second delay.

### Process Tree Visualization:
```
Parent Process (PID X) 
│
├── Fork() → Creates Child Process (PID Y)
│
├── Parent Process: Displays PID X
│    ├── Iteration 1: "This is process X"
│    ├── Iteration 2: "This is process X"
│    ├── Iteration 3: "This is process X"
│    ├── Iteration 4: "This is process X"
│    ├── Iteration 5: "This is process X"
│
├── Child Process: Displays PID Y
│    ├── Iteration 1: "This is process Y"
│    ├── Iteration 2: "This is process Y"
│    ├── Iteration 3: "This is process Y"
│    ├── Iteration 4: "This is process Y"
│    ├── Iteration 5: "This is process Y"
│
└── **Finishes after 5 iterations**
```
> **Note:** There is no synchronization, so the output order may be random depending on CPU scheduling.

## 4. fork04.c
This program uses `fork()` to create a child process, then the parent waits for the child to finish using `wait()`.

### Process Tree Visualization:
```
Parent Process (PID X)
│
├── Fork() → Creates Child Process (PID Y)
│
├── Child Process (PID Y)
│    ├── Print: "I am the child, my PID is Y"
│    ├── Print: "My parent is X"
│    ├── Exit
│
├── Parent Process (PID X)
│    ├── Print: "I am the parent, my PID is X"
│    ├── Print: "My child has PID Y"
│    ├── Wait for child to finish with `wait()`
│    ├── Exit after child finishes
```

## 5. fork05.c
This program creates a child process, which then executes a command using `execl()` to replace the process execution.

### Process Tree Visualization:
```
Parent Process (PID X)
│
├── Fork() → Creates Child Process (PID Y)
│
├── Child Process (PID Y)
│    ├── Print: "I am the child, my PID is Y"
│    ├── Execute `/bin/ls -l /home`
│    ├── Exit after execution completes
│
├── Parent Process (PID X)
│    ├── Print: "I am the parent, my PID is X"
│    ├── Print: "My child has PID Y"
│    ├── Wait for child to finish with `wait()`
│    ├── Exit after child finishes
```

## 6. fork06.c
This program attempts to execute an external program using `execl()`, and if it fails, prints an error message.

### Process Tree Visualization:
```
Parent Process (PID X)
│
├── Fork() → Creates Child Process (PID Y)
│
├── Child Process (PID Y)
│    ├── Print: "I am the child, my PID is Y"
│    ├── Execute `execl("fork03", "goose", NULL)`
│    ├── If failed, print "Could not execl file fork3" then exit
│
├── Parent Process (PID X)
│    ├── Print: "I am the parent, my PID is X"
│    ├── Print: "My child has PID Y"
│    ├── Wait for child to finish with `wait()`
│    ├── Exit after child finishes
```
