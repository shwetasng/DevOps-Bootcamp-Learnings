## HOW DO I EXPOSE MY APPLICATION TO THE WORLD?
- If you have an application running in Kubernetes cluster then how do you show it to the world? It is done using INGRESS CONTROLLER.
- First ingress-nginx controller is deployed in the cluster. This is only done once per cluster. Command: kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.8.1/deploy/static/provider/aws/deploy.yaml
- After that we checked the logs of ingress-nginx controller pods

<img width="638" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/b7fc8228-7083-4cb4-9d3c-be6828603828">

- Then we went to Route53 service in aws which is a DNS service and there a URL is already made for us to use.
<img width="960" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/74b56fd4-ada9-41fb-9472-2902d6a1c0b3">

