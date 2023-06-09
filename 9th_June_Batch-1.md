## About EC2
- In EC2 instance when you give a name, a tag is added by AWS with key:Name and Value:the name you gave.
- AWS has its own Linux created using CentOS
- Anyone can create image AMI(Amazon Machine Image) upload it on AWS for people to use.
- AMI is different from Docker image. Docker Images are very light and AMI are heavy.
- Instance type basically tells about the generation of the hardware being used. Read more about it on https://aws.amazon.com/ec2/instance-types/
- Note: If a t type instance is running but is idle i.e., CPU is not being used, you earn some credits from AWS. And if in future you require more than 1 CPU, AWS uses these credits for providing those CPU..that is you don't have to pay for those extra CPU's.
- Every EC2 instance is a part of a network; Since AWS don't want to bother you with Networking issue, VPC is created by AWS automatically; basically there are default VPC in every region though this is unsecure since open to internet but very convenient.
- For project we are supposed to do, we are required to create our own VPC.
- we don't want EC2 instance to have public IP since it is very risky.
- if you ever see Timeout, it is most probably because of security group issue.
- <ins>User Data:</ins> in this we are supposed to write bash script; but recommended not to use; this is for beginner level. this script is not versioned like github, not reviewed hence not convenient.

## About S3

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


