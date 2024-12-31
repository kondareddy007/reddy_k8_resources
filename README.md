configured components in VM
route53 with IP address

1. traffic
2. self healing
3. load balancing

autoscaling
launch templates
target groups
load balancers

1. we have a docker host where all containers are running
	what if docker host crash? we lose all containers
	even we use docker volumes, data is still in the host, so we lost data as well
2. what if traffic increases/decreases? are our containers scalable
3. even we have multiple containers to balance the load? who is the LB here?
4. what if some container crashes? can docker make it available again?
5. what about configurations and secrets? where to store them?
6. what if we have multiple hosts running with containers

we need some orchestrator?

kubernetes is popular container orchestration tool. 

docker is used for building the images...it can also run containers but have lot of above disadvantages..

minikube --> it is a single node cluster.. master and node is same. it is just to practice few k8 resources.

kubeconfig --> is the files contains authentication information to connect kubernetes cluster

kubectl --> to connect kubernetes cluster

kubectl will check automatically a file

~/.kube/config

kubernetes
---------------
resources

Namespace --> it is like a project in your kubernetes cluster to provision your project resources. it is isolated

every resource is YAML...a basic syntax is

apiVersion:
kind: # what kind of resource you are creating
metadata:
	name:

kubectl create -f <your.yaml> --> create resources, if you use this once again, you get error
kubectl apply -f <your.yaml> --> if not created it will create, if you use again any changes it will update or it will say unchanged.

kubectl delete -f yamlfile.yaml --> delete the resources

kubectl get namespaces --> will get all namespaces in cluster

kubectl get nodes

pod --> a simple container, it is a smallest deployable unit in kuberenetes

pod vs container
-----------------
a pod can contain multiple containers, it is the smallest thing in kuberenetes

docker run -d -p 80:80 -v nginx:/usr/share/nginx/html --name roboshop-nginx nginx

services:
	nginx:
	  image: nginx
	  container_name: web
	  port:
	  - "80:80"
	  volumes:
	  - source:
		target:

labels vs annotaions
--------------------
labels --> have some limitation on the length and charecters of key and values
annotaions --> no limit on length and special charecters also can be used...

labels are used to select other kubernetes resources.
annotaions are used to select external resources to kubernetes.
