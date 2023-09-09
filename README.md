# Assignment1
##Task1: Setup Initial Infrastructure

Google Cloud Console helps in managing several cloud services. In Task 1, I created a Kubernetes cluster in Google Cloud Console. Through GKE (Google Kubernetes Engine) an environment can be managed for deploying, managing, and scaling containerized application on Google infrastructure.

The first thing I did was create an account in Google Cloud Console. Under the Kubernetes Engine, I created two clusters; one manually and the next with the commands. 
For manually, clicked on the “create” button, added a name, location, and created. The cluster “clustertask1” was created. 

I created the second cluster giving a command on the terminal on project A1Task1 and project id: a1task1-398409

gcloud config set project a1task1-398409 #for setting up a new project

gcloud config set compute/zone australia-southeast1 #for setting up a location in my zone

gcloud container clusters create-auto cluster cluster-task1 #created a cluster name clustertask1

gcloud container clusters get-credentials cluster-task1 #retrives the details of cluster's authentication credential and configuration updating the 'kubectl' configuration file

The cluster was created. 

##Task2: Microservices Architecture and Deployment

Firstly, I went through the Saleor functionalities and its repositories. 
Saleor API is a Python and Django-based open-source GraphQL-based e-commerce framework that is used as the back-end component in the development of recent and efficient e-commerce platforms. 
Saleor Storefront is a user-facing component of an e-commerce platform which makes customer interact on a page having a speedy response integrating with the Saleor API. Being a Progressive Web App, it is user-friendly on both the web and mobile devices. 
Likewise, Saleor Dashboard is used for managing an e-commerce site driven by the backend (Saleor API) and the frontend (Saleor Storefront) which gives a user-friendly interface for performing the tasks. 
Saleor Platform uses docker compose and acts as a centralized repository for configuring and cordinating with many components of the Saleor e-commerce platform. It allows to manage and combine three components; Saleor API, Saleor Platform, and Saleor Dashbaord. 

###Assigning port 9003 to Saleor Dashbaord
As the task suggested, I forked the Saleor platform repository. With the guidelines given, I was able to run all the applications on the located port. 
For cloning the repository, the command was used:
  git clone https://github.com/mahimaaryal/saleor-platform
After cloning, went to the cloned directory:
  cd saleor-platform
Built the application:
  docker compose build
Applied Django Migration:
  docker compose run --rm api python3 manage.py migrate
Populated the data with example data and created the adminuser:
  docker compose run --rm api python3 manage.py populatedb --createsuperuser
Finally, ran the application:  
  docker compose up

From the above code, I was successful on running the application on the below port:
Saleor Core (API) - http://localhost:8000
Saleor Dashboard - http://localhost:9000
Jaeger UI (APM) - http://localhost:16686
Mailpit (Test email interface) - http://localhost:8025

Changing the Saleor Dashbaord port on 9003
For changing the port, I edited the docker-compose.yml file. 
After changing the port, for restarting, I used a command on the terminal:
  docker compose stop
  docker compose up -d
The port then was successfully run on- http://localhost:9003
***
Here is the github repository: https://github.com/mahimaaryal/saleor-platform
***

###Configuring the React Storefront to operate on 3009
Similar to the above task, I forked the the saleor/react-storefront repository and followed the guidelines.
After forking, I edited the docker-compose.yml file and changed the port into 3009. 
Though the port has been changed into - http://localhost:3009
There is 500 error on the React Storefront dashbaord. 
***
Here is the github repository: https://github.com/mahimaaryal/react-storefront
***





