# LAB: Google Cloud Fundamentals: Getting Started with Compute Engine

## Objectives
* Create a Compute Engine virtual machine using the Google Cloud Platform (GCP) Console.

* Create a Compute Engine virtual machine using the gcloud command-line interface.

* Connect between the two instances.



1. Create a Compute Engine virtual machine using the Google Cloud Platform (GCP) Console

#### Steps
    gcloud compute instances create "my-vm-1" \
    --machine-type "n1-standard-1" \
    --image-project "debian-cloud" \
    --image "debian-9-stretch-v20190213" \
    --subnet "default" \
    --tags http

    gcloud compute firewall-rules create  allow-http --action=ALLOW --destination=INGRESS --rules=http:80 --target-tags=http

* Part of the instructions for this first task was that for the firewall rule, we should "Allow HTTP traffic".
* When you select the option to allow http traffic while creating a compute engine instance in the cloud console, a firewall rule is created in the background to allow access to that instance 
* So basically when you create an instance and you want to allow HTTP traffic, firstly you create a tag(tagname = http) for the instance like we did on the 3rd to the last line above, and then a firewall rule is created to target any instance with that tag


2. Create a virtual machine using the gcloud command line
#### Steps
* To list all zones associated with the us-central1 region, we use 

    gcloud compute zones list | grep us-central1

* To choose a new zone, we use
    gcloud config set compute/zone us-central1-f

* Now to create a VM called my-vm-2

gcloud compute instances create "my-vm-1" \
--machine-type "n1-standard-1" \
--image-project "debian-cloud" \
--image "debian-9-stretch-v20190213" \
--subnet "default" 


3. Connect between VM instances
#### Steps

    1. Use the ping command to confirm that my-vm-2 can reach my-vm-1 over the network:

        - Connect to my-vm-2
            gcloud compute ssh my-vm-2

        - ping my-vm-1 from my-vm-2
            ping -c 4 my-vm-1

        - Use ssh command to open a command prompt on my-vm-1 from my-vm-2:
            
            ssh my-vm-1

        -At the command prompt on my-vm-1, install nginx web server:

            sudo apt-get install nginx-light -y

        -Use the nano text editor to add a custom message to the home page of the web server:

            sudo nano  /var/www/html/index.nginx-debian.html

        -Add text like this, and replace YOUR_NAME with your name:

            Hi from YOUR_NAME

        -Exit the editor and confirm that the web server is serving your new page. At the command prompt on my-vm-1, execute this command 

            curl http://localhost/  

        -Result:
                The response will be HTML source of web server's home page, including your line of custom text.

        -To exit the command prompt on my-vm-1, execute this command:

            exit


        
