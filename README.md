# 🖥️ Operating System Simulator Suite

![Status](https://img.shields.io/badge/Status-Active_Development-success) ![Language](https://img.shields.io/badge/Languages-Python_%7C_C-blue) ![Domain](https://img.shields.io/badge/Domain-System_Programming_%7C_Kernel_Simulation-orange)

**Author:** Niyati Bansal  
**Role:** Computer Engineering Student & Placement Coordinator @ NMIMS  

---

## 📖 Project Abstract

This repository houses a comprehensive **Operating System Simulator**, a technical portfolio designed to bridge the gap between theoretical OS concepts and practical implementation. Unlike standard simulation tools, this suite combines **low-level C programming** for kernel operations with **high-level Python visualization** for performance analysis.

The primary objective is to simulate the lifecycle of an Operating System, demonstrating proficiency in:
* **Process Management:** Algorithmically scheduling tasks to optimize CPU utilization.
* **Memory Architecture:** Managing fragmentation and virtual memory paging.
* **Concurrency Control:** Preventing race conditions and deadlocks in multi-threaded environments.
* **I/O Optimization:** Reducing disk seek times through advanced scheduling algorithms.

---

## 🏗️ Architectural Modules

The project is structured into five distinct engineering modules, each targeting a specific subsystem of an Operating System.

### 1. CPU Scheduling Engine
* **Directory:** `01_CPU_Scheduler_Visualizer`
* **Core Function:** Simulates the Short-Term Scheduler (CPU Scheduler) to decide which ready process executes next.
* **Algorithms Implemented:**
    * **FCFS (First-Come, First-Served):** Non-preemptive implementation using a FIFO queue.
    * **SJF (Shortest Job First):** Minimizes waiting time by selecting the process with the smallest burst time.
    * **Round Robin:** Preemptive scheduling using a configurable Time Quantum (TQ) to ensure fairness.
    * **Priority Scheduling:** Handles high-priority tasks first to simulate real-time system requirements.
* **Visualization:** Uses `Matplotlib` to render **Gantt Charts**, providing a visual timeline of context switches and burst durations.

### 2. Memory Management Unit (MMU)
* **Directory:** `02_Memory_Manager`
* **Core Function:** Simulates the allocation of RAM to processes and handles Virtual Memory paging.
* **Allocation Strategies:**
    * **First Fit:** Scans memory from the beginning for the first sufficiently large hole.
    * **Best Fit:** Searches the entire list for the smallest hole that is big enough (minimizes internal fragmentation).
    * **Worst Fit:** Allocates the largest available hole.
* **Page Replacement:** Implements **LRU (Least Recently Used)** and **FIFO** algorithms to handle Page Faults when physical memory is full.

### 3. Concurrency & Deadlock Prevention
* **Directory:** `03_Concurrency_and_Deadlocks`
* **Core Function:** Manages multi-threaded execution and resource sharing.
* **Key Implementations:**
    * **Producer-Consumer Problem:** Solved using **Semaphores** and **Mutex Locks** in C (`pthread.h`) to synchronize access to a shared bounded buffer.
    * **Banker's Algorithm:** A resource allocation and deadlock avoidance algorithm that tests for safety by simulating the allocation of predetermined maximum possible amounts of all resources.

### 4. Disk I/O Optimizer
* **Directory:** `04_Disk_Optimizer_Visualizer`
* **Core Function:** Optimizes the movement of the disk arm (read/write head) to service I/O requests efficiently.
* **Algorithms Implemented:**
    * **FCFS:** Services requests in order. High seek time but fair.
    * **SSTF (Shortest Seek Time First):** Selects the request closest to the current head position.
    * **SCAN (Elevator Algorithm):** The arm moves in one direction, servicing requests until it reaches the end, then reverses.
    * **C-SCAN (Circular SCAN):** Similar to SCAN, but treats the cylinders as a circular list.
* **Visualization:** Plots "Zig-Zag" seek graphs to visually compare the total head movement (seek time) of different algorithms.

### 5. System Internals (Kernel Interface)
* **Directory:** `05_System_Internals`
* **Core Function:** Direct interaction with the Linux Kernel via System Calls.
* **Features:**
    * **Process Spawning:** Using `fork()` to create child processes and `exec()` to replace process images.
    * **File Descriptors:** Low-level file manipulation using `open()`, `read()`, and `write()`.
    * **Pipes:** Inter-process communication (IPC) implementation.

---

## 🛠️ Technology Stack

| Component | Technology Used | Use Case |
| :--- | :--- | :--- |
| **Logic Core** | **C (GCC Compiler)** | Memory management pointers, pthreads, system calls. |
| **Visualization** | **Python (Matplotlib, Pandas)** | Rendering Gantt charts and Disk Seek graphs. |
| **Concurrency** | **POSIX Threads (`pthread`)** | Implementing thread safety and synchronization. |
| **Build System** | **Make / Shell Scripts** | Automating compilation and execution. |

---

## ⚡ Installation & Execution Guide

Follow these steps to deploy and test the simulator on your local machine.

### Prerequisites
1.  **GCC Compiler:** Required for compiling C modules.
    * *Linux:* `sudo apt install build-essential`
    * *Windows:* Install MinGW.
2.  **Python 3.x:** Required for visualizers.
    * *Dependencies:* `pip install matplotlib pandas`

### Step 1: Run CPU Scheduler (Python)
```bash
cd 01_CPU_Scheduler_Visualizer
python main.py

Step 2: Run Memory Manager (C)
Bash
cd 02_Memory_Manager
gcc allocation_strategies.c -o memory_sim
./memory_sim

Step 3: Run Concurrency Demo (C)
Bash
cd 03_Concurrency_and_Deadlocks
gcc producer_consumer.c -o thread_sim -lpthread
./thread_sim

Step 4: Run Disk Optimizer (Python)
Bash
cd 04_Disk_Optimizer_Visualizer
python visualize_disk.py
