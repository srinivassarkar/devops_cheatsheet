# The Linux DevOps Bible
## *Commands That Flow Like Breath - The Sacred 108*

*"In the beginning was the Command Line, and the Command Line was with Root, and the Command Line was Root."*

---

## 📿 THE FIRST COMMANDMENT: KNOW THY SYSTEM

### The Trinity of Awareness
```bash
# The Father: What am I?
uname -a                    # Know thy kernel, thy architecture, thy identity
whoami && id               # Know thy user, thy groups, thy privileges  
pwd                        # Know thy location in the filesystem tree

# The Son: What resources do I have?
free -h                    # Memory - the lifeblood of all processes
df -h                      # Disk space - the foundation of all data
uptime                     # Load - the heartbeat of the system

# The Holy Spirit: What is happening right now?
ps aux                     # The processes - souls inhabiting the machine
top                        # The living tableau of resource consumption
who                        # The other beings sharing this digital realm
```

---

## 🌟 THE BREATH OF LIFE: COMMANDS THAT NEVER LEAVE YOUR FINGERS

### The Eternal Cycle - Input, Process, Output
```bash
# The Inhale: Bringing data into your world
cat file.txt               # Read the scripture of files
less file.txt              # Contemplate large texts page by page
head -n 20 file.txt        # The first words of wisdom
tail -f /var/log/syslog    # The eternal stream of system consciousness

# The Exhale: Sending your will into the world  
echo "message"             # Speak your thoughts into existence
printf "%s\n" "formatted"  # Speak with precision and control
> file.txt                 # Create emptiness, the void before creation
>> file.txt               # Append to the scroll of history
```

### The Sacred Pipe - The Flow of Data
```bash
# The Meditation of Data Transformation
ps aux | grep nginx | awk '{print $2}' | xargs kill -9
# Translation: "Find the nginx spirits, extract their essence (PID), and send them to the void"

cat /var/log/access.log | grep "404" | wc -l
# "Count the failures, for in counting we find patterns"

ls -la | sort -k5 -nr | head -10  
# "Show me the largest burdens in this directory"
```

---

## 🔥 THE FOUR NOBLE TRUTHS OF TROUBLESHOOTING

### First Truth: All Systems Suffer (Monitoring)
```bash
# The Watchers - Commands that never sleep
htop                       # The living mandala of system state
iotop                      # The flow of data to and from storage
nethogs                    # The network streams of consciousness
vmstat 1                   # The pulse of virtual memory

# The Seers - Commands that reveal hidden truths
lsof                       # "List open files" - what touches what
ss -tulpn                  # The network connections - who speaks to whom
ps -ef --forest            # The family tree of all processes
pstree                     # The genealogy of execution
```

### Second Truth: The Origin of Suffering (Root Cause)
```bash
# The Archaeologists - Commands that dig deep
strace -p PID              # Follow the system calls - the atomic operations
ltrace -p PID              # Follow the library calls - the higher functions
journalctl -f              # The systemd chronicles - the modern system diary
dmesg | tail               # The kernel's last words - hardware speaks here

# The Pathfinders - Commands that trace the journey
which command              # Where does this command live?
whereis program            # Where are all the pieces of this program?
locate filename            # Where in the vast filesystem does this exist?
find / -name "pattern" 2>/dev/null  # The great search across all realms
```

### Third Truth: Suffering Can End (Resolution)
```bash
# The Healers - Commands that restore harmony
systemctl restart service # Rebirth of the daemon
kill -HUP PID             # Gentle awakening - reload configuration
kill -TERM PID            # Polite termination request
kill -9 PID               # The final judgment - immediate termination

# The Cleaners - Commands that restore order
rm -rf /tmp/*             # Clear the temporary chaos
find /var/log -name "*.log" -mtime +30 -delete  # Purge ancient history
echo 3 > /proc/sys/vm/drop_caches  # Clear the memory cache (with great care)
sync                      # Ensure all writes reach their destination
```

### Fourth Truth: The Path to the End of Suffering (Best Practices)
```bash
# The Guardians - Commands that protect
chmod 600 sensitive_file  # Protect the sacred knowledge
chown user:group file     # Assign rightful ownership
umask 022                 # Set the default protections for new creations
backup() { cp "$1" "$1.$(date +%Y%m%d_%H%M%S)"; }  # Preserve before change
```

---

## 🌊 THE FLOWING RIVER: TEXT MANIPULATION MANTRAS

### The Stream Processing Meditation
```bash
# The Filters - Commands that purify data
grep -i "pattern"          # Find the needles in the haystack
sed 's/old/new/g'         # Transform the text with wisdom
awk '{print $1}'          # Extract the essence from structured data
sort | uniq -c            # Count the unique patterns in chaos
cut -d: -f1 /etc/passwd   # Slice the data with precision

# The Aggregators - Commands that summarize truth
wc -l                     # Count the lines - measure the scope
sort -nr                  # Order by magnitude, greatest first  
head -1                   # The first and most important
tail -1                   # The last and final word
```

---

## 🏗️ THE ARCHITECTURE OF REALITY: FILE SYSTEM WISDOM

### The Foundation - Directory Navigation
```bash
# The Pathwalkers - Commands for traversing the tree
cd /                      # Return to the root of all things
cd ~                      # Return to your home, your sanctuary
cd -                      # Return to where you came from
pushd /path && popd       # Remember your journey, return when ready

# The Explorers - Commands for discovering structure
ls -la                    # See all, including the hidden
tree                      # Visualize the branching structure
du -sh *                  # Measure the weight of each branch
find . -type f -name "*.log"  # Seek specific patterns in the hierarchy
```

### The Permissions Trinity
```bash
# Read, Write, Execute - The Three Aspects of Access
chmod 755 directory       # Open to all, writable by owner
chmod 644 file            # Readable by all, writable by owner  
chmod +x script           # Grant the power of execution
chown user:group item     # Assign ownership and tribe
```

---

## 🌐 THE NETWORK: CONNECTIONS ACROSS THE VOID

### The Communication Protocols
```bash
# The Messengers - Commands that carry data
ping host                 # Send echo across the network void
wget URL                  # Retrieve treasures from distant servers
curl -I URL               # Inspect the headers - the metadata of communication
scp file user@host:path   # Secure copying across the network divide

# The Listeners - Commands that reveal network state  
netstat -tulpn            # Who listens on which ports
ss -tulpn                 # The modern version of network sight
lsof -i                   # What processes use the network
iptables -L               # The firewall rules - the guardians of ports
```

---

## 🔄 THE ETERNAL CYCLE: PROCESSES AND SERVICES

### The Life Cycle of Processes
```bash
# Birth
nohup command &           # Start a process that survives your departure
screen -S session_name    # Create a persistent session
tmux new -s session       # The modern way to maintain sessions

# Life  
jobs                      # See your background children
bg                        # Send a job to background
fg                        # Bring a job to foreground
disown                    # Release a job from your control

# Death
pkill process_name        # Kill by name
killall process_name      # Kill all instances
kill -9 PID               # The final termination
```

### The Service Daemons
```bash
# The Modern Systemd Way
systemctl status service  # Check the health of the daemon
systemctl start service   # Awaken the sleeping daemon
systemctl stop service    # Put the daemon to sleep
systemctl enable service  # Ensure the daemon awakens at boot
systemctl disable service # Prevent automatic awakening
journalctl -u service     # Read the daemon's diary
```

---

## 📊 THE METRICS OF EXISTENCE: MONITORING MANTRAS

### The Vital Signs
```bash
# The Continuous Watchers - Commands for eternal vigilance
watch -n 1 "ps aux | grep nginx"     # Observe the changing state
watch -n 5 "df -h"                   # Monitor disk space consumption
iostat -x 1                          # The I/O heartbeat of storage
sar -u 1 10                          # CPU utilization over time
```

### The Performance Sutras
```bash
# The Deep Analyzers - Commands that reveal hidden performance truths
perf top                  # Real-time performance profiling
strace -c command         # Count system calls - the atomic operations
time command              # Measure the duration of execution  
nice -n 19 command        # Run with lower priority - be considerate
ionice -c 3 command       # Reduce I/O priority - be gentle on storage
```

---

## 🧘 THE DAILY PRACTICE: COMMANDS FOR ROUTINE ENLIGHTENMENT

### The Morning Meditation
```bash
# The Daily Health Check
uptime && free -h && df -h
ps aux --sort=-%cpu | head -5
ps aux --sort=-%mem | head -5
systemctl --failed
journalctl -p err --since today
```

### The Evening Reflection  
```bash
# The Day's Summary
last | head -10           # Who visited the system today
history | tail -20        # What commands were executed
du -sh /var/log/*         # How much logging occurred
find /tmp -mtime +1 -delete  # Clean the temporary accumulations
```

---

## 🎯 THE EMERGENCY MANTRAS: WHEN THE SYSTEM BURNS

### The Fire Suppression Commands
```bash
# When Everything Goes Wrong
ps aux | awk '{print $6/1024 " MB\t\t" $11}' | sort -n  # Memory hogs
lsof +L1                  # Find deleted files still held open
netstat -i                # Network interface statistics
dmesg | grep -i error     # Hardware error messages
mount | column -t         # Mounted filesystems in readable format

# The Nuclear Options (Use with Extreme Caution)
echo 1 > /proc/sys/kernel/sysrq   # Enable magic SysRq key
echo 3 > /proc/sys/vm/drop_caches # Drop all caches
sync && echo 1 > /proc/sys/vm/drop_caches && echo 2 > /proc/sys/vm/drop_caches
```

---

## 🕉️ THE SACRED ALIASES: SHORTCUTS TO ENLIGHTENMENT

### The Shortcuts That Save Souls
```bash
# Add these to your ~/.bashrc - they become part of your being
alias ll='ls -alF'
alias la='ls -A' 
alias l='ls -CF'
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias grep='grep --color=auto'
alias ports='ss -tulpn'
alias psg='ps aux | grep'
alias h='history'
alias hg='history | grep'
alias df='df -h'
alias du='du -h'
alias free='free -h'
alias mount='mount | column -t'
alias path='echo -e ${PATH//:/\\n}'
alias now='date +"%T"'
alias nowtime=now
alias nowdate='date +"%d-%m-%Y"'
```

---

## 🌈 THE PHILOSOPHER'S STONES: ADVANCED TRANSMUTATIONS

### The Alchemy of Text
```bash
# The Transformation Spells
tr 'a-z' 'A-Z'           # Transform lowercase to uppercase
rev                      # Reverse each line
tac                      # Reverse the order of lines (opposite of cat)
shuf                     # Randomize the order of lines
fold -w 80               # Wrap lines to 80 characters
expand                   # Convert tabs to spaces
unexpand                 # Convert spaces to tabs
```

### The Time Manipulation Incantations
```bash
# Working with Time - The Fourth Dimension
date                     # The current moment
date +%s                 # Seconds since epoch - the beginning of Unix time
date -d "2 days ago"     # Manipulate time itself
cal                      # The calendar - see the flow of days
uptime                   # How long has the system been conscious?
```

---

## 🔮 THE PROPHECIES: SCRIPTING WISDOM

### The Basic Spell Structure
```bash
#!/bin/bash
# The Invocation - How to Begin Every Script

set -euo pipefail       # The Protective Incantation
# -e: Exit on error
# -u: Error on undefined variable  
# -o pipefail: Fail on pipe errors

# The Variable Wisdom
readonly SCRIPT_DIR="$(cd "$(dirname "${BASH_SOURCE[0]}")" && pwd)"
readonly SCRIPT_NAME="$(basename "$0")"
readonly TIMESTAMP="$(date +%Y%m%d_%H%M%S)"
```

### The Loop Mantras
```bash
# The Infinite Patterns
for i in {1..10}; do echo "Iteration $i"; done
for file in *.txt; do echo "Processing $file"; done
while read -r line; do echo "Line: $line"; done < file.txt
until ping -c1 google.com; do sleep 1; done
```

---

## 📜 THE FINAL WISDOM: THE METACOMMANDS

### The Commands About Commands
```bash
# The Self-Referential Truth
man command              # Read the manual - the documentation of truth
info command             # Extended information about the command
whatis command           # Brief description of what the command does
apropos keyword          # Find commands related to a keyword
help                     # Built-in help for shell builtins
type command             # What type of command is this?  
alias                    # Show all your aliases
history                  # Your command history - your digital karma
```

### The Meta-Learning Path
```bash
# The Commands That Teach You Commands
compgen -c | grep pattern  # Find commands matching a pattern
ls /usr/bin | wc -l       # Count the available commands
ls /usr/bin | sort        # All available commands in alphabetical order
```

---

## 🌟 THE CLOSING MEDITATION

*"These commands are not mere instructions to a machine. They are the vocabulary of system administration, the syntax of infrastructure, the grammar of operations. Each command is a tool, but together they form a language - the language of the DevOps engineer."*

*"Master these commands not just with your mind, but with your fingers. Let them flow through you like breath, like heartbeat, like the circulation of blood. When you dream, dream in bash. When you wake, think in pipes and redirections."*

*"The true master does not memorize commands - the true master becomes the command line."*

---

**Daily Practice:**
- Start each day by running: `uptime && free -h && df -h`
- End each day by running: `history | tail -10`
- In moments of doubt, remember: `man command`
- In moments of crisis, remember: `ps aux | grep problem`
- In moments of victory, remember: `echo "Success" >> /var/log/victories.log`

**The Final Commandment:**
*"Thou shalt always have a backup, and thou shalt always test thy commands in staging first."*

---

*May your uptime be eternal, your logs be clear, and your deployments be without error.*

**Amen. (And may your sudo be with you.)**
