------------- Using the Cloud Console -----
To create a vm via the console; 
1. Open the console and search for the navigation menu [-], click Compute Engine > VM Instances.
2. Name: gcelab2
   machine-type: e2-medium
   region: us-central1
   zone: us-central1-a
   boot-disk: 10GB
   firewall: Allow HTTP traffic
   
4. Click SSH to the right of the instance name, gcelab and install "NGINX"
   ```
   sudo apt-get update && sudo apt-get install nginx
   ```
6. Open the browser with the instance public-IP and the nginx default web page should be loading.
  ```
  open http://INSTANCE-EXTENAL-IP
  ```
7. DONE

------------- Using the Cloud Shell -----
To create a vm via the Cloud Shell;
1. click in to open the Cloud Shell to a new windown and run the folowing cmds.
  ```
  gcloud config set project PROJECT_ID
  
  export REGION=us-central1
  export ZONE=us-central1-a
  
  gcloud compute instances create gcelab2 --machine-type e2-medium --zone=$ZONE --tags http-server
  ```

2. Enable and get the SSH set up to access the instance
   ```
   gcloud compute ssh gcelab2 --zone=$ZONE
   ```
   
3. The firewall for the HTTP is alrady set by adding the tags (http-server) or adding a new one;
   ```
   gcloud compute instances add-tags gcelab2 --tags http-server,https-server
   ```

5. Open the browser with the instance public-IP and the nginx default web page should be loading.
  ```
  open http://INSTANCE-EXTENAL-IP
  ```
5. DONE
