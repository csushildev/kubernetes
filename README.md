# kubernetes: 
Kubernetes Architecture : 
We essential have two components in Kubernetes Architecture : 
- Control Plane
- Data Plane

Control Plane ? 
In a Kubernetes cluster, the control plane is responsible for managing the cluster and its components. It consists of several key components that work together to maintain the desired state of the cluster.

API Server:

The API Server is the central management entity of Kubernetes. It acts as the front end for the Kubernetes control plane.
All administrative tasks, as well as communication and interaction with the cluster, are handled through the API server.
It validates and processes RESTful requests, stores the cluster state, and exposes the Kubernetes API.
Scheduler:

The Scheduler is responsible for determining where and how to run pods (the smallest deployable units) based on resource availability, policies, and constraints.
It watches for new pods with no assigned node and selects an appropriate node for them to run on, considering factors like resource requirements, affinity/anti-affinity, and other constraints.
Etcd:

Etcd is a distributed key-value store that acts as the cluster's backing store for all cluster data.
It stores the entire state of the Kubernetes cluster, including configurations, metadata, and the actual state of each object in the cluster (like pods, services, and more).
Etcd is a highly available and consistent datastore, crucial for maintaining the cluster's state.
Controllers:

Controllers are control loops that watch the state of the cluster through the API server and work towards achieving the desired state.
They are responsible for managing different aspects of the cluster, such as node control, replication, endpoints, namespaces, and more.
Each controller aims to ensure that the actual state of the cluster matches the desired state specified in the cluster's configuration.
CCM (Cloud Controller Manager):

CCM is a component responsible for integrating the Kubernetes cluster with the underlying cloud provider's infrastructure.
It abstracts the cloud-specific code from the core Kubernetes components, allowing Kubernetes to run seamlessly across different cloud environments.
CCM manages external cloud resources like load balancers, volumes, and instances, translating Kubernetes API requests into the cloud provider's specific API calls.
These components collectively form the control plane, enabling Kubernetes to manage and orchestrate containerized applications efficiently, ensuring high availability, scalability, and resilience within the cluster.


Data Plane : 

The data plane components in Kubernetes are responsible for managing and maintaining the containers and their networking within the cluster.

Kubelet:

Kubelet is an agent that runs on each node in the cluster and ensures that containers are running in a Pod as expected.
It communicates with the Kubernetes API server to receive instructions about which containers to run.
Kubelet manages the container lifecycle on the node, handling container creation, destruction, and monitoring. It interacts with the container runtime to perform these operations.
It also performs health checks on containers, ensuring they are running and reporting their status to the control plane.
Kube-proxy (Kubernetes Proxy):

Kube-proxy is responsible for network proxying and load balancing within the cluster.
It manages network connectivity to services by maintaining network rules (iptables rules) that allow communication to reach the correct pods and services.
Kube-proxy implements the Kubernetes service concept by enabling access to services regardless of the underlying pod's location, handling load balancing and routing traffic to the appropriate pods.
Container Runtime:

The container runtime is the software responsible for running containers. Kubernetes supports various container runtimes such as Docker, containerd, and others.
It provides the necessary tools and libraries to manage container images, create and run containers, manage their lifecycle, networking, and storage.
Container runtimes interface with the underlying operating system's kernel to manage container processes, isolation, resource constraints, and more.
Significance of Data Plane Components:

Container Orchestration: Kubelet, kube-proxy, and the container runtime collectively form the foundation of the data plane, responsible for executing and managing containers based on the instructions received from the control plane.

Resource Management: These components ensure that containers are appropriately created, scheduled, and managed across the cluster's nodes while adhering to resource constraints and configurations specified by the control plane.

Networking: Kube-proxy handles networking by providing a virtual IP and load balancing for services. It ensures that services remain accessible and can route traffic to the appropriate pods regardless of their location within the cluster.

Operational Integrity: Kubelet performs health checks and manages container lifecycle, ensuring that the containers are healthy and running as expected. It reports the container's status back to the control plane, contributing to the overall cluster's operational integrity.

Together, these data plane components ensure that containers run effectively, are appropriately connected, and adhere to the desired state specified by the control plane, contributing to the smooth operation of a Kubernetes cluster.
