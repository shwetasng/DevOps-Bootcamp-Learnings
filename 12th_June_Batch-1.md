## DOCKER
- Docker has 4 objects :- 
  1. Docker containers
  2. Docker Images
  3. Docker network
  4. Docker volume

### Virtualization 
- With BARE METAL SYSTEMS where every application runs on a single machine, it requires neccessary dependencies, libraries etc to run successfully. If any of the insatlled library breaks, entire system collapse and we need to install the OS Server again.
- Hypervisor is a layer that seperates the VMs from physical host machine and from one another.
- VMs are seperated from one another.
- VMs access memory from data center of AWS.
- VM advantages :- Isolation, Hardware Abstraction, OS fexibility etc.
- Image in AWS is AMI.
- Collection of virtaul machine is called cluster. In each node, we have 1 or more VM(s). If one of the Virtual Machine fails, an automated process creates a new VM on the same host machine or different host machine called FAULT TOLERANCE.
- If the failure of VM  is expected we can go with graceful termination or if the failure is unexpected we can't do anything. Failure is rare.
- Proxy components can hold the user requests. If VM fails, proxy components redirects the user requets the fails machine was dealing with to the new VM.
- Kafka, Rabbitmq, sqs = Queques Technolgy. Architecture that serves the user request atleast once.

## CONTAINERS
- Containers under the hood are just linux processes.
- Example : Running a simple Flask Webserver doesn't require an entire OS. It's a lightweight process, thus we run it as an isolated process as a container.
- Containers are isolated linux processes. Containers think that they are the only running process on the host machine but actaully they are just a part of multiple processes runnning on the machine.
- By default, containers cannot change anything on the host machine. They are just guest processes.
- ANALOGY :
  - Docker Image = Class
  - Docker Container = Instance
- OCI = Open Container Interface.
- Docker Client and Docker Server/Deamon usually resides on the same machine but this is not neccessary.
- Deamon executes the command received from Docker client.
- We connect to conatiner if it was a VM but there is no concept of VMs and SSH in Container.
- Docker Hu is like github. It's a hub for docker images. 
- "docker run -it ubuntu /bin/bash" command to connect with container that has "ubuntu" image.
- Here :- 
  - '-i' flag : interactive (we can provide some input to container and get some output).
  - '-t' flag : terminal (TTY terminal - fakes like linux terminal inside the container)
  -  'ubuntu' : it's an image
- Every process in linux starts with a command.
- We have default ubuntu image command.
- We use Ubuntu image as a base image to create other images.
- Container has its own filesystem (it doesn't share the filesystem of the host machine). Thus, we need to fake a terminal for container to interact with its filesystem (get the feeling of connecting to a VM and using its CLI).
 
