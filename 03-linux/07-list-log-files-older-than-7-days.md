## Question  
How do you find and list the log files older than 7 days in the `/var/log` folder?

### 📝 Short Explanation  
This question tests your comfort with Linux file management and log housekeeping — a common task for DevOps and sysadmins.

## ✅ Answer  
You can use the `find` command with the `-mtime` option to locate files older than 7 days:

```bash
find /var/log -type f -name *.log
becuse we don't have exact file name else we use file name to search
```

### 📘 Detailed Explanation  

#### 🔍 Breakdown of the command:

- `find`: The Linux command to search for files in a directory hierarchy.
- `/var/log`: The target directory that contains log files.
- `-type f`: Limits the search to files (not directories).
- `-mtime +7`: Filters files **modified more than 7 days ago**.
  - `+7` means strictly older than 7 days.
  - `-7` would mean newer than 7 days.

---

#### 🛠️ Practical Usage:
If you want to **view the size and timestamp** of those files:
```bash
find /var/log -type f -name *.log -mtime +7
and exec it
 now to get all details of files like owner, and full info
find /var/log -type f -name *.log -mtime +7 -exec ls -ltr \;

```

If you want to **delete** those files:
```bash
sudo find /var/log -type f -mtime +7 -delete
```
⚠️ Be careful with deletion — make sure you’ve reviewed the list first.
Interview asked to mv files  
find /var/log -type f -name *.log -mtime +7 -exec mv {}
To zip all files 
find /var/log -type f -name *.log -mtime +7 -exec gzip {}

---

> Summary:  
> Use `find /var/log -type f -mtime +7` to list log files older than 7 days — a must-know for log maintenance in production servers.

---
