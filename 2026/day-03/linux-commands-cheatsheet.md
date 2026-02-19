# Day 03 – Linux Commands Cheat Sheet (DevOps Edition)

---

## 🧠 Process Management

- `ps aux` – List all running processes with CPU/memory usage  
- `top` – Real-time process and resource monitoring  
- `htop` – Enhanced interactive process viewer (if installed)  
- `pidof nginx` – Get PID of a running process  
- `kill <pid>` – Gracefully stop a process  
- `kill -9 <pid>` – Force kill a stuck process (last resort)  
- `pkill nginx` – Kill process by name  
- `uptime` – System load average & running time  

---

## 📁 File System & Disk

- `ls -lh` – List files with human-readable sizes  
- `du -sh /var/log` – Check size of a directory  
- `df -h` – Disk usage by filesystem  
- `find /var -type f -size +100M` – Find large files  
- `chmod 755 file.sh` – Change file permissions  
- `chown user:group file` – Change ownership  
- `stat file` – Detailed file info  
- `mount` – Show mounted filesystems  

---

## 📄 Logs & Debugging

- `tail -f /var/log/syslog` – Live log streaming  
- `journalctl -xe` – View system errors  
- `journalctl -u nginx` – Logs for a specific service  
- `grep -i error /var/log/syslog` – Search errors in logs  

---

## 🌐 Networking & Connectivity (Troubleshooting)

- `ping google.com` – Check basic connectivity  
- `ip addr` – Show IP ad

