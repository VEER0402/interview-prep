\# Linux Important Concepts



\# Process vs Thread



Process:

\- Independent program execution

\- Separate memory space



Thread:

\- Lightweight unit inside process

\- Shared memory



Example:

Chrome browser:

\- One process

\- Multiple threads



\---



\# Zombie Process



Zombie process:

\- Process finished execution

\- Entry still exists in process table



Caused when:

\- Parent does not read child exit status



Check:

```bash

ps aux | grep Z

```



\---



\# Swap Memory



Swap:

\- Disk space used as extra RAM



Problem:

\- Much slower than RAM



High swap usage may indicate:

\- Memory pressure



\---



\# Inode



Inode stores:

\- File metadata

\- Permissions

\- Ownership



Not file name.



Important:

Disk may show free space,

but inode exhaustion can still stop file creation.



Check:

```bash

df -i

```



\---



\# File Permissions



Example:

```bash

\-rwxr-xr--

```



Meaning:

\- Owner

\- Group

\- Others



Permission values:

\- r = 4

\- w = 2

\- x = 1



\---



\# Why 777 is Dangerous



```bash

chmod 777 file

```



Gives:

\- Read

\- Write

\- Execute

to everyone.



Security risk:

\- Any user can modify file.



\---



\# Soft Link vs Hard Link



Soft Link:

\- Points to file path

\- Breaks if original deleted



Hard Link:

\- Points to inode

\- Works even if original deleted



\---



\# Load Average



Shows system workload.



Example:

```bash

uptime

```



Interpretation:

High load may indicate:

\- CPU bottleneck

\- Waiting processes

\- Heavy applications

