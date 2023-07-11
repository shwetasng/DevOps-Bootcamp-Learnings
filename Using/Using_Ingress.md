## HOW DO I EXPOSE MY APPLICATION TO THE WORLD?
- If you have an application running in Kubernetes cluster then how do you show it to the world? It is done using INGRESS CONTROLLER.
- First ingress-nginx controller is deployed in the cluster. This is only done once per cluster. Command: kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.8.1/deploy/static/provider/aws/deploy.yaml
- After that we checked the logs of ingress-nginx controller pods

<img width="638" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/b7fc8228-7083-4cb4-9d3c-be6828603828">

- Then we went to Route53 service in aws which is a DNS service and there a URL is already made for us to use.
<img width="960" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/74b56fd4-ada9-41fb-9472-2902d6a1c0b3">

- we want to route our traffic to load balancer as shown in the picture. ref:https://aws.amazon.com/blogs/opensource/network-load-balancer-nginx-ingress-controller-eks/
<img width="347" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/1731ca7c-6d22-42ba-a1e6-43f03361e09e">

- Add a subdomain A record for the upes-int-devops-23.com domain (e.g. my-2048.upes-int-devops.com). The record should have an alias to the NLB created by EKS after the ingress controller has been deployed. STEPS TO DO THIS:
  <img width="889" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/37eb48d1-b1f8-47fe-a408-2f856544b9b7">
  <img width="797" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/6f071722-01e8-4229-a686-ccbee1d15c55">
- After this I created frontend-ingress.yaml file and put in the required code in it.
  <img width="638" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/60e22cbd-f448-4d92-a73d-e264d72d3c7d">



  

