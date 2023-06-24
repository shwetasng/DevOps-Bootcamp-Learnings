## KUBERNETES
### Questions:-
- How does we want master to communicate with the worker(s)?
- How we can protect the k8scluster on the cloud? 

### Learnings from the classroom:-
- 3 types of CI-CD Pipeline:-
  - Build Pipeline
  - Deploy Pipeline
  - Pull request Pipeline
- Consider having large number of EC2 instances with us. We need a way to manage this architecture. If any of the instance fails, we need to heal it and thus need to monitor the architecture. Hence, we need someone to heal the broken instances, monitor the architecture, inform about which conatiners are available and which are not. **KUBERNETES** is the one perfect to do all these tasks.
- In Kubernetes (often abbreviated as K8s), a node is a worker machine that runs containerized applications. It is a physical or virtual machine(EC2 Instances) that forms part of the underlying infrastructure in a Kubernetes cluster. Nodes are responsible for running and managing the pods, which are the smallest deployable units in Kubernetes.
- K8s is a container orchestration system.
- K8s in greek means 'helmsman' or 'pilot' responsible for shipping and managing the containers.
- Instead or working and managing the instances on cloud, we can talk with k8s in much more efficient way to manage the instances. We don't even need to connect to the instance using the SSh.
- K8s is called the 'Kernel of the Cloud' because like the kernel of the system prevents the user to directly interact with the CPU or disk os the system, likewise k8s allows users to maintain and manage the container(s) with manual intervention.
- **'Minikube'** is the common, lightweight dustribution of k8s. It's sufficient to practice k8s locally. Eliminates the need to work with costly k8s cluster.
- K8s can scale up the application by launching the EC2 instances and can terminate the instances when there is scale down.
- **'AWS EKS'** is Amazon Elastic Kubernetes Service offered by the AWS. It simplifies the process of deploying, managing, and scaling containerized applications using Kubernetes on AWS infrastructure.
- K0s is very light distribution of kubernetes.
- **k8s cluster** is the set of nodes (generally the node is composed of EC2 Instances).
- Before the introduction of k8s, we need to create instance and deploy containers to instances manually.
- We have a command line tool called **'kubectl'** to communicate with the k8s cluster.
- AWS has a tool called **'eksctl'** similar to kubectl, that allows to create cluster using a single line command.
- Kubernetes also have versions as linux have.
- Be careful to update your k8s version. Don't be enthusiatic to move to newly released version. Let the latest version run for a year and then switch to it because by that time the that version would have been used by other users, vulnerabilities and bugs identified and fixed. Hence, version would become stable. Developers use version one higher than the deprecated version.
- AWS EKS does all the stuff for us but we need to provide it the permissions to access the other services of AWS while doing its job. Create a role and put this role in EKS that enables permissions to access the other services of the AWS.
- It's a good practice to place the EC2 instance in the private cluster of the subnet.
- k8s and Jenkins follows **master-worker** architecture.
- EKS is the k8s master and workers are the EC2 instances(or nodes).
- AWS offers 3 diiferent ways tp access the cluster:-
  1. **Public access**: User wants public cluster end-point for the masterso as to communicate directly with the master in the cluster. It's the ability to commmunicate with the master from your local and ability of master to communicate with the worker(s) over the internet. It's not a good idea to have public access to the cluster as the cluster may contain user data which can then be modified easily through public access.
  2. **Private access**: Communication to master from local machine is public while the communication from master to nodes is private.
  3. **Public & Private**: AWS allows us to have workers other than EC2 instance outside the cloud(e.g. on premises server). Master communicates with this worker outside of its VPC over the Internet using public-private access.
- We generally put master in the private subnet so that nobody have a public access to the end-point of the cluster. The only way to communiv=cate with such type of cluster is through 'BASTION SERVER'.
- How does we want master to communicate with the worker(s)?
  - ANSWER : We want master to communicate privately with the worker within the VPC.
- **NOTE**: In our shared cluster for the Bootcamp, we'll use the public access architecture.
- 
- 
