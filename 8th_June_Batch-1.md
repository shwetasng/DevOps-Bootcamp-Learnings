## QUESTIONS:-
- Where does AWS stores your public key in the machine?
- What is log4j?
- How we can use asymmetric encryption scheme to establish a connectio using SSH?
- How the server can verify that the code was written by the developer using the code or signature?
- Why does AWS made General Purpose SSD(gp3) (a newer generation EBS volume) cheaper than gp2 EBS volume? 


## Classroom Learnings:-
- To connect to your EC2 instance, don't use connect option from the AWS GUI, rather use SSH client to connect to it.
-  RDS protocol is used in windows to connect to EC2 instance.

## CODE SIGNING
  - Git allows to sign the code.
  - Code signing is done to prove that every code running in the production environment is digitally signed that allows to run exactly same code that is written by the developers on production server.
  - Digital signature is used to sign the code using private key. We encrypt using private key and decrypt using public key.
  - "openssl dgst -sha256 -sign private key -out signature.txt simple_flask_web server/app.py" command generates a signature in encrypted format.
  - "-sha" is a hashing algorithm and "signature.txt" conatins the output of the above executed command.
  - EC2 is the biggest service in AWS cloud.
  - IOPS = input output per second.
  - EXAMPLE : If IOPS=3000, we can read or write from disk 3000 times in a second.
  - Make sure your disk is provisioned in the same Availabilty Zone as your machine(VM).
  - In AWS, almost every resource can be tagged using key-value.
  - Very comman tags includes:-
    - project: project and its details.
    - env tag: the environment to which the resources belongs to. Generally, we have different accounts to use in different environment.
    - managed-by tag: who manages the resource.  
  - Terraform - Tool that helps to manage AWS resources as code. Example : In single click using terraform, resources can be provisioned.
  - Whie connecting to EC2 instance, if TIMEOUT ERROR occurs, probable reason is Firewall error. Inbound rules for port range=22(default port for SSH) & allowed port= 9999(to allow communication with server)
    - SOLUTION:- 
      - Go to security group -> Edit inbound rule -> Add rule -> Custom TCP to 8080(in port range) -> Set source to 0.0.0.0(anywhere IPv4).
