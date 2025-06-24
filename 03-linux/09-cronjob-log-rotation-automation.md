## Question  
Your application generates large logs in `/var/log/myapp/` and there's no log rotation setup.

**Task:**  
Write a shell script that compresses logs older than 7 days and deletes logs older than 30 days. Also, run it daily via cron.

### 📝 Short Explanation  
This question tests your ability to manage disk space with log compression and retention — a common task in DevOps. You're expected to automate it safely and consistently using a cron job.

## ✅ Answer  

1. first verify if this directory even exist on system.
2. After verifivation done , find logs to compress it older than 7 days.
3. Now when you compress the logs that are older than 7 days then you need to do consideration to not take logs that are older than 30 days. Because it is easy to take logs lder than 7 days but it also can taek logs older than 14 days too or 15 days too.
 You have to add checkpoint in the script that if this script find logs file older than 30 days.
 it will not create zip or gzip file instead it will ignore it because in the next step as per the ques
we will use find command to find the logs older than 30 days and we will simply remove the logs .

### 🖥️ Shell Script: `log_cleanup.sh`

```bash
#!/bin/bash

# Directory where logs are stored
LOG_DIR="/var/log/myapp"
LOG_FILE="/var/log/myapp/log_rotation.log"

# Ensure the log directory exists
if [ ! -d "$LOG_DIR" ]; then
    echo "[$(date)] ERROR: Log directory $LOG_DIR does not exist!" >> "$LOG_FILE"
    exit 1
fi

# Compress logs older than 7 days (but newer than 30)
find "$LOG_DIR" -type f -name "*.log" -mtime +7 -mtime -30 ! -name "*.gz" -exec gzip {} \; -exec echo "[$(date)] Compressed: {}" >> "$LOG_FILE" \;

# Delete compressed logs older than 30 days
find "$LOG_DIR" -type f -name "*.gz" -mtime +30 -exec rm -f {} \; -exec echo "[$(date)] Deleted: {}" >> "$LOG_FILE" \;

# Optional: Delete uncompressed logs older than 30 days
find "$LOG_DIR" -type f -name "*.log" -mtime +30 -exec rm -f {} \; -exec echo "[$(date)] Deleted (uncompressed): {}" >> "$LOG_FILE" \;

# Done
echo "[$(date)] Log rotation completed successfully." >> "$LOG_FILE"

```
