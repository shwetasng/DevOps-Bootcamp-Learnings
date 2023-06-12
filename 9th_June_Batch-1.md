## PRACTICAL:-
- Launch EC2 instance in your own created VPC.
## About EC2
- In EC2 instance when you give a name, a tag is added by AWS with key:Name and Value:the name you gave.
- AWS has its own Linux created using CentOS.
- In the world of virtualization, we have concept of images. EXAMPLE:- Take all the windows os data, compress and zip it to obatin its image. We give this image to virtualization machine like Virtual Box, it will launch the OS.
- Anyone can create image AMI(Amazon Machine Image) upload it on AWS for people to use.
- AMI is different from Docker image. Docker Images are very light and AMI are heavy.
- Instance type basically tells about the generation of the hardware, number of CPUs and memory size being used. Read more about it on https://aws.amazon.com/ec2/instance-types/
- AWS has CPU optimized, RAM optimized and Network optimized instances.
- <ins>Note:</ins> If a 't' type instance is running but is idle i.e., CPU is not being used but you have paid for it, you earn some credits from AWS. And if in future you require more than 1 CPU, AWS uses these credits for providing those CPU..that is you don't have to pay for those extra CPU's.
- Every EC2 instance is a part of a network; Since AWS don't want to bother you with Networking issue, VPC is created by AWS automatically; basically there are default VPC in every region though this is unsecure since all subnets in this network are open to internet but very convenient. AWS hepls you to go global in minutes.
- Every region in AWS has a default VPC.
- For project we are supposed to do, we are required to create our own VPC.
- we don't want EC2 instance (consists sensitive data like customer information) to have public IP since it is very risky. Instances are made to have private IP. We can communicate with private EC2 using Kubernetes.
- if you ever see Timeout, it is most probably because of security group issue.
- <ins>User Data:</ins> in this we are supposed to write bash script; but recommended not to use; this is for beginner level. this script is not versioned like github, not reviewed hence not convenient.
- In EC2 instance under the Advanced Details tab, we have the following important options:-
  - Purchasing option : Request for spot instances.
  - Shutdown Behavior
  - Termination protection : Not able to terminate the instance(important instance) until we unable the instance first.
  - Placement group : Helps to place the instances inside the data server close to each other physically to reduce the latency.
  - User data -optional : can place bash script here. Once the instance is launched, script written here is also launched. Not a good way. This script is not versioned and reviewed by others unlike github.
  
## About S3 (SIMPLE STORAGE SERVICE)
- This is an object storage service. Different from block storage service (block storage exists in windows, linux etc where the data is stored in blocks).
- It is like google drive; just like google drive you will see directories in S3 but under the hood there is no such concept of Directories in this.
- Hadoop Filesystem - first object storage system. We don't have ideas of directories or files here, but idea of blob exists. 
- Here we have buckets to store objects and everything is stored in it with flat namespace.
- There is no meaning of file type here, everything is an object. Object has no meaning of itself, it's just a collection of bits.
- It's a regional service. When we store objects inside the bucket, we don't need to choose the bucket because every object you store in AWS region it is replicated atleast 3 times i.e., in 3 availability zones.
- Block storage is quicker than object storage (uses HTTP protocol to write in the bucket).
- Functions of Object storage:
  - objects are uploaded using http hence comparatively slower.
  - chances to loose data is low
  - There is no limit to store data.
  - Highly available service; every day service is not available only for 8 seconds.
- S3 is incredibly durable, highly available and we communicate with S3 using REST API, it is scalable and have high performance.
- when you store data in S3, you can't edit the data. to modify it: read-> edit-> modify-> overwrite.
- In S3 there is no search function; we can only list by help of prefix because we don't have concept of directories to search the data.
- ACL disabled means no other owner of object and it is advised to keep it disabled otherwise needed. 
- if 2 services of AWS wants to communicate with each other, it is done easily using role.
- Under the hood, data in S3 bucket is stored on regular disks. AWS provides us the interface in form of S3(abstraction).
- S3 is SaaS. We are provided with the software, we don't need to deal with code, network infrastrcture or whwre the data is going or stored.
- we can install AWS CLI inside the instance using ' sudo apt install awscli '
- bucket name is unique across AWS.
- to read a file in S3, you will have to download it and read it like a regular file.
- <ins>Imp:</ins> What if by mistake some developer overwrite an object in S3 since in S3 objects with same name are overwritten? To solve this we enable bucket versioning, so instead of overwriting we can see different versions of the objects.
- Storage Classes:
  - S3 Standard IA is a storage which is infrequently accessed so for this you pay less to store data but pay more to access data.

## SS from today's session:
![image](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/422b1def-8c9d-4a69-b4ee-126282263fdc)
![image](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/6724db6a-c8c1-4de4-9570-f7dae788ed0c)
![image](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/386d59d4-f561-43e9-b7f3-518e6e1bc3a1)
![image](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/18dd9570-5bf9-4b98-9af8-ab1ad54ec07e)
![image](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/c7f10ed2-e0d3-418e-813f-6e39c21b7798)
![image](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/01cf9374-715e-43c8-917f-96e35518bbcc)
![image](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/7945d488-b2ab-4109-a154-c26fa9e82a6b)
![image](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/d102e852-e124-414e-bb8e-2cf070036591)
![image](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/e27793e3-6c2c-45a8-bc13-94535b0a38fd)
![image](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/fd8c3f17-7f8f-4ca0-81c5-ba5129ef76fe)
![image](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/7fe790d3-6f64-4875-a302-5dc70246b602)
![image](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/e27e6f00-2e1d-44e0-a9a1-3dd81cb5456e)
![image](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/32b6175b-f520-4ff6-b4c3-301506832a62)
![image](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/5ac39552-3a46-45b9-8a65-c49ea165fbe8)
![image](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/c1b34789-de5c-4712-abf9-88e48d480e27)
![image](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/e6186bb8-24f9-4c2b-98a1-a4d7fafab626)
![image](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/b71e1211-b3e0-4199-a9bd-414e61eda05d)
![image](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/2192aa09-b1d6-460f-8ce6-bf26fb1e87ee)
<img width="530" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/7c29458b-0614-40d0-9456-0a321d199b6e">
<img width="530" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/aa3a64c2-888d-417e-81e3-79fd8b5c121d">
<img width="528" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/52e99efc-7c12-4780-b184-ab138b2e0537">
<img width="533" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/c23dd958-5835-4382-bbb9-dd688fe56b6a">
<img width="524" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/5ff549c0-0952-4049-9de5-f11f95e85795">
<img width="523" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/aedc1845-24dd-465d-ab1b-f98d7e43a6ed">
<img width="526" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/95d8240d-ee00-4b8c-9822-f63bac2f9396">
<img width="527" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/5fe2934a-b6fd-42d8-bcf1-72a9f324c5f9">
<img width="527" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/718aaa61-f34a-4f6f-86b9-3657f913317c">
<img width="529" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/8941129e-f420-49f3-b8a4-77daf081c6a4">
<img width="529" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/123a6ab4-f775-4251-837e-08122f6f5453">
<img width="527" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/fb2b1abd-46b0-4ac0-a00f-e0bd4b514d05">
<img width="527" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/48f70315-b682-4086-ac2b-290e51e10831">
<img width="530" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/43cf552d-0aee-4971-931f-cc1836f97891">
<img width="529" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/20d2129c-fc85-4fe9-adb3-7910cec688b6">
<img width="523" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/eda8f8f1-3c6b-4501-98d9-820422cd4da7">
<img width="529" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/92ac64e4-a5cf-4d75-977f-9f4da2984398">




