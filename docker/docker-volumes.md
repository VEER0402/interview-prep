\# Docker Volumes



\## Problem



Containers are temporary.



If container is deleted:

\- Data can be lost



Volumes solve this problem.



\---



\## What is a Volume?



Persistent storage managed by Docker.



\---



\## Create Volume



```bash

docker volume create my-volume

```



\---



\## View Volumes



```bash

docker volume ls

```



\---



\## Mount Volume



```bash

docker run -d \\

\-v my-volume:/data \\

nginx

```



\---



\## Bind Mount



Example:



```bash

docker run -d \\

\-v /host/logs:/app/logs \\

nginx

```



\---



\## Volume vs Bind Mount



Volume:

\- Managed by Docker

\- Portable



Bind Mount:

\- Uses host path

\- Less portable



\---



\## Real World Use Cases



Databases:

\- MySQL

\- PostgreSQL

\- MongoDB



Log storage



Application uploads



\---



