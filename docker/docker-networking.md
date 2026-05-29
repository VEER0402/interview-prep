\# Docker Networking



\## Why Networking?



Containers need communication.



Examples:

\- Frontend → Backend

\- Backend → Database



\---



\## Network Types



\### Bridge



Default network.



```bash

docker network ls

```



Used for:

\- Containers on same host



\---



\### Host



Container uses host network directly.



Benefits:

\- Better performance



Drawback:

\- Less isolation



\---



\### None



No networking.



Used for:

\- Highly isolated containers



\---



\### Overlay



Used in Docker Swarm.



Supports communication across multiple hosts.



\---



\## Create Network



```bash

docker network create my-network

```



\---



\## Run Container in Network



```bash

docker run -d --network my-network nginx

```



\---



\## Inspect Network



```bash

docker network inspect my-network

```



\---

