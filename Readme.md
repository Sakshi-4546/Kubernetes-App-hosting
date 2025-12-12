#  K8s Two-App Hosting Demo using Ingress

This project demonstrates how to host and expose two different applications on a Kubernetes cluster consisting of one Master node and one Worker node. It uses a LoadBalancer Service along with Ingress to route traffic to multiple applications through a single external DNS.
The applications used in this demo are:

**App1 → nginx (Nginx web server)**

**App2 → httpd (Apache web server)**  
To access the applications:

<LoadBalancer-DNS>/app1 → Nginx app

<LoadBalancer-DNS>/app2 → Apache app

## Step-By-Step

### Step1 : Connect to master server and install ingress controller
- kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/cloud/deploy.yaml

![](./Img/Screenshot%20(1).png)  

### Step 2 : Create 3 YAML files 
1) app1.yml

![](./Img/Screenshot%20(181).png)
2) app2.yml

![](./Img/Screenshot%20(182).png)
3) ingress.yml

![](./Img/Screenshot%20(183).png)

### Step 3 : Apply app1.yml,app2.yml file and ingess.yml
 Before applying ingress.yml run the following command  and then apply 
- kubectl delete validatingwebhookconfiguration ingress-nginx-admission

![](./Img/Screenshot%20(2).png)
![](./Img/Screenshot%20(3).png)

### Step 4 : Create one target group
![](./Img/Screenshot%20(4).png)
- Add ingress loadbalacer port inside tagert group

![](./Img/Screenshot%20(5).png) 
- Select your worker instance for register targets

![](./Img/Screenshot%20(6).png)
- Create target group

![](./Img/Screenshot%20(7).png)
 
### Step 5 : Create one Application LoadBalancer 
- Add port range 30000-32768 inside worker instance security group

![](./Img/Screenshot%20(10).png)

### Step 6 : Copy the loadbalancer DNS and access in your browser
### Add /app1 at the end of DNS

![](./Img/Screenshot%20(12).png)
### Add /app2 at the end of DNS

![](./Img/Screenshot%20(13).png)





