\# Linux Troubleshooting Basics



\## 1. Check System Load



```bash

uptime

```



Shows:

\- Current time

\- System uptime

\- Load average



Example:

``` id="g4j8ke"

load average: 1.20, 0.80, 0.60

```



High load may indicate:

\- CPU bottleneck

\- Too many processes

\- Heavy applications



\---



\## 2. Check Memory Usage



```bash

free -h

```



Shows:

\- Total RAM

\- Used memory

\- Free memory

\- Swap usage



\---



\## 3. Check Disk Usage



```bash

df -h

```



Used for:

\- Checking disk full issues



If disk becomes 100%:

\- Applications may crash

\- Logs stop writing

\- Pods/services fail



\---



\## 4. Find Large Files



```bash

du -sh \\\*

```



Helpful for:

\- Cleaning storage

\- Finding log growth



\---



\## 5. Check Running Processes



```bash

top

```



or



```bash

htop

```



Used for:

\- CPU monitoring

\- Memory monitoring

\- Killing problematic process



\---



\## 6. Check Specific Process



```bash

ps aux | grep nginx

```



Used for:

\- Finding process

\- Debugging services



\---



\## 7. Kill Process



```bash

kill -9 PID

```



SIGKILL forcefully terminates process.



\---



\## 8. Check Open Ports



```bash

netstat -tulnp

```



or



```bash

ss -tulnp

```



Used for:

\- Debugging port conflicts

\- Checking listening services



\---



\## 9. Check Logs



```bash

tail -f /var/log/syslog

```



or



```bash

journalctl -u nginx -f

```



Important for:

\- Service debugging

\- Crash investigation



\---



\## 10. Check Service Status



```bash

systemctl status nginx

```



Used for:

\- Service health

\- Startup failure debugging



\---



\# Real-world Troubleshooting Flow



1\. Check service status

2\. Check logs

3\. Check CPU/memory

4\. Check ports

5\. Check disk space

6\. Restart service if needed



\---



\# Common Interview Question



\## What happens if disk becomes 100%?



Possible issues:

\- Logs stop writing

\- Applications crash

\- Database corruption risk

\- Kubernetes pods may fail



Immediate actions:

\- Find large files

\- Clear logs

\- Increase storage



