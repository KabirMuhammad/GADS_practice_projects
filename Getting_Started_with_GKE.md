## Lab: Google Cloud Fundamentals: Getting Started with GKE

## Objectives

In this lab, you learn how to perform the following tasks:

    - Provision a Kubernetes cluster using Kubernetes Engine.

    - Deploy and manage Docker containers using kubectl.

Task 1: Sign in to the Google Cloud Platform (GCP) Console with the credentials generated for you by Google

Task 2: Confirm that needed APIs are enabled: Kubernetes Engine API and Container Registry API

Task 3: Start a Kubernetes Engine cluster

    1.  Click the top right toolbar icon to activate Cloud Shell

    2. Type in this command to store your preffered zone in a variable "MY_ZONE" for convinience:

        export MY_ZONE=us-central1-a

    3. Start a Kubernetes cluster managed by Kubernetes Engine. Name the cluster webfrontend and configure it to run 2 nodes

        gcloud container clusters create webfrontend --zone $MY_ZONE --num-nodes 2

    4. Check your installed version of Kubernetes 

        kubectl version
    
Task 4: Run and deploy a container

    1. Launch a single instance of the nginx container

        kubectl create deploy nginx --image=nginx:1.17.10

    2. View the pod running the nginx container

        kubectl get pods
    
    3. Expose the nginx container to the Internet with an external Load balancer and an IP address attached to it.

        kubectl expose deployment nginx --port 80 --type LoadBalancer

    4. View the new service

        kubectl get services

    5. Scale up the number of pods running in your service 

        kubectl scale deployment nginx --replicas 3

    6. Confirm that Kubernetes has updated the number of pods 

        kubectl get pods
    
    7. Confirm that your external IP address has not changed

        kubectl get services

    8. In this lab, you configured a Kubernetes cluster in Kubernetes Engine. You populated the cluster with several pods containing an application, exposed the application, and scaled the application.
