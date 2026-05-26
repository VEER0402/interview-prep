\# Shell Scripting Basics



\## What is Shell Script?



A shell script is a file containing Linux commands executed automatically.



Used for:

\- Automation

\- Monitoring

\- Deployment

\- Backups



\---



\# Basic Script



```bash

\#!/bin/bash



echo "Hello DevOps"

```



Run:

```bash

chmod +x script.sh

./script.sh

```



\---



\# Variables



```bash

name="veerendra"



echo $name

```



\---



\# User Input



```bash

read username



echo "Welcome $username"

```



\---



\# If Condition



```bash

if \[ $a -gt 10 ]

then

&#x20; echo "Greater"

fi

```



\---



\# Loop Example



```bash

for i in 1 2 3

do

&#x20; echo $i

done

```



\---



\# Check Service Status Script



```bash

\#!/bin/bash



systemctl is-active nginx

```



\---



\# Disk Monitoring Script



```bash

\#!/bin/bash



df -h

```



\---



\# Real-world DevOps Use Cases



\- Health check automation

\- Backup scripts

\- Deployment automation

\- Log cleanup

\- Service monitoring



\---



\# Important Interview Question



\## What shell scripts have you written?



Example answer:



"I have written scripts for:

\- checking disk usage

\- monitoring services

\- automating deployments

\- cleaning old logs

\- validating server health"



\---



\# Common Mistakes



\## Mistake 1

Not giving execute permission.



Fix:

```bash

chmod +x script.sh

```



\---



\## Mistake 2

Wrong shebang.



Correct:

```bash

\#!/bin/bash

```

