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
