🚀 Kubernetes on Minikube (Windows)

This repo documents how to set up Kubernetes locally with Minikube on Windows 11, deploy an Nginx app, and expose it via a service.

🔹 Prerequisites
Windows 11 Pro

Docker Desktop (docker.com ) installed and running

Chocolatey package manager installed

Basic PowerShell knowledge

🔹 Step 1: Install Tools

powershell

choco install kubernetes-cli -y 

kubectl version --client

minikube version

🔹 Step 2: Start Minikube

powershell

minikube start

First run downloads base images (~700 MB).

Subsequent runs are faster.

Verify cluster:

powershell

kubectl get nodes

kubectl cluster-info

🔹 Step 3: Deploy Nginx

powershell

kubectl create deployment my-nginx --image=nginx:latest

kubectl get deployments

kubectl get pods

🔹 Step 4: Expose Service

powershell

kubectl expose deployment my-nginx --port=80 --type=LoadBalancer

kubectl get services

minikube service my-nginx


⚠️ Note: With Docker driver on Windows, Minikube opens a tunnel in your terminal to simulate a LoadBalancer.

Keep the terminal open while testing.

Access via the URL shown (e.g., http://127.0.0.1:61028).

Closing the terminal stops the tunnel.

🔹 Step 5: Dashboard & Metrics

powershell

minikube dashboard

minikube addons enable metrics-server

kubectl get pods -n kube-system


🔹 Step 6: Verify Pod

powershell

kubectl describe pod <pod-name>

kubectl logs <pod-name>


✅ Summary

Installed kubectl + minikube via Chocolatey

Started Minikube cluster with Docker driver

Deployed Nginx container

Exposed service via LoadBalancer (tunnel)

Accessed app in browser


Author:- Rahul Shukla DevOps Engineer