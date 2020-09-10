## Lab: Google Cloud Fundamentals: Getting Started with Compute Engine

## Objectives:

In this lab, you will learn how to perform the following tasks:

    - Create a Compute Engine virtual machine using the Google Cloud Platform (GCP) Console.

    - Create a Compute Engine virtual machine using the gcloud command-line interface.

    - Connect between the two instances.

Task 1: Sign in to the Google Cloud Platform (GCP) Console with the credentials generated for you by Google
    
1. Click the top right toolbar icon to activate Cloud Shell

Task 2: Create a Compute Engine virtual machine instance using the GCP console with firewall rules to allow HTTP services

    1. Create a firewall rule with tag "http"
        
        gcloud compute firewall-rules create allow-http --action=ALLOW --direction=INGRESS --rules=http:80 --target-tags=http

    2. Type the command to create the Compute Engine instance with the HTTP firewall tag 

        gcloud compute instances create "my-vm-1" --machine-type "n1-standard-1"  --image-project "debian-cloud"  --image "debian-9-stretch-v20190213" --subnet "default" --tags http

   
Task 3: Create a virtual machine using the gcloud command line

    1. Set the zone in which to launch the compute Engine virtual machine
       
        gcloud config set compute/zone us-central1-b

    2. Create a VM instance called my-vm-2 in that zone

        gcloud compute instances create "my-vm-2" --machine-type "n1-standard-1" --image-project "debian-cloud" --image "debian-9-stretch-v20190213" --subnet "default"

Task 4: Connect between VM instances

    1. Click SSH to open a command prompt in VM-2 and ping VM-1

        ping my-vm-1

    2. Press Ctrl+C to abort the ping command and SSH into VM-1 on same command window

        ssh my-vm-1

    3. Install the Nginx web server on VM-1 

        sudo apt-get install nginx-light -y

    4. Use the nano text editor to add a custom message to the home page of the web server and replace your name in the h1 header.

        sudo nano /var/www/html/index.nginx-debian.html

    5. Press Ctrl+O and then press Enter to save your edited file, and then press Ctrl+X to exit the nano text editor

    6. Confirm that the web server is serving your new page. At the command prompt on my-vm-1, execute this command

        curl http://localhost/

    7. The response will be the HTML source of the web server's home page, including your line of custom text.To exit the command prompt on my-vm-1, execute this command

        exit

    8. You will return to the command prompt on my-vm-2. To confirm that my-vm-2 can reach the web server on my-vm-1, at the command prompt on my-vm-2, execute this command 
        
        curl http://my-vm-1/

    9. The response will again be the HTML source of the web server's home page, including your line of custom text.
    
    10. In this lab, you created virtual machine (VM) instances in two different zones and connected to them using ping, ssh, and HTTP. End your lab
