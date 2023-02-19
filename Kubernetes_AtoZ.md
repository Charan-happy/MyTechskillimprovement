source : techiestamp.com

# 1. Kubernetes - Introduction:

## what is kubernetes ?
- kubernetes is an opensource system for automating, scaling and managing the production code deployment of containarized applications.  It groups containers that makes up an application into logical units for easy management and discovery.

## why do we need kubernetes ?
- if we can able to deploy application on containers, why we need kubernetes.

- let's look at the scenario of deploying containerized application spanning multiple servers.

- Below are the steps involved in deploying a containerized application on the multiple servers withoout any container orchestration tools like kubernetes
- **1. Set up multiple servers:** you would need to setup multiple servers either on the cloud or on-premises to host containers
- **Install a container runtime:** You would need to install a container runtime such as docker on each of the servers.
- **Deploy containers:**next you need to deploy containers manually on each server. This could involve pulling container images and starting the containers on each of the servers.
- **manage networking:**You would need to manage the networking betweent the containers on the each server ensuring they can communicate with each other as needed. This could involve setting up network bridges , creating network segments or using other network configurations.
- **Manage scaling :** Inorder to scale the application, you need to manually add or remove the containers from an application.
- **Manage loadbalancing:** you need customized application to enable load balancing.


This process is time consuming, error-prone and doesnot provide automation and scalability features.

Here is where container orchestration tools like kubernetes comes into picture.

- using kubernetes you just have to worry about the application development and deploymnets. All remaining heavy lifting like networking, service to service communication across nodes, load balancing, resource scheduling, scalability and high availability are taken care of by kubernetes.

- overall kubernetes helps us to achieve the following.

**1.container orchestration:** automates the deployment, scaling and management of containers<br>
**2. Automatic scaling :**Horizontal and vertical scaling<br>
**3. self-healing:**detects and replaces failed containers<br>
**4. load balancing:** distributes incoming requests across multiple containers<br>
**5.service discovery and networking :**Manages the communication between the containers.<br>
**6. Rolling updates and rollbacks:**Deploy applications with zero downtime.<br>
**7.Resource management:** Manage CPU, memory and storage of containers<br>
**8. volume management:**manage persistant storage for the containers<br>
**9. config and secret management:**provides ways to externalize application configs and secrets and makes them accessible to applications running inside the containers.<br>

## 2. prerequisites to learn kubernetes

**1. Distributed system:** Learn about distributes system basics and their usecases in modern IT infrastructure.<br>
**2.Linux:** Eventhough kubernetes run on both windows and linux OS. Most of the production deployments happening on linux only. So, learning linux helps not only in deployment process but also in understanding architecture of kubernetes.
**3.Authentication and authorization:**It is must know concept for every software developer. It is recommended to learn it through analogy<br>
**4.key-value store:** It is a type of nosql database. Understand it helps a lot in kuberntes<br>
**5.API:** Kubernetes is an api driven system. so, we need to understand RESTFuL api and also try to understand gRPC API<br>
**6.YAML:** YAML stands for yet another markup language. it is a dataserialization language that can be used for datastorage and configuration files. it is a simple language with easily understandable syntax. Hence, it is better to learn YAML.<br>
**7.containers:**Kubernetes is all about managing the containers.so, good understanding of how containers work is essential.<br>
**8.service discovery:** it is one of the key areas of kubernetes. you need to have a basic knowledge of client side and server side service discovery. To put it simply client side service discovery, the request goes to a service registry to get the endpoints available for backend services. In server side service discovery, the request goes to load balancer and the load balancer uses the service registry to get the ending of backend service.<br>
**9.Networking basics:**
CIDR Notation & Type of IP Addresses<br>
L3, L4 & L7 Layers (OSI Layers)<br>
SSL/TLS: One way & Mutual TLS<br>
Proxy<br>
DNS & Ports<br>
IPTables<br>
Software Defined Networking (SDN)<br>
Virtual Interfaces<br>
Overlay networking<br>
**10. Familiarity with command line interface(CLI):**Kubernetes is primarily managed by using command line.<br>
**11. GIT**<br>We will make use of git for version control system and source code management.

# Kubernetes Architecture and administration

## kubernetes Architecture :
- 
 ![image](https://user-images.githubusercontent.com/89054489/219829342-0f6fa732-61aa-4bcc-bf84-f77fe40dc0f0.png)

cd : Devopscube

- The first thing we need to know about kubernetes is that it is a **distributed system**. Meaning it has multiple components spread across different servers over a network. These servers could be virtual machines or bare metal servers. we call it a kuberntes cluster.

- a kubernetes cluster consists of controlplane nodes and worker nodes.

**control plane**
- The control plane is responsible for container orchestration and maintaining the desired state of the cluster. It has the following components.

1. kube-apiserver<br>
2. etcd<br>
3. kube-scheduler<br>
4. kube-controller-manager<br>
5. cloud-controller-manager<br>

**worker nodes** 
- The worker nodes are responsible for running containerized applications. The worker node has the following components.

1. kubelet<br>
2. kube-proxy<br>
3. container runtime<br>

Now let's dig into the each one of the above components.

**1. kube-apiserver**
- The kube-apiserver is the central hub of the kubernetes cluster that exposes the kubernetes API
- End users and other cluster components talks with cluster via API server. very rarely monitoring systems and third-party services may talk to API servers to interact with the cluster.
- so, when you use kubectl to manage the cluster, at the backend you are actually communicating with the API server through HTTP REST APIs. However the internal cluster components like the scheduler, controller, etc talk to the API server using gRPC.
|gRPC|REST API|
|-----|-------|
|gRPC stands for google remote procedure call | REST API stands for Representational state transfer|
|It is a modern opensource high performance Remote Procedure call(RPC) framework used to build scalable and fast APIs. It can run in any environment.|It is a software architecture that imposes conditions on how an API should work. REST was initially created as a guideline to manage communication on a complex network like the internet| 
|These uses protocol buffers|These uses JSON or XML message formats|
|To signal errors, REST APIs use error codes| These uses HTTP Status codes|
|It is 7 times faster than REST APIs|It is slower when compared to gRPC|

- The communication between the API server and other components in the cluster happens over TLS(transport layer security) to prevent unauthorized access to the cluster.

![image](https://user-images.githubusercontent.com/89054489/219929059-7faf8e19-47d4-4edd-b147-b17138a333e7.png)

- kubernetes **API-server** is responsible for the following:

**1. API Management:**Exposes the cluster API endpoint and handles all API requests<br> 
**2. Authentication:**(using client certificates, bearer tokens, and HTTP basic Authentication) and Authorization (ABAC[attribute based access] and RBAC[Rolebased access] evaluation)<br>
3.Processing API requests and validating data for the API objects like pods[collections of containers that share the same resources and local network or in simple pod is the smallest execution unit in kubernetes], services etc <br>
4. It is the only component that communicates with etcd<br>
5. api-server coordinates all the processes between the control plane and worker node components.<br>

**etcd**

- kubernetes is the distributed system and it needs an effecient database like etcd to support  its distributed nature. etcd acts as both backend service discovery and a database. we can call it as the brain of kubernetes cluster.

- etcd is an opensource strongly consistent, distributed key-value store. so what does it mean ?
<br>
1. **Strongly consistent:** if an update is made to a node. strong consistency will ensure it gets updated to all the other nodes in the cluster immediately. <br>
2. **Distributed: ** etcd is designed to run on multiple nodes as a cluster without sacrificing consistency<br>
3. **Key value store** A non-relational database that stores data as keys and values. It also exposes a key-value API. The datastore is built on top of  **BboltDB** which is a fork of BoltDB.

- etcd uses **raft consensus algorithm** for strong consistency and availability. It works in a leader-member fashion for high availability and to withstand node failures.

so, how etcd works with kubernetes ?
- To put it simply, when you use kubectl to get kubernetes object details, you are getting it from etcd. Also when you deploy an object like pod, an entry gets created in etcd.

In short, Here is what you need to know about etcd ?

1. etcd stores all configurations, states, and metadata of kubernetes objects(pods, secrets, daemonsets, deploymnents, configmaps, statefulsets, etc)<br>
2. etcd allows a client to subscribe to the events using watch() API. Kubernetes api-server uses the etcd's watch functionality to track the changes in the state of an object.<br>
3. etcd exposes key-value API using gRPC also gRPC gateway is a RESTFUL proxy that translates all the HTTP API calls into gRPC messages. It makes it an ideal database for the kubernetes.<br>
4. etcd stores all objects under the /registry directory key in key-value format. For example, information on a pod named Nginx in the default namespace can be found under /registry/pods/default/nginx
- etcd is the only **statefulset** component in the control plane.

![image](https://user-images.githubusercontent.com/89054489/219936921-3b521262-d20a-439a-98c4-7f1272ba4ca7.png)

**kube-scheduler**

- The kube-scheduler is responsible for scheduling pods on worker nodes.
- when you deploy a pod, you specify the pod requirements such as CPU, memory, affinity, taints or tolerations, priority, persistent volume(PV), etc. The scheduler's primary task is to identify the create request and choose the best node for a pod that satisfies the requirement.

- The following image shows a high-level overview of **how the scheduler works**

![image](https://user-images.githubusercontent.com/89054489/219937274-ac51fc69-f25e-456f-af86-c4688d5aa5ff.png)

In a kubernetes cluster, there will be a morethan one workernode. So how does the scheduler select the node out of all worker nodes ?

Here is how the scheduler works.

1. To choose the best node, the kube-schduler uses **filling and scoring** operations.<br>
2. In filtering, the scheduler finds the best-suited nodess where the pod can be scheduled. for ex: if there are five worker nodes with resource availability to run the pod, it selects all five nodes. if there are no nodes, then the pod is unschedulable and moved to the schduling queue. if it is a large cluster, let's say 100 worker nodes, and the schduler doesn't iterate over all the nodes. There is a schduler configuration parameter called **percentageofnodestoscore**. The default value is typically 50% . So it tries to iterate over 50% of nodes in a round-robin fashion. if the worker nodes are spread across multiple zones, then the schduler iterates over nodes in different zones. For very large clusters the scheduler iterates over nodes in different zones. For very large clusters the default **percentageofnodetoscore** is 5%<br>
3. In the scoring phase, the scheduler ranks the nodes by assigning a score to the filtered worker nodes. The scheduler makes the scoring by calling multiple scheduling plugins. Finally, the worker node with the highest rank will be selected for scheduling the pod. if all the nodes have the same rank , then a random node will be selected.<br>
4. once the node is selected, the scheduler creates a binding event in the API server. Meaning an event to bind a pod and node.

In short, Things we should know about scheduler

1. It is a controller that listens to pod creation event in the API server<br>
2. The scheduler has two phases. **scheduling cycle** and **binding cycle**. Together it is called the scheduling context. The scheduling cycle selects the worker node and the binding cycle applies that changes to the cluster.<br>
3. The scheduler always places the high-priority pods ahead of the low-priority pods for scheduling. Also, in somecases, after the pod started running in the selected node, the pod might get evicted or moved to other nodes. <br>
4. you can create custom schedulers and run multiple schedulers in a cluster along with the native scheduler. When you deploy a pod you can specify the custom scheduler in the pod manifest. so the scheduling decisions will be taken based on the custom scheduler logic.<br>
5. The scheduler has a pluggable scheduling framework. meaning, you can add your custom plugin to the scheduling workflow.

**Kube controller Manager:**

#### what is controller ?
- controllers are programs that run infinite control loops. meaning it runs continuously and watches the actual and desired state of objects. If there is a difference in teh actual and desired state, It ensures that the kubernetes resource/object is in the desired state.<br>

As per official documentation:<br>
In kubernetes, controllers are control loops that watch the state of your cluster, then make or request changes where needed. each controller tries to move the current cluster state closer to the desired state.<br>

let's say you want to create a deployment, you specify the desired state in the manifest YAML file(declarative approach). For ex, 2 replicas, one volume mount, configmap etc. The in-built deployment controller ensures that the deployment is in the desired state all the time. if a user updates the deployment with 5 replicas, the deployment controller recognizes it and ensures the desired state is 5 replicas.

**Kubernetes controller manager** is a component that manages all the kubernetes controllers. kubernetes resources/objects like pods, namespaces, jobs, replicaset are managed by respective controllers. Also, the kube scheduler is also a controller managed by kube controller manager.

![image](https://user-images.githubusercontent.com/89054489/219939288-63476a42-83b1-4aa3-95d8-2281eb8b317a.png)

The following is the list of important built-in kubernetes controllers.

1. Deployment controller<br>
2. Replicaset controller<br>
3. Daemonset controller<br>
4. Job controller<br>
5. cronjob controller<br>
6. endpoint controller<br>
7. namespace controller<br>
8. service account controller<br>
9. node controller

In short, the following you should know about kube controller manager
- It manages all the controllers and the controllers try to keep the cluster in the desired state.
- You can extend kubernetes with custom controllers associated with a custom resource definition

**cloud controller Manager (CCM)**

when kubernetes is deployed in cloud environments, the cloud controller mmanager acts as a bridge between cloud platform APIs and the kubernetes cluster.


This way the core components can work independently and allow the cloud providers to integrate with kubernetes using plugins. (for ex: an interface between kubernetes cluster and AWS cloud API)


Cloud controller integration allows kubernetes cluster to provision cloud resources like instances(for nodes), load balancers (for services), and storage volumes (for persistant volumes)

![image](https://user-images.githubusercontent.com/89054489/219939900-46b2d1bc-d2cb-4b19-8374-fd8bf19e1ed0.png)

Cloud controller manager contains a set of cloud platform specific controllers that ensure the desired state of cloud specific components (nodes, loadbalancers, storage etc). Following are the 3 main controllers that are part of the cloud controller manager.

**1. Node controller:**This controller updates node related information by talking to the cloud provider API. For ex, node labeling & annotation, getting hostname, CPU & memory availability, nodes health etc.
**2. Route controller**It is responsible for configuring networking routes on a cloud platform. so that pods in different nodes can talk to each other.
**3. service controller:**It takes care of deploying load balancers for kubernetes services, assigning IP addresses etc

Following are some of the classic examples of cloud controller manager.

1. Deploying kuberenetes service of type load balancer. Here kubernetes provisions a cloud-specific loadbalancer and integrates with kuberentes service

2. Provisioning storage volumes (PV) for pods backed by cloud storage solutions.

overall Cloud Controller Manager manages the lifecycle of a cloud specific resources used by kubernetes.


**kubelet**

kubelet is an agent component that runs on every node in the cluster. It does not run as a container instead runs as a daemon, managed by systemd.

it is responsible for registering worker nodes with API serveer and working with the podspec(pod specification -YAML or JSON) primarily from the API server. PodSpec defines the containers that should run inside a pod, their resources (e.g; CPU and memory limits) and other settings such as environment variables, volumes and labels.

It then brings the podSpec to the desired state by creating containers.

To put it simply, kubelet is responsible for the following:

1. creating, deleting and modifying containers for the pod.<br>
2. Responsible for handling liveliness, readiness, and startup probes.<br>
3. Responsible for mounting volumes by reading pod configuration and creating respective directories on the host for the volume mount.<br>
4. collecting and reporting node and pod status via calls to the API server.


Kubelet is also a controller where it watches for pod changes and utilizes the node's container runtime to pull images, run containers etc.

Other than podSpecs from API server, kubelet can accept podspec form a file, HTTP endpoint, and HTTP server. A good example of "podSpec from a file" is kubernetes static pods.

static pods are controlled by kubelet, not the API server.

This means you can create pods by providing a pod YAML location to the kubelet component.However static pods created by kubelet are not managed by the API server.

![image](https://user-images.githubusercontent.com/89054489/219944499-a4ed5970-7c11-4ce7-949c-acb14a15bced.png)

Here is the real-world example use case of the static pod.

while bootstrapping the control plane, kubelet starts the api server, scheduler, and controller manager as static pods from podspec located at /etc/kubernetes/manifests

Following are the some of the key things about kubelet:

1. kubelet uses the container runtime(CRI) gRPC interface to talk to the container runtime.<br>
2. It also exposes an HTTP endpoint to stream logs and provides exec sessions for clients.<br>
3. it uses CRI(container storage interface) gRPC to configure block volumes. <br>
4. It uses the CNI plugin configured in the cluster to allocate the pod IP address and set up any necessary network routes and firewall rules for the pod.

**Kubeproxy**

To understand kube proxy, you need to have a basic knowledge of kubernetes service & endpoint objects.

service in kubernetes is a way to expose a set of pods internally or to external traffic. when you create the service object, it gets a virtual IP assigned to it. it is called cluster IP. it is only accessible within the kubernetes cluster.

The Endpoint object contains all the IP addresses and ports of pod groups under a service object. the end point controller is responsible for maintaining a list of pod IP addresses (endpoints). The service controller is responsible for configuring endpoints to a service.

you cannot ping the cluster IP because it is only used for service discovery. unlike pod IPs which are pingable.

now let's get into the Kube Proxy.

Kube proxy is a daemon that runs on every node as a daemonset. It is a proxy component that implements the kubernetes service concept for pods.(single DNS for a set of pods with load balancing) .

when you expose pods using a service(cluster IP) kubeproxy creates network rules to send traffic to the backend pods (endpoints) grouped under the service object. Meaning all the service discovery and load balancing are handled by the kubeproxy.

![image](https://user-images.githubusercontent.com/89054489/219945433-3be7c95c-d8ac-406f-83ae-618ecc2a421e.png)

so, how does kube-proxy work ?

Kube proxy talks to the API server to get the details about the service (clusterIP) and respective pod IP's & ports (endpoints). It also monitors for changes in service and endpoints.

kubeproxy then uses any of the following modes to create/update rules for routing traffic to pods using a service.

1.**IPTables:** It is the default mode. In IPTables mode, the traffic handled by the IPTable rules. In this mode, kube-proxy chooses the backend pod random for load balancing. once the connection is established, the requests go to the same pod until the connection is terminated.
<br>
2.**IPVs:** for clusters with services exceeding 1000, IPVs offers performance improvement. it supports the following load-balancing algorithms for the backend.
<br>
1. rr: round-robin: it is the default mode<br>
2. lc: least connection (smallest number of open connections)<br>
3.dh: destination hashing<br>
4.sh: source hashing<br>
5.sed: shortest expected delay<br>
6.nq: never queue 

3.**username:** legacy & not recommended
4. **kernelspace** This mode is only for windows systems


**Container Runtime**

Just like Java Runtime(JRE), how needed for running java programs on a host. In the sameway, container runtime is a software component that is required to run containers.

container run time runs on all the nodes in the kubernetes cluster. It is responsible for pulling images from container registries, running containers, allocating and isolating resources for containers, and managing the entire lifecycle of a container on a host.

To understand more about it let's have a look at the following two key concepts:

1. **Container runtime interface:** it is a set of APIs that allows kubernetes to interact with different container runtimes. It allows different container runtimes to be used interchangeably with kubernetes. The CRI defines the API for creating , starting , stopping, and deleting containers, as well as for managing images and container networks.<br>
2,**open container initiative(OCI)** It is a set of standards for container formats and runtime.

- All the container runtimes implement the CRI interface and expose gRPC CRI APIs (runtime and image service endpoints)

How does kubernetes make use of the container runtime ?

- As we learned in the kubelet section, the kubelet agent is responsible for interacting with container runtime using CRI APIs to manage the lifecycle of a container. It also gets all the container information from the container runtime and provides it to the control plane.

![image](https://user-images.githubusercontent.com/89054489/219946492-f5fed8f7-245b-4b0a-a79b-9756e0b2d45a.png)

1. When there is a new request for a pod from API server, the kubelet takes the crio daemon to launch the required containers via kubernetes container runtime interface.
<br>
2, CRI-O checks and pulls the required container image from the configured container registry using `containers/image` library.<br>
3. CRI-O then generates OCI runtime specification (JSON) for a container.<br>
4. CRI-O then launches an OCI-compatible runtime(runc) to start the container process as per the runtime specification.


**CNI Plugin (Addon)**

It is a plugin based architecture with vendor neutral specification and libraries for creating network interfaces for containers.

It is not specific to kubernetes. with CNI container networking can be standardized across container orchestration tools like kubernetes, Mesos, Cloudfoundry, podman, docker etc.

when it comes to container networking, companies might have different requirements such as network isolation, security, encrption, etc. As container technology advanced, many network providers created CNI-based solutions for containers with a wide range of networking capabilities. You can call it as CNI-Plugins

This allows users to choose a networking solution that best fits their needs from different providers.

How does CNI Plugin work with Kubernetes ?

1. The kube-controller-manager is responsible for assigning pod CIDR to each node. Each pod gets a unique IP address from the pod CIDR<br>
2. kubelet interacts with container runtime to launch the scheduled pod. The CRI plugin which is part of the container runtime interacts with CNI plugin to configure the pod network <Br>
3. CRI plugin enables networking between pods spread across the same or different nodes using an overlay network.


![image](https://user-images.githubusercontent.com/89054489/219947277-bd58d0f6-141a-471f-b446-b9a2e20d43ed.png)

The following are the high-level functionalities provided by CNIPlugins.

1.pod networking<br>
2. Pod network security & isolation using network policies to control the traffic flow between pods and between namespaces.

Some popular CNI plugins include:

1. calico<br>2. Flannel<br>3. Weave Net<br>4.Cilium (uses eBPF)<br>5. Amazon VPC CNI (for AWS VPC)<Br>7. Azure CNI (for Azure virtual network) kubernetes networking is a big topic and it differs based on the hosting platforms.







