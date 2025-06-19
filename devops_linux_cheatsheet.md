# DevOps Linux Commands Cheatsheet - Daily Survival Guide


## 🔥 SYSTEM MONITORING - The Holy Trinity

### Process & Resource Monitoring
```bash
# The Big 4 - Check these every damn day
htop                           # Interactive process viewer (better than top)
iotop                          # I/O usage by process
nethogs                        # Network usage by process  
iftop                          # Network bandwidth by connection

# Quick system overview
vmstat 1 5                     # VM stats every 1sec, 5 times
iostat -x 1                    # Extended I/O stats
sar -u 1 10                    # CPU utilization over time
uptime && free -h && df -h     # The trinity: load, memory, disk

# Process hunting
ps aux --sort=-%cpu | head -10 # Top CPU consumers
ps aux --sort=-%mem | head -10 # Top memory hogs
pgrep -f "java.*elasticsearch" # Find processes by pattern
kill -9 $(pgrep -f "stuck_process") # Nuclear option
```

### Memory Deep Dive
```bash
# Memory investigation arsenal  
cat /proc/meminfo | grep -E "(MemTotal|MemFree|MemAvailable|Cached|Buffers)"
echo 3 > /proc/sys/vm/drop_caches  # Clear page cache (careful!)
slabtop                        # Kernel slab allocator info
pmap -x PID                    # Memory map of process
smem -t -k                     # Memory usage with swap
```

## 🚨 LOG ANALYSIS - Where Dreams Go to Die

### The Log Whisperer Commands
```bash
# Tail like a boss
tail -f /var/log/syslog | grep -i error
multitail /var/log/nginx/access.log /var/log/nginx/error.log
journalctl -f -u nginx.service # systemd service logs

# Log archaeology 
zgrep "ERROR" /var/log/app/*.gz | tail -1000  # Search compressed logs
grep -r "OutOfMemory" /var/log/ --include="*.log"
awk '{print $1}' /var/log/nginx/access.log | sort | uniq -c | sort -nr | head
sed -n '1000,2000p' massive_log_file.log      # Extract specific lines

# Log analysis magic
cut -d' ' -f1 access.log | sort | uniq -c | sort -nr  # Top IPs
awk '$9 ~ /^5/ {print $0}' access.log         # 5xx errors only
grep -E "$(date '+%b %d')" /var/log/syslog    # Today's logs
```

## 📁 FILE SYSTEM WIZARDRY

### Disk Space Management
```bash
# Disk space hunters
du -h --max-depth=1 | sort -hr  # Disk usage by directory
find / -type f -size +100M 2>/dev/null | head -20  # Big files
find /var/log -name "*.log" -mtime +30 -delete     # Cleanup old logs
ncdu /                          # Interactive disk usage analyzer

# File operations at scale
find . -name "*.tmp" -mtime +7 -exec rm {} \;
rsync -avz --progress /source/ /dest/  # Sync with progress
tar czf backup_$(date +%Y%m%d).tar.gz /important/data/
```

### File Permissions & Ownership
```bash
# Permission kung fu
find /var/www -type f -exec chmod 644 {} \;  # Files to 644
find /var/www -type d -exec chmod 755 {} \;  # Dirs to 755
chown -R www-data:www-data /var/www/
chmod +x script.sh && ./script.sh            # Make executable and run
```

## 🌐 NETWORK TROUBLESHOOTING

### Network Diagnostics
```bash
# Connection debugging
ss -tuln                       # Modern netstat replacement
netstat -tulpn | grep :80      # What's using port 80
lsof -i :8080                  # What process owns port 8080
nmap -sS -p 1-1000 target_ip   # Port scan

# Network performance
iperf3 -s                      # Start iperf server
iperf3 -c server_ip -t 30      # Client test for 30 seconds
mtr google.com                 # Enhanced traceroute
tcpdump -i eth0 port 80 -w capture.pcap  # Packet capture

# DNS & Connectivity
dig +short google.com @8.8.8.8  # DNS lookup
nslookup -type=MX domain.com     # Mail exchange records
curl -I -w "@curl-format.txt" http://site.com  # Response time analysis
```

## 🔧 SYSTEM ADMINISTRATION

### Service Management (systemd)
```bash
# Service control mastery
systemctl status nginx         # Service status
systemctl restart nginx       # Restart service
systemctl enable nginx        # Enable at boot
systemctl list-units --failed # Failed services
journalctl -u nginx -n 50     # Last 50 lines of service logs
systemctl daemon-reload       # Reload systemd configs
```

### User & Security Management
```bash
# User operations
sudo -u appuser whoami         # Run as different user
last | head -20                # Recent logins
w                              # Who's logged in and what they're doing
passwd username                # Change password
usermod -aG docker username    # Add user to group
```

## 🐳 CONTAINER & ORCHESTRATION

### Docker Operations
```bash
# Docker essentials (even though we're Kubernetes now)
docker ps -a --format "table {{.Names}}\t{{.Status}}\t{{.Ports}}"
docker logs -f --tail=100 container_name
docker exec -it container_name /bin/bash
docker system prune -a        # Clean up everything
docker stats --no-stream     # Resource usage snapshot
```

### Kubernetes Quick Hits
```bash
# K8s daily operations
kubectl get pods -o wide --all-namespaces
kubectl describe pod pod-name -n namespace
kubectl logs -f deployment/app-name -n production
kubectl top nodes && kubectl top pods
kubectl get events --sort-by=.metadata.creationTimestamp
```

## 📊 PERFORMANCE TUNING

### System Performance Analysis
```bash
# Performance investigation toolkit
perf top                       # Real-time performance counter
strace -p PID                  # System call tracing
ltrace -p PID                  # Library call tracing
tcpdump -i any -c 100 -w dump.pcap  # Network packet analysis

# I/O Performance
iotop -oPa                     # I/O by process (accumulated)
iostat -x 1                    # Extended I/O statistics
dstat -cdngy                   # Comprehensive resource stats
```

## 🔍 TEXT PROCESSING MASTERY

### Advanced Text Manipulation
```bash
# The text processing arsenal
awk -F',' '{sum+=$3} END {print sum}' data.csv  # Sum column 3
sed 's/old_string/new_string/g' file.txt        # Replace all occurrences
sort -k2 -nr file.txt          # Sort by 2nd column, numeric, reverse
uniq -c sorted_file.txt        # Count unique lines
tr '[:lower:]' '[:upper:]' < file.txt  # Convert to uppercase

# JSON processing (because everything is JSON now)
cat api_response.json | jq '.data[] | select(.status == "active")'
curl -s api.endpoint.com/data | jq -r '.results[].name'
```

## 🚀 AUTOMATION & SCRIPTING

### Bash Scripting Essentials
```bash
# Script debugging
bash -x script.sh             # Debug mode
set -euo pipefail             # Strict error handling in scripts

# Useful one-liners for automation
for i in {1..10}; do echo "Server-$i"; done
while read line; do process_line "$line"; done < input.file
find /path -name "*.log" -exec grep -l "ERROR" {} \;
```

## 💡 PRO TIPS FROM THE TRENCHES

### Aliases That Save Your Sanity
```bash
# Add these to your ~/.bashrc
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'
alias ..='cd ..'
alias ...='cd ../..'
alias grep='grep --color=auto'
alias ports='netstat -tulanp'
alias meminfo='free -m -l -t'
alias psg='ps aux | grep -v grep | grep -i -e VSZ -e'
alias histg='history | grep'
alias myip='curl http://ipecho.net/plain; echo'
alias logs='find /var/log -name "*.log" | xargs ls -la'
```

### Emergency Response Commands
```bash
# When everything is on fire 🔥
ps aux | awk '{print $6/1024 " MB\t\t" $11}' | sort -n  # Memory usage by process
ss -i  # Socket statistics with internal TCP information
cat /proc/sys/kernel/pid_max    # Max PID limit
echo 'vm.swappiness=10' >> /etc/sysctl.conf  # Reduce swapping
sync && echo 3 > /proc/sys/vm/drop_caches    # Free up memory (CAREFUL!)
```

---

*"In DevOps, you're only as good as your last deployment. These commands have saved my ass more times than I can count across three major cloud providers. Use them wisely, and may your servers stay green." - A Slightly Obsessed DevOps Engineer*

**Remember**: With great power comes great responsibility. Always test in staging first, and never `rm -rf /` (yes, people have done this).
