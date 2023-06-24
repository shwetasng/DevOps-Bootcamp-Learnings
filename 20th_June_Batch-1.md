## KUBERNETES
### Questions:-
- Why do we need to run same containers in different nodes(EC2 Instances)?
- In what case do we want two different containers to run close to each other i.e. within the same node(EC2 instance)?

### Learnings from classroom:-
- Consider a situation where we have 2 containers. The two containers need to communicate with each other for sharing the data with each other. Both of the containers stream a huge amount of data. Thus creates a load on the network. To reduce the load on the network it's better to place them within the single node.
- **KUBELET :** is a component of k8s. Whenever master wants to interact with the node, it sends the insructions to kubelet that allows commuincation between the master and the node.
- **KUBEPROXY :** it allows networking and communication between the containers located in different nodes.
- **APP DESCRIPTOR :** it's the description about the application. Description of how your service stack looks like.

- **"aws eks --region <region> update-kubeconfig --name <cluster-name>"** command is used to get credentials to get access to EKS cluster.
- **"kubectl get pods"** command displays the pods in default namespace but once the default namespcae is set to your own namespace, this command displays the pods in your respective namespace.
- **"kubectl create ns <your-alias-name>"** command is executed to create your namespcae within the cluster.
- **"kubectl get pods -n <your_ns_alias>"** command is used to list the pods in your respective namespace.
- **"kubectl config set-contex --current --namespace=<your_ns_alias>"** command to set the default namespace to your own namespace. It allows to work as default namespace with your own namespace. Any command you execute after executing this command gets executed in your own namespace.

- **NAMESPACE :** namespace is a virtual grouping mechanism used to organize and isolate resources within a Kubernetes cluster. Namespaces provide a way to partition a cluster into multiple virtual clusters, allowing different teams or applications to have their own logical space to work in. Namespaces serve as a scope for these resources, ensuring that objects are unique within a given namespace.

**STATELESS & STATEFUL APPLICATIONS:-**
- Stateless applications do not store any persistent data and treat each request as an independent transaction, while stateful applications rely on persistent data or state to maintain the application's context and process subsequent requests.

**POD:-**
- A pod is the atomic unit of deployment in Kubernetes. It is a logical abstraction that represents a group of tightly coupled containers that are scheduled together on the same node and share the same execution context.
- Each POD has its own POD ID.
- A pod can consist of one or more containers that are co-located and share the same resources and network namespace. Most of the time 1 container is placed in 1 pod. Containers within a pod can communicate with each other using localhost, and they can also share files and storage volumes.

**SERVICE:-**
- Service is the abstraction of k8s that allows to access the pods.
- Service has selectors in it that route traffic to relevant opds. Sevice is a load balancer itself.
- It has a service discovery ability that discover if there is any new pod with the relevant tag or label & route the traffic to that pod.
- For debugging purpose, we make the service available locally.
- A service is an abstraction that provides network connectivity and load balancing for a set of pods. It acts as a stable endpoint for clients to access the pods that are running an application or providing a specific service within the cluster.
- A service assigns a stable virtual IP address (ClusterIP) to a set of pods. This virtual IP remains constant even if the underlying pods are created, terminated, or scaled. Clients can use this IP address to access the pods providing the service.
- Services automatically distribute client requests across the pods associated with the service. This load balancing functionality ensures that traffic is evenly distributed and eliminates the need for clients to directly manage the individual pod instances.
- Services provide a DNS name that can be used to discover and access the pods. Clients can access the service using the service name, and Kubernetes takes care of routing the requests to the appropriate pods.

**DEPLOYMENT:-**
- Deployment is a set of relicated same pods. Most of the time these pods are stateless which means it doesn't matter which pods handles whhich request. Each pod in stateless state knows the data that other pod(s) knows and they all perform the same task.
- If deployment is the set of identical images, Replica Set is the set of same image(s) of the same version.
- Each time we introduce a new version, a new Replica Set gets created. Updating version is followed by 0 downtime.
- Deployments use Replica Sets as the underlying mechanism to manage and maintain the desired number of pod replicas. A Replica Set ensures that a specified number of identical pods are always running by creating or scaling the replicas based on the defined configuration.
- Deployments declare the desired state of the pods, including the number of replicas, container images, resource requirements, environment variables, and other configuration parameters. Kubernetes continuously monitors the actual state of the deployment and automatically takes actions to match the desired state.
- Deployments facilitate rolling updates by managing the deployment of new versions of the application. When a new version of the deployment is specified, Kubernetes gradually updates the pods to the new version while ensuring that the desired number of replicas is maintained. This allows for zero-downtime updates and rollbacks if necessary.
- Deployments support scaling the number of replicas up or down based on the workload demands.
- Deployments can define health checks to monitor the readiness and liveness of pods. Health checks can be configured to ensure that only healthy pods receive traffic and that any pods that become unresponsive or unhealthy are automatically restarted or replaced.

**ROLLING UPDATE :** creating new pods in new replica set slowly(used to upgrade the application seamlessly with zero downtime).
- We don't mind on which node the pod is running on, it's k8s responsibility to handle the allocation of pod(s) to the node.
- EXAMPLE - we deployed 2 nginx containers in the cluster and we need to route the traffic between these 2 containers using the load balancer.
- In k8s, everything(all the deployments, replica sets, pods etc.) is internal by default. We cannot access them from outside the cluster.

- **NOTE :** We can append different yaml code within the same file using '---' seperator.
- Deployment object has property of self-healing. If any of the pods amomg mentioned number of pods fails, k8s creates a pod immediately same as the failed pod or if any of the instance on whoch the pod was running gets failed, k8s self-healing property regenerates the new instance.
- To access the pods within the cluster,, we can use **"curl http://mynginx:8080"**, where 8080 is the service port.
- **PORT FORWARDING** is used to access the applicatiobs in the cluster using your local machine. This way we can communicate with pods within the cluster from our local system i.e. exposing the application locally.
- Port forwarding is used to establish a connection from a local machine to a specific pod within the cluster, allowing direct access to the pod's port. It creates a tunnel between the local machine and the selected pod, but it is limited to communication between the local machine and that specific pod.
- Port forwarding remains active as long as the kubectl command is running. If you terminate the command, the port forwarding is also terminated.
- Port forwarding is a convenient way to access services running within the cluster without exposing them publicly or configuring complex networking setups. However, it should be used for development, debugging, or troubleshooting purposes and not as a production-level solution.
  - EXAMPLE :- **"kubectl port-forward service/mynginx 9000:8080"** command involves 2 port mappings. One from local machine(9000) to service(8080) amd another from service(8080) to the container(80). Nginx web-server forwards the request on port 80.
