 Flask App Deployment using Docker & Kubernetes (Minikube)

This project demonstrates how to containerize a simple Python Flask" web application using "Docker", and deploy it on a local "Kubernetes" cluster using "StatefulSet". The app is exposed using both "ClusterIP" and "NodePort" services for internal and external access.



 Project Overview

 🐍 Built a basic Flask web application
 🐳 Containerized the app using Docker
 ☸️ Deployed it to Kubernetes using a StatefulSet
 🌐 Exposed the app via ClusterIP (internal) and NodePort (external)
 🧪 Tested using `kubectl` and browser on Minikube


 🛠️ Tech Stack

| Tool         | Purpose                        |
|--------------|--------------------------------|
| Python       | Backend language               |
| Flask        | Lightweight web framework      |
| Docker       | Containerization               |
| Kubernetes   | Orchestration of containers    |
| StatefulSet  | Manages stateful pods          |
| Minikube     | Local Kubernetes cluster       |
| YAML         | K8s config files               |


1. Start Minikube
     minikube start

2. Use Docker inside Minikube
   minikube docker-env | Invoke-Expression

3. Build Docker image
   docker build -t flask-stateful-app:latest .

4. Apply Kubernetes Manifests
   kubectl apply -f k8s/

5. Check Services
   kubectl get svc

6. Quick Test from Inside Minikube VM
        minikube ssh
        curl http://localhost:30036
If this works, your app is fine and your Windows firewall or Docker NAT is blocking access from the host.

7. Last Resort: Port-Forwarding
If NodePort still doesn’t work externally, just use:

kubectl port-forward svc/flask-nodeport 5000:80

Now Open on browser:  http://localhost:5000
"This always works since it bypasses networking and directly tunnels traffic."


Finally: Use Minikube Addons Dashboard

   --minikube dashboard
"This opens a full UI where you can inspect services, pods, logs, etc."


   




   






