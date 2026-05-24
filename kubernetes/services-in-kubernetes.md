\# Kubernetes Services



\## What is a Service in Kubernetes?



A Service provides a stable network endpoint to access Pods.



Pods are temporary:

\- Pods can die

\- IP addresses change

\- New pods get new IPs



Service solves this problem by giving:

\- Stable IP

\- Stable DNS name

\- Load balancing



\---



\## Why Services are needed



Without Service:

\- Direct pod communication breaks after pod restart



With Service:

\- Traffic automatically routes to healthy pods



\---



\## Types of Kubernetes Services



1\. ClusterIP

2\. NodePort

3\. LoadBalancer

4\. ExternalName



\---



\# 1. ClusterIP



Default service type.



Used for:

\- Internal communication inside cluster



Example:

\- Backend API accessed by frontend pod



Characteristics:

\- Accessible only within cluster

\- Not exposed to internet



Example YAML:



```yaml

apiVersion: v1

kind: Service

metadata:

&#x20; name: backend-service

spec:

&#x20; selector:

&#x20;   app: backend

&#x20; ports:

&#x20;   - port: 80

&#x20;     targetPort: 8080

```



Flow:

Frontend Pod → Service → Backend Pods



\---



\# 2. NodePort



Exposes application on a port of worker node.



Used for:

\- Testing

\- Small environments

\- Direct external access



Example:

```yaml

apiVersion: v1

kind: Service

metadata:

&#x20; name: nginx-nodeport

spec:

&#x20; type: NodePort

&#x20; selector:

&#x20;   app: nginx

&#x20; ports:

&#x20;   - port: 80

&#x20;     targetPort: 80

&#x20;     nodePort: 30007

```



Access:

``` id="kqbl1r"

http://<NodeIP>:30007

```



Problems:

\- Not production friendly

\- Manual port management

\- Security exposure



\---



\# 3. LoadBalancer



Used in cloud environments like:

\- AWS

\- Azure

\- GCP



Creates external load balancer automatically.



Example:

```yaml

apiVersion: v1

kind: Service

metadata:

&#x20; name: app-loadbalancer

spec:

&#x20; type: LoadBalancer

&#x20; selector:

&#x20;   app: myapp

&#x20; ports:

&#x20;   - port: 80

&#x20;     targetPort: 8080

```



Benefits:

\- Public access

\- Cloud-managed load balancing

\- Better for production



\---



\# 4. ExternalName



Maps Kubernetes service to external DNS.



Example:

```yaml

apiVersion: v1

kind: Service

metadata:

&#x20; name: external-db

spec:

&#x20; type: ExternalName

&#x20; externalName: mydb.example.com

```



Use case:

\- Connect external database/service



\---



\# Service Discovery



Kubernetes automatically creates DNS entries.



Example:

``` id="wjm79m"

backend-service.default.svc.cluster.local

```



Pods can communicate using service names.



\---



\# Important Interview Points



\## Difference between Pod and Service



Pod:

\- Temporary

\- Dynamic IP



Service:

\- Stable endpoint

\- Load balancing



\---



\## NodePort vs LoadBalancer



NodePort:

\- Opens port on node

\- Manual access



LoadBalancer:

\- Cloud-managed

\- Production ready



\---



\## What happens if Pod dies?



Service automatically routes traffic to healthy pods.



No change needed from client side.



\---



\# Real-world Example



Frontend application:

\- Calls backend-service



Backend pods may restart anytime.



Service ensures:

\- Stable communication

\- Load balancing

\- High availability



\---



\# Useful Commands



Create service:

```bash

kubectl expose deployment nginx --port=80 --type=NodePort

```



Get services:

```bash id="h2k1lh"

kubectl get svc

```



Describe service:

```bash id="n4m5fx"

kubectl describe svc nginx

```



\---



\# Common Beginner Mistake



Thinking Service and Pod are same.



Service is only a networking abstraction.

It does NOT run application containers.

