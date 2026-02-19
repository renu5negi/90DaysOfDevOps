# Day 02 – Linux Architecture, Processes, and systemd

---

## 1. Core Components of Linux (High-Level View)

- **Kernel**
  - Core of the OS  
  - Manages CPU scheduling, memory, disk I/O, networking, and hardware  
  - Examples: process scheduling, file systems, network stack  

- **User Space**
  - Where applications run (nginx, docker, python, bash, etc.)  
  - Programs request services from kernel using system calls  

- **init / systemd**
  - First process started by the kernel (PID 1)  
  - Responsible for starting and managing all system services  
  - Handles service restarts, dependencies, boot sequence, logging  

---

## 2. How Processes Are Created and Managed

- A new process is created using:
  - `fork()` → creates a child process  
  - `exec()` → replaces child process with a new program  
- Each process has:
  - PID (Process ID)  
  - Parent PID (PPID)  
  - State (running, sleeping, zombie, etc.)  
- The kernel scheduler decides:
  - Which process gets CPU  
  - For how long  

---

## 3. Process States (Important for Debugging)

- **Running (R)**  
  - Process is executing on CPU  

- **Sleeping (S / D)**  
  - Waiting for I/O, network, or resource  
  - `S` = interruptible sleep  
  - `D` = uninterruptible sleep (disk I/O wait – dangerous if stuck)  

- **Stopped (T)**  
  - Paused by signal (e.g., Ctrl+Z)  

- **Zombie (Z)**  
  - Process finished execution but parent has not collected exit status  
  - Consumes no CPU, only PID table entry  

- **Orphan**
  - Parent died, child is adopted by systemd (PID 1)  

---

## 4. What systemd Does & Why It Matters

- Manages services (start, stop, restart, enable on boot)  
- Restarts crashed services automatically  
- Handles service dependencies (start DB before app)  
- Central logging using `journalctl`  
- Improves boot time with parallel service startup  

Common commands:
- `systemctl status nginx`
- `systemctl start nginx`
- `systemctl restart nginx`
- `systemctl enable nginx`
- `journalctl -u nginx`

---

## 5. 5 Linux Commands I Use Daily (DevOps)

- `ps aux` → list running processes  
- `top` / `htop` → real-time CPU & memory usage  
- `df -h` → disk usage  
- `free -m` → memory usage  
- `journalctl -xe` → system & service logs  

---

## 6. Why This Matters for DevOps

- Helps debug:
  - High CPU  
  - Memory leaks  
  - Crashed services  
  - Slow servers  
- Understanding PID 1 (systemd) helps:
  - Fix services not starting after reboot  
  - Debug restart loops  
- Process states explain:
  - Why apps hang  
  - Why servers feel slow even when CPU is free  

---

## Summary (In One Line)

If you understand **kernel + processes + systemd**,  
you can debug **80% of real production Linux issues**.

