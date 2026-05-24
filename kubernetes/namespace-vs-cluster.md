Namespace vs Cluster



Cluster

A Kubernetes cluster is the complete environment containing:

\- Control plane

\- Worker nodes

\- Pods

\- Services

\- Networking



A single cluster can contain multiple namespaces.



\---



&#x20;Namespace

Namespace is a logical isolation inside a cluster.



Used for:

\- Environment separation

\- Team separation

\- Resource organization



Examples:

\- dev

\- staging

\- production



\---



&#x20;Why namespaces matter

\- Avoid naming conflicts

\- Resource quotas

\- RBAC control

\- Better organization



\---



&#x20;Real-world example



Company has one cluster:



\- frontend team → frontend namespace

\- backend team → backend namespace

\- monitoring tools → monitoring namespace



\---



&#x20;Commands



Create namespace:

```bash

kubectl create namespace production

