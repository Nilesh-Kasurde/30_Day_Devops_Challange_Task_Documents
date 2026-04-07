# Day 3 – Linux System Monitoring and Automated Backup Script

Day 3 – Linux System Monitoring and 
Automated Backup Script 

🎯 Objective (Why this task?) 

In real Linux servers, two things are very important: 

1.  System Monitoring 

○  CPU usage 

○  Memory (RAM) usage 

○  Disk usage 

2.  Data Backup 

○ 

Important files should be backed up regularly 

○  Backup helps recover data if something goes wrong 

👉 DevOps engineers automate both monitoring and backups instead of doing them 
manually. 

🧠 What You Will Learn in This Task 

By completing this task, you will learn: 

●  How to check CPU, memory, and disk usage in Linux 

●  How to write a Bash script for monitoring 

●  How to create automated backups using Bash 

●  How real System Admins & DevOps engineers work on servers 

 
 
 
 
 
 
 
 
 
 
 
 
 
 
🛠 Prerequisites 

Before starting: 

●  Linux OS (Ubuntu / VM / WSL / EC2) 

●  Basic terminal knowledge 

●  User with sudo access (recommended) 

🧩 Step 1: Login to Your Linux Machine 

Open terminal and login. 

Check system: 

uname -a 

🧩 Step 2: Create a Working Directory 

We will keep all scripts in one place. 

mkdir devops-day3 

cd devops-day3 

🧩 Step 3: Create System Monitoring Script 

Create script file: 

nano system_monitor.sh 

 
 
 
 
 
 
 
 
 
 
Paste this code: 

#!/bin/bash 

echo "==============================" 

echo " System Monitoring Report" 

echo " Date: $(date)" 

echo "==============================" 

echo "" 

echo "CPU Usage:" 

top -bn1 | grep "Cpu(s)" 

echo "" 

echo "Memory Usage:" 

free -h 

echo "" 

echo "Disk Usage:" 

df -h 

Save and exit: 

●  CTRL + X 

●  Y 

●  Enter 

 
 
 
 
 
 
 
 
🧩 Step 4: Give Execute Permission 

chmod +x system_monitor.sh 

🧩 Step 5: Test System Monitoring Script 

Run the script: 

./system_monitor.sh 

You should see: 

●  CPU usage 

●  Memory usage 

●  Disk usage 

●  Date & time 

✅ Monitoring script working successfully 

🧩 Step 6: Create Backup Script 

Now we will create a script to back up important files. 

Create backup script: 

nano backup.sh 

Paste this code: 

#!/bin/bash 

 
 
 
 
 
 
 
 
 
 
 
SOURCE_DIR="/home" 

BACKUP_DIR="/tmp/backup" 

DATE=$(date +%F) 

mkdir -p $BACKUP_DIR 

tar -czf $BACKUP_DIR/home_backup_$DATE.tar.gz $SOURCE_DIR 

echo "Backup completed on $DATE" 

🧩 Step 7: Give Execute Permission to Backup Script 

chmod +x backup.sh 

🧩 Step 8: Run Backup Script 

./backup.sh 

Check backup files: 

ls -lh /tmp/backup 

You should see: 

home_backup_YYYY-MM-DD.tar.gz 

 
 
 
 
 
 
 
 
 
 
✅ Backup created successfully 

🧩 Step 9: Combine Monitoring + Backup (Single Run) 

Now run both scripts together: 

./system_monitor.sh 

./backup.sh 

This simulates: 

●  Monitoring server health 

●  Taking backup after checking system status 

🧠 Beginner Explanation of Important Commands 

🔹 top -bn1 

Shows CPU usage in non-interactive mode 

🔹 free -h 

Shows memory usage in readable format 

🔹 df -h 

Shows disk usage in readable format 

🔹 tar -czf 

Creates compressed backup archive 

🔹 mkdir -p 

Creates directory if it doesn’t exist 

 
 
 
 
 
 
⚠ Common Errors & Fixes 

❌ Permission denied 
 ✔ Run chmod +x scriptname.sh 

❌ Backup file not created 
 ✔ Check SOURCE_DIR path 

❌ Script not running 
 ✔ Ensure you are inside correct directory 

🌟 Real-Life DevOps Use Case 

In production environments: 

●  Monitoring scripts run automatically 

●  Backups are scheduled 

●  Logs are stored for auditing 

●  Later replaced by tools like: 

○  Prometheus 

○  Grafana 

○  CloudWatch 

○  Backup automation tools 

👉 This task builds strong Linux + DevOps fundamentals. 

 
 
 
 
 
 
 
 
 
 
