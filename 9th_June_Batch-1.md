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
