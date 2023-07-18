## Using dig command to resolve ip address of stanford.edu

1. First we get list of root level servers using below command.
<img width="368" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/38db594c-d693-4407-92fa-247bf86b515f">

2. Then we choose one of those servers to give list of all server responsible for .edu
<img width="400" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/222fc77b-244b-436d-b8fb-8fbbdeb7e3d5">
<img width="357" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/221a3b59-9cb5-45bd-a67d-c77522513233">

3. Then we ask one of these servers to get authoritative servers of stanford.edu
<img width="373" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/18966e39-f7d9-4d37-810c-9492b441724b">

4. From these authoritative servers we then ask for ip-address of stanford.edu
<img width="362" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/efbdf00b-4447-48a1-806a-8be9cb644590">

### NOTE
if we resolve a hostname once and then resolve it again within some time it will be retireved in 0ms since it is stored in cache for some time.
<img width="351" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/e44a0ac6-5030-425e-80f7-cb0a716127a3">




 

