## QUESTIONS:-
- What happens during rolling out an update?
- How k8s kills the pods?
- How does the organizations achieved zero downtime before the introduction of Kubernetes?

## READINESS PROBE
- It's an important probe that helps in rolling out an update or a new version of the application.
- Kubernetes allows to update the conatiner with zero downtime using readiness probe.
- It helps to check that whether the application is ready to accept the request of the user or not. Application nmay even fail to accept the request even if it is up and running healthy.
- Liveliness Probe checks whether the application is running healthy or not whereas Readiness Probe checks that whether the application is ready to accept the requests or not.

### Usage of Readiness Probe in Zero Downtime
- Consider having a deployment with two replica sets in it : New Replica Set and Old Replica Set.
- We have pods running inside the old replica set intially and have no pods inside the new replica set.
- We are considering the situation where we are rolling out an update i.e. updating the version of the application.
- During rolling out an update k8s kill the old pods and creates the new pods of the new version. Once all the pods from the old replica set have been killed by the kubernetes and all the new pods gets created in the new replica set, k8s finally kills the old replica set.
- When k8s kills the pods from the old replica set, it was still handling the user request, thus ,the request gets failed.
- This is how k8s kills the pod:-
  - Pods are containers and under the hood containers are the processes. So containers(i.e. pods) can be killed the same way we kill the processes i.e. by using the SIGNALS. k8s sends the SIGTERM to the pod before killing it.
  - For pod to gracefully terminate and don't fail the user request, we want it to receive SIGTERM such that it fails in Readiness Probe. Once the pod receives the SIGTERM, it fails the readiness probe indicating to the k8s that I am going to be killed soon and unavailable to receive new requets. Thus, stop routing new requests to me.
  - In this way, even without loosing a single user request, zero downtime is achived using the readiness probe.

### Screenshots frm today's class:-

![22-6-23a](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/9a025c44-7cd8-4607-a022-f9688f947436)

