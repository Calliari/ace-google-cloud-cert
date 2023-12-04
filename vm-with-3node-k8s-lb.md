Topics tested:

1. Create an instance
2. Create a 3-node Kubernetes cluster and run a simple service
3. Create an HTTP(s) load balancer in front of two web servers

------------------------------------
Task 1. 
Create a project jumphost instance
Create a VM name: jumphost
Use an e2-micro machine type.
Use the default image type (Debian Linux).

------------------------------------
Task 2. 
Create a Kubernetes service cluster
Create a zonal cluster using <filled in at lab start>.
Use the Docker container hello-app (gcr.io/google-samples/hello-app:2.0) as a placeholder; the team will replace the container with their own work later.
Expose the app on port App port number.

------------------------------------
Task 3. 
Set up an HTTP load balancer
Create an HTTP load balancer with a managed instance group of 2 nginx web servers with the startup script
  ```
  cat << EOF > startup.sh
  #! /bin/bash
  apt-get update
  apt-get install -y nginx
  service nginx start
  sed -i -- 's/nginx/Google Cloud Platform - '"\$HOSTNAME"'/' /var/www/html/index.nginx-debian.html
  EOF
  ```

3.a) Create an instance template.
3.b) Create a target pool.
3.c) Create a managed instance group.
3.d) Create a firewall rule named as Firewall rule to allow traffic (80/tcp).
3.f) Create a health check.
3.g) Create a backend service, and attach the managed instance group with named port (http:80).
3.h) Create a URL map, and target the HTTP proxy to route requests to your URL map.
3.i) Create a forwarding rule.

