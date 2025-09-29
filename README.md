# Minikube-K8sCluster

#Prerequisites (powershell)
>> Install Docker Desktop for windows from official website
>> Install kubectl CLI
curl -LO "https://dl.k8s.io/release/v1.28.0/bin/windows/amd64/kubectl.exe"
Move-Item .\kubectl.exe C:\Windows\System32\kubectl.exe
kubectl version --client
>> Install Minikube for windows
https://github.com/kubernetes/minikube/releases/latest (minikube-windows-amd64.exe)
minikube version
if not working (Move minikube.exe => C:\Windows\System32 to C:\Minikube\minikube.exe then edit environment variables and restart the machine)
still not working (Set-Alias minikube "C:\Minikube\minikube.exe" => minikube version and keep the powershell in running)

#Start Minikube Cluster (powershell)
minikube start --driver=docker
minikube status
kubectl get nodes

#Create YAML Files (bash)
deployment.yml & service.yml then push it into github

#Deploy to Kubernetes (bash)
kubectl apply -f deployment.yml
kubectl apply -f service.yml

#Verify and Manage Pods/Services (bash)
>> Check pods and services:
kubectl get pods
kubectl get services
>>Scale your deployment to 3 replicas:
kubectl scale deployment nginx-deployment --replicas=3
kubectl get pods
>>Describe pods and view logs:
kubectl describe pods (make sure everything is running eg:docker)
kubectl logs <pod-name>

#Access the App (powershell)
kubectl get services
minikube service <nginx-service> (name of the service)
