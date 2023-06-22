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

![22-6-23b](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/1966a6eb-174d-4807-abe2-7cff7008963e)


![22-6-23c](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/8c1c59c2-7cf8-47ee-9c42-3edcbad107a9)


![23-6-23d](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/d8fa86aa-20de-4ed2-91d4-998df8c6d92c)


![22-6-23e](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/45654ea2-7964-4d5c-b1fd-5bf9c3e8af8d)

![22-6-23f](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/7a0fff68-149c-4925-9cdc-e9fcb89c3921)

![22-6-23g](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/1c67d575-d207-4800-897d-498a409c8627)

![22-6-23h](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/899b894c-b0f9-4387-8b2f-3e4f63c2a4bf)

![22-6-23j](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/5d255234-41a2-4bd3-8694-a6d37214d12f)

![22-6-23k](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/7f0bc1cc-058b-4f35-8c70-a4f2b952ea74)
![22-6-23l](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/f0c6b0de-fd26-45fe-ac4e-0a158c9d13c3)



![22-6-23m](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/e8d50098-a828-459f-ba3a-c5af7b7fa265)

![22-6-23n](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/68624468-2877-43c9-a175-32af9b81a6ce)

![22-6-23o](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/0238c6e3-85c2-4ec0-8032-73a6ae4a2b4c)
![22-6-23p](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/ed14dcf0-83ab-4c79-9854-7dc3e1fd963c)
![22-6-23q](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/2658e621-18c2-4f04-9aab-e897b602da3d)

![22-6-23r](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/3623623d-4f6e-41f8-848c-8c916a0b9d01)

![22-6-23s](https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/110754474/ea609f68-34b8-4aeb-b21e-370d5c09a453)



