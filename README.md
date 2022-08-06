# NGINX Reverse Proxy Deployment in Kubernetes:

Here, I have deployed two laravel applications along with two nodeport services as kubernetes object. To get these application as per API call we need to deploy nginx as a reverse proxy. As need to load custom configuration file into container that's why I use hostpath /nginx-confg as volumes with /etc/nginx/conf.d/default.conf container path as volumemounts and also mentioned the node to deploy defining nodeSelector option since it's volumes as hostpath.

Since we're accessing the application via nginx nodeport service that's why I configure default.conf file mentioning the application's service name and container's port where to exposing like below.

proxy_pass http://laravel-svc:8000/app1;

where, laravel-svc is service name for applicaiton one and 8000 is the container port. But we can create application service type as ClusterIP because we're accessing the application through nginx proxy. 





