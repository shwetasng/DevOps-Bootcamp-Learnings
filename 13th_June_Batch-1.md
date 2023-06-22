## Questions-
- How two or more containers communicate with each other?
- Is there any way to recover the terminated instance?
- How do we get the private IP address of the container?
- Who is the user inside the container?
  
## DOCKER CONTAINERS & IMAGES
- Virtual Machine is the virtualization of the operating system.
- Container is the virtualization of an application.
- Under the hood, conatiner is a process.
- Container is created from image.
- An image is a lightweight, standalone, and executable software package that includes everything needed to run a piece of software, including the code, runtime, system tools, libraries, and dependencies. It serves as a template or blueprint for creating Docker containers.
- An image is built from a set of instructions called a Dockerfile, which defines the steps needed to create the image.
- Docker images form the basis of Docker containers. Containers are instantiated from images and run in isolation, providing a consistent and reproducible environment for applications. Images can be pulled from a registry, built locally, or even created using existing images as a starting point.
- ***"docker ps"*** command is used to list the running containers. Running Processes in linux can be listed using "ps" command and sice under the hood conatiners are also processes, thus, we used the same command as used for linux processes.
- ***"docker ps -a"*** command to list all the containers.
- We can rerun the container that has been stopped or exited but in real production env. we never deal with such conatiners rather creates a new container.
- ***"docker run name_of_container"*** command is used to create and run the new container.
- nginx image from DockerHub registry. Nginx is a very common web-server. We can directly install it on our local machine or launch it as a container using its image. Pull the nginx image from the DockerHub registry and then use it. There exists various versions of the nginx server. To launch the container use "docker run nginx" command.
- To visit the application(i.e. nginx server), open the browser and type "localhost:80". But this results in error because container is a seperate process, seperated from rest of the processes. Solution to this problem is to agian run the container using the ***"docker run -p 3455:80 nginx"*** command. Here -p publishes the port in the docker container i.e used for port mapping. "-p 3455:80" specifies port mapping, where the container's port is mapped to the host's port. In this case, it maps port 80 inside the container to port 3455 on the host. So, when accessing port 3455 on the host, the traffic will be directed to port 80 within the NGINX container.
- Now type localhost:3455 in web-browser to communicate with the web-server.
- We can use "docker ps" command to list the running conatiners on any machine(including the EC2 instance(s)).
- ***"docker rm name_of_the_conatiner"*** command is used to remove the container.
- Name of the container must be unique.
- To check that whether the nginx server container is running or not we can use the following ways-
  - run "docker ps" command
  - type "localhost:3455" on web browser
  - or run "curl localhost:3455" command on terminal.
- **Example** : Let's consider the 2 nginx containers.
  - "docker run --name nginx1 -p 8080:80 nginx" command to run the first container.
  - "docker run --name nginx2 -p 8081:80 nginx" command to run the second container.
  - We want to communicate from nginx2 to nginx1.
  - Open the terminal and to connect the nginx2 server container use ***"docker exec -it nginx /bin/bash"*** command to connect to the running conatiner and gets its terminal access.
  - use ***"docker inspect name_of_the_container"*** command to find the information of both the container. This command will also display the IP addresses of both the containers.
  - ping nginx1 server from nginx2 server to test the reachability of nginx2 server for communication. Command to be used is ***"ping nginx1 IP_Address"***.
- Each running container has a virtual private IP address.
- Use ***"docker inspect nginx2"*** command to display the information about the nginx2 web-server.
- Use ***"docker inspect nginx1"*** command to display the information about the nginx1 web-server.
- Root is the user inside the conatiner.
- ***"apt -get install iputils -ping"*** command is used to instal ping inside the container.
- Username is the container ID(for container's terminal).

### Docker Networking
- Container Network Model (CNM).
- Inside the container, we have a sandbox that contains the virtualized services or features in it.
- If the 2 containers are connected to the same network, they can communicate with each other.
- Sandbox is a virtualized stack (contains virtualozed route tables, virtualized network interface etc.).
- Inside sandbix, we have network interface that hepls to go out to network bridge.
- _**BRIDGE :**_ allows conatiners in the same network to communicate with each other on the same host machine.
- A bridge network creates a virtual bridge or switch, which acts as a layer 2 (data link layer) networking device to facilitate communication between containers.
- **OVERLAY DRIVERS :** these are network drivers used to create overlay networks in container runtimes such as Docker. Overlay networks enable communication between containers running on different hosts or nodes within a cluster using private IP address, providing connectivity and network isolation across multiple machines.
- **NONE NETWORK PLUGIN :** - 'none' network plugin or driver is used to create a network namespace for a container without attaching it to any specific network. It essentially means that the container is not connected to any network and does not have network access. When you use the "none" network plugin, the container will not have an IP address assigned and will not be able to communicate with other containers or external networks. This can be useful in certain scenarios where network connectivity is not required or when you want to isolate a container completely from any network.


## Screenshots from today's class:-

![13-6-23a](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/127d1e2a-8764-4d60-ab3b-14a8e0ccbca7)

![13-6-23b](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/921cb827-3e1f-48c4-8d86-dd56d8ee0681)

![13-6-23c](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/eb8c6639-8b80-4403-a1e8-bfc6274f099f)

![13-6-23d](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/168f58b3-a019-4c61-8b15-936134284def)

![13-6-23e](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/00dbd10c-7de6-4bc7-8dfb-0e3b575e77b4)
![13-6-23f](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/04ffee63-52f8-40af-a801-81dddb653451)


![13-6-23g](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/2e313c4d-346b-4c4e-a9cb-b14a0b9df80f)
![13-6-23h](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/6d716043-b5c0-40dc-a309-923a84c86ea2)


![13-6-23i](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/56a50711-dca8-40c5-94a5-85cd43fed4d6)
![13-6-23j](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/0a24dec5-e86b-44f8-aa14-c3e1f924cb13)


![13-6-23k](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/1d45e944-0031-4e37-b3a3-755e1dd2eb8e)
![13-6-23l](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/037c6dc3-43de-4a5b-be46-f467f15ef1d1)

![13-6-23m](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/4c64b683-a6c5-40e7-8e45-dd3f95d37c52)


