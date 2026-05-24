\# Kubernetes Architecture



\## What is Kubernetes Architecture?



Kubernetes architecture defines how different Kubernetes components work together to manage containerized applications.



A Kubernetes cluster mainly contains:

1\. Control Plane

2\. Worker Nodes



\---



\# High-Level Architecture



``` id="1w8wna"

&#x20;               +----------------------+

&#x20;               |    Control Plane     |

&#x20;               +----------------------+

&#x20;                  /      |       \\

&#x20;                 /       |        \\

&#x20;        Scheduler   API Server   Controller Manager

&#x20;                             \\

&#x20;                              etcd



&#x20;       --------------------------------------------



&#x20;             Worker Node 1        Worker Node 2

&#x20;            +--------------+     +--------------+

&#x20;            | kubelet      |     | kubelet      |

&#x20;            | kube-proxy   |     | kube-proxy   |

&#x20;            | Container RT |     | Container RT |

&#x20;            | Pods         |     | Pods         |

&#x20;            +--------------+     +--------------+

```



\---



\# 1. Control Plane



Control Plane is the brain of Kubernetes.



It manages:

\- Cluster state

\- Scheduling

\- Monitoring

\- API handling

\- Desired state management



Main components:

1\. API Server

2\. Scheduler

3\. Controller Manager

4\. etcd



\---



\# API Server



The API Server is the entry point of Kubernetes.



All communication happens through it.



Examples:

\- kubectl commands

\- CI/CD tools

\- Internal cluster communication



Example:

```bash

kubectl get pods

```



This command talks to API Server.



Responsibilities:

\- Accept requests

\- Validate requests

\- Update cluster state

\- Communicate with etcd



\---



\# Scheduler



Scheduler decides:

"Which node should run the pod?"



It checks:

\- CPU availability

\- Memory availability

\- Node conditions

\- Affinity rules

\- Taints/Tolerations



Example:

If Node1 has enough CPU and memory,

scheduler may place pod there.



\---



\# Controller Manager



Controller Manager continuously checks:

"Desired state vs Actual state"



Example:

Desired replicas = 3



If one pod dies:

\- Controller detects issue

\- Creates new pod automatically



Controllers include:

\- Deployment Controller

\- Node Controller

\- ReplicaSet Controller



\---



\# etcd



etcd is Kubernetes database.



Stores:

\- Cluster configuration

\- Secrets

\- Pod information

\- Service data

\- Current cluster state



Important:

\- Distributed key-value store

\- Very critical component

\- Backup is important



If etcd is lost:

Cluster state can be lost.



\---



\# 2. Worker Node



Worker nodes run actual applications.



Each worker node contains:

1\. kubelet

2\. kube-proxy

3\. Container Runtime

4\. Pods



\---



\# kubelet



kubelet is node agent.



Responsibilities:

\- Talks with API Server

\- Ensures pods are running

\- Monitors containers

\- Reports node status



If pod crashes:

kubelet helps restart it.



\---



\# kube-proxy



Handles networking inside cluster.



Responsibilities:

\- Service networking

\- Traffic forwarding

\- Load balancing



Example:

Service traffic routed to healthy pods.



\---



\# Container Runtime



Responsible for running containers.



Examples:

\- containerd

\- CRI-O

\- Docker (older setups)



Tasks:

\- Pull images

\- Start containers

\- Stop containers



\---



\# Pods



Smallest deployable unit in Kubernetes.



A pod can contain:

\- One container

\- Multiple tightly coupled containers



Example:

```yaml

Pod

&#x20;└── nginx container

```



\---



\# Kubernetes Workflow Example



\## Step-by-step flow



1\. User runs:

```bash

kubectl apply -f app.yaml

```



2\. Request goes to API Server



3\. API Server stores data in etcd



4\. Scheduler selects worker node



5\. kubelet receives instruction



6\. Container runtime pulls image



7\. Pod starts running



8\. kube-proxy manages networking



\---



\# Important Interview Questions



\## What is Control Plane?



Brain of Kubernetes cluster that manages overall orchestration.



\---



\## What happens if Worker Node dies?



Pods on that node become unavailable.



Scheduler creates replacement pods on healthy nodes.



\---



\## What happens if API Server goes down?



kubectl commands and cluster management stop working.



Running applications may continue temporarily.



\---



\## Why is etcd important?



Stores complete cluster state.



Without etcd, Kubernetes loses cluster information.



\---



\# Real-World Production Thinking



Production clusters usually have:

\- Multiple control plane nodes

\- Multiple worker nodes

\- etcd backups

\- Monitoring

\- Auto scaling

\- High availability



\---



\# Common Beginner Mistakes



\## Mistake 1

Thinking Kubernetes directly runs containers.



Reality:

Container Runtime runs containers.



\---



\## Mistake 2

Thinking Scheduler runs pods.



Reality:

Scheduler only selects node.

kubelet actually starts pod.



\---



\## Mistake 3

Ignoring etcd backup.



In production:

etcd backup is critical.

