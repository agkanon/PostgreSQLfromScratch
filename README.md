# PostgreSQLfromScratch

## Deploy PostgreSQL by Creating Configuration from Scratch in kubernetes cluster.

Manual configuration of Postgres on Kubernetes allows you to fine-tune your deployment configuration.

## Step 1: Create and Apply ConfigMap 
The ConfigMap resource contains the data that is used during the deployment process. The most important part of the file is the data section, where you provide a name for the database, the username, and the password for logging into the PostgreSQL instance.

## Step 2: Create and Apply Persistent Storage Volume and Persistent Volume Claim
Apply the resources with kubectl, The system confirms the successful creation of both PV and PVC.
Check that the PVC is connected to the PV with the following command:
   ## kubectl get pvc
The status of the PVC is Bound, and the PVC is ready to be used in the PostgreSQL deployment.

## Step 3: Create and Apply PostgreSQL Deployment
The deployment file contains configuration of the PostgreSQL deployment and provides specifications for the containers and volumes. 

## Step 4: Create and Apply PostgreSQL Service
Apply the configuration with kubectl, The system confirms the successful creation of the service.


## Use the following command to list all resources on the system.

   ## kubectl get all
The pod and the deployment show the 1/1 ready status. The desired number of replica sets reflect what is configured in the deployment YAML file.

## Step 5: Connect to PostgreSQL
1. When all the resources are ready, use kubectl exec to log into the PostgreSQL instance.
     ## kubectl exec -it [pod-name] --  psql -h localhost -U admin --password -p [port] postgresdb
2. The system asks for the password. Type in the password defined in Step 1 and press Enter. The psql command prompt appears.


The database is now ready to receive user input.


