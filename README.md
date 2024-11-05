# kubernetes-notes

### Kuberenetes :
* Kuberenetes is a container orchestration environment that offers capabilities like auto scaling, auto healing and enterprise level support like load balancing

### Kuberenetes Architecture :
* On a broad level, we can divide the k8's components into two parts;
 - Control plane : Api server, ETCD, control manger, schedule manager
 - Data plane : Kubelet, kube-proxy, container-runtime

### Pod :
* A Pod in kubernetes is a runtime specification of a container in docker. A pod provides more declarative way of defining using yaml and you can run more than one continer in a pod. It is the smallest deployable unit in kubernetes

### Namespace :
* Isolated project space where we can create resources related to our project

### labels :
* Labels are used to identify the resources
### Annotations:
* Syntax is same as labels but have some advantages like long structure key-value pairs, can use special characters and to store external information(to identify external resources)


### Environment :
* Setted at containers. Env values can be accessed inside containers

### Resouces :
- Helps us to allocate/set the resource limits to our resources/objects.
- Requests - soft limits
- Limit - Hard limits

### Configmap :
   - Used to supply configs to our services/resources
   - configmap is an api object used to store non-confidential data in key-value pairs
   - pods can consume configmaps as environment variables, command line arguments or as configuration files in a volume.
   - Configmap does not provide secrecy or encryption. if you want store the data confidential data use secrets or thirdparty tools
### Secrets :
* SecretsTo store confidential information(echo admin|base 64)

### Services:
* Pods are Ephemeral in nature, IP address are temporary/keep changing when pods is up and down. we can address this with service.3 services:
  - Cluster IP : Default service, used for internal communication within the cluster.
  - NodePort : Pods can face the internet, Nodeport will open a port on each node and traffic will be routed to services through random port.
  - Loadbalancer : Forwards the external traffic to the services with load balancing

### Sets :
- There are 4 types of sets;
  - Replica : Creates replica of pod, ensures desired no of pods are always running
  - Deployment : Provides declarative way to update applications such as image, no of pods
  - Daemonset : Ensures that a pod runs on every node(useful for monitoring)
  - Stateful : Each pod will have own volume associated, Pods are created in orderly manner
  
### Headless service :
* A service which will not have cluster IP is called headless service. In a clustering application if a request comes for one pod it search other nodes in cluster through nslookup of headless service


### Volumes :
* volume are two types;
  - Static provisiong : volume(EBS&EFS),PV,PVC
  - Dynamic provosionong : SC, PVC
  - PV(Persistent Volume) : Used to represent volume inside kubernetes with a resource called PV. This is equivalent storage inside cluster.
  - PVC(Persistent Volume Claim) : Pods can claim volume through resource PVC
  - Storage class(SC) : volume+PV
  



### RBAC:
*  Role based access contraol is used for autherization
  - Role & RoleBinding : Useful at ns level
  - ClusterRole & ClusterRoleBinding : For different ns, entire at cluster level


### Ingress controller :
* The ingress controller adds a layer of abstraction to traffic routing, accepting traffic from outside the kubernetes platform and load balancing it to pods running inside the platform./Ingress controller is an exteranl component to eks cluster through which eks receives traffic. ALB is LB in the ingress controller public hits ALB through the routse53. Based on the ingress resources traffic is routed to the pod through service

### :
*


