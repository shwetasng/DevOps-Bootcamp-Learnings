## KUBERNETES
### Questions:-
- How does we want master to communicate with the worker(s)?
- How we can protect the k8scluster on the cloud?
- How can we communicate with the cluster from our local machine?
- What is the difference between the pods containing the single container and the container itself?

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
- We can protect the cluster inside the cloud by restricting the communication b/w the master and the worker(s). Allow communication only through BASTION SERVER.
- **CLOUDWATCH** is the observability service of cloud. It's the monitoring tool for AWS. All the application logs and metrices are stored here.
- Amazon EKS add-ons inter-relates to the internal architecture of K8s. Some of theese are mandatory(default) to operate in the cluster. Remember that version of the add-ons must be corresponding to the version of the kubernetes.
- kubectl can be used to communicate & control the cluster.
- **POD** is the set of 1 or more container. It's the smallest deployable unit in the cluster. 
- **OpenLens** is an open sorce tool that helps in visualisation of the cluster.It helps to know what happening inside the cluster. If our kubectl works good, openlens also works good.
- **"kubectl get pods"** command is used to list the pods running inthe cluster.
- **"kubectl get nodes"** command is used to list the nodes in the cluster.
- We have master in the cluster but needs to add the workers(nodes).
- **NODE GROUP** is the group of instances(nodes) of same type. Cluster is composed of different groups of nodes.
- Chatgpt is trained on kubernetes cluster.
- k8s is just an orchestration tool. Under the hood, it's all docker containers running inside the EC2 instances(or any other node).
- We provide k8s cluster containers, k8s decides where to run the containers.
- Suppose you have a docker conatiner that wants to communicate with the S3 service. By default this container has no permissions to communicate with the other aws service(s). This docker container needs to be authenticated. Idea of role can help us in this.
- Node IAM is the role we assign to every node in the node group. Sice the container is running inside the instance, we take this role, put it on EC2. EC2 assumes the role as a mask and can now enable the conatiner in it to access the S3 service.
- EC2 instances (worker) reside inside the cluster. We create a role that every node in the node-group is assigned to.
- Every node in the EKS cluster must have the default permissions. One of these permissions is "AmazonEC2containerRegistryReadOnly" that allows EC2 to read containers from ECR i.e. enables to pull images from the registry.
- Kubernetes is a declarative platform i.e. it allows us to declare what we want (in yaml files) amd k8s will do its best to fulfill our needs.

