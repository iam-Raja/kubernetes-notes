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
  - Pods are Ephemeral in nature, IP address are temporary/keep changing when pods is up and down. we can address this with service.3 services:
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
 - volume are two types;
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

##


1. Explain the deployment manifest file? - 
- A deployment manifest file in Kubernetes is a YAML or JSON file that defines the desired state of an 
application, including the number of replicas, container images, resource requirements, and other 
configurations. It is used by Kubernetes to manage and maintain the state of the application. 

2. Choreography vs. orchestration in Kubernetes?  
- Choreography: Each service works independently and interacts with other services through events 
without a central controller. - Orchestration: A central controller manages the interactions and coordination between services, 
ensuring that the workflows are executed in a specific order. 

3. What is the difference between stateless and stateful microservices? 
- Stateless microservices do not retain any internal state between requests. Each request is independent.- Stateful microservices maintain state across requests, requiring persistent storage to retain data 
between sessions. 

4. What is the role of domain events in microservices? 
- Domain events are used to communicate changes or significant occurrences within a microservices to 
other microservices. They help maintain eventual consistency across the system by propagating changes 
asynchronously. 

5. How are the pods communicating with each other?
- Pods communicate with each other using Kubernetes Services, which provide stable IP addresses and 
DNS names. Services can be of type ClusterIP, NodePort, or Load Balancer, facilitating internal and external 
communication. 

6. What is pod security policy
- Pod Security Policy (PSP) is a cluster-level resource in Kubernetes that controls security-sensitive 
aspects of the pod specification. It defines a set of conditions that a pod must meet to be accepted by the 
system, such as running as a non-root user or using specific volume types. 

7. What is the Blue/Green Deployment Pattern
- Blue/Green Deployment involves maintaining two identical environments (blue and green). The blue 
environment is the active one, and the green environment is where new changes are deployed. Once 
validated, traffic is switched from blue to green, ensuring zero downtime. 

8. How do you secure microservices
- Secure microservices by implementing mutual TLS for service-to-service communication, using API 
gateways for centralized security policies, managing secrets securely, and applying network policies to 
control traffic. 

9. What is a service in Kubernetes? How many types are there? 
- A Kubernetes Service is an abstraction that defines a logical set of pods and a policy for accessing them. 
Types of Services include ClusterIP (default, internal traffic), NodePort (external traffic to a specific port), 
Load Balancer (external traffic using a load balancer), and ExternalName (external service mapping). 

10. How does ingress help in Kubernetes? 
- Ingress manages external access to services within a Kubernetes cluster, typically via HTTP/HTTPS. It 
provides routing rules to manage traffic, enabling features like load balancing, SSL termination, and name
based virtual hosting. 

11. What is API versioning and why is it important in microservices? 
- API versioning allows different versions of an API to coexist, enabling backward compatibility and safe 
evolution of the API. It is important to prevent breaking changes and to allow clients to transition to newer 
API versions at their own pace. 

12. What are taints and tolerations in Kubernetes and how do they work? 
- Taints are applied to nodes to repel pods that do not have matching tolerations. Tolerations are applied 
to pods to allow them to be scheduled on nodes with matching taints, enabling control over which pods 
can be scheduled on specific nodes.
 
13. Handling increased traffic on Kubernetes Cluster? 
- Handle increased traffic by scaling pods horizontally using the Horizontal Pod Autoscaler (HPA), 
optimizing resource requests and limits, using a load balancer, and ensuring efficient resource utilization. 

14. What are some common issues you might encounter when spinning up a container in 
Kubernetes? 
- Common issues include image pull errors, incorrect configurations in the manifest file, resource limits 
not set appropriately, networking issues, and insufficient permissions. 

15. Comprehensive Backup Strategy for Kubernetes? 
- A comprehensive backup strategy includes regular snapshots of etcd, backing up persistent volumes, 
using tools like Valero for automated backups and restores, and ensuring application-level backups for 
stateful applications. 


