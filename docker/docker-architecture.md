\# Docker Architecture



\## Main Components



1\. Docker Client

2\. Docker Daemon

3\. Docker Registry

4\. Docker Images

5\. Docker Containers



\---



\## Docker Client



Commands:



```bash

docker build

docker run

docker pull

docker push

```



Client sends requests to Docker Daemon.



\---



\## Docker Daemon



Runs in background.



Responsibilities:

\- Build images

\- Run containers

\- Manage networks

\- Manage volumes



\---



\## Docker Registry



Stores images.



Examples:

\- Docker Hub

\- Amazon ECR

\- GitHub Container Registry



\---



\## Docker Image



Read-only template.



Contains:

\- Application code

\- Dependencies

\- Runtime



Example:



```bash

docker pull nginx

```



\---



\## Docker Container



Running instance of an image.



Example:



```bash

docker run nginx

```



\---



\## Workflow



Developer

→ Docker Build

→ Image Created

→ Push to Registry

→ Pull on Server

→ Run Container



\---

