
### KUBERNETES

Kubernetes uses linux container technologies to provide isolation of running applications.
Kubernetes is a software system that allows you to easily deploy and manage containerized applications on top of it. It relies on the features of Linux containers to run heterogeneous applications without having to know any internal details of these
applications and without having to manually deploy these applications on each host.
how exactly containers can isolate processes
if they’re running on the same operating system. Two mechanisms make this possible.
The first one, Linux Namespaces, makes sure each process sees its own personal view of
the system (files, processes, network interfaces, hostname, and so on). The second
one is Linux Control Groups (cgroups), which limit the amount of resources the process
can consume (CPU, memory, network bandwidth, and so on).

### NAMESPACES
All system resources, such as filesystems, process IDs, user IDs, network interfaces, and others, belong to the
single namespace. But you can create additional namespaces and organize resources
across them. When running a process, you run it inside one of those namespaces. The
process will only see resources that are inside the same namespace. Well, multiple
kinds of namespaces exist, so a process doesn’t belong to one namespace, but to one
namespace of each kind.
 The following kinds of namespaces exist:
 Mount (mnt)
 Process ID (pid)
 Network (net)
 Inter-process communication (ipc)
 UTS
 User ID (user)


### LIMITING RESOURCES AVAILABLE TO A PROCESS (CONTROL GROUP)
The other half of container isolation deals with limiting the amount of system
resources a container can consume. This is achieved with cgroups, a Linux kernel feature that limits the resource usage of a process (or a group of processes). A process
can’t use more than the configured amount of CPU, memory, network bandwidth, and so on. This way, processes cannot hog resources reserved for other processes, which is similar to when each process runs on a separate machine.

### KUBERNETES FUNCTIONS

##### Service Discovery

##### Scaling
Kubernetes can even automatically scale the whole cluster size up or down based on the needs of the
deployed applications.

##### Load-Balancing

##### Self-Healing
Kubernetes monitors your app components and the nodes they run on and automatically reschedules them to other nodes in the event of a node failure.

##### Leader Election


### KUBERNETES ARCHITECTURE OF A KUBERNETES CLUSTER

 The master node, which hosts the Kubernetes Control Plane that controls and manages the whole Kubernetes system
 Worker nodes that run the actual applications you deploy

### THE CONTROL PLANE

The Control Plane is what controls the cluster and makes it function. It consists of
multiple components that can run on a single master node or be split across multiple
nodes and replicated to ensure high availability. These components are
 The Kubernetes API Server, which you and the other Control Plane components
communicate with.
 The Scheduler, which schedules your apps (assigns a worker node to each deployable component of your application)
 The Controller Manager, which performs cluster-level functions, such as replicatset, deployment, statefulset, daemonset, job components, keeping track of worker nodes, handling node failures,
and so on
 etcd, a reliable distributed data store that persistently stores the cluster
configuration.


### THE NODES

The worker nodes are the machines that run your containerized applications. The
task of running, monitoring, and providing services to your applications is done by
the following components:
 container runtime, which runs your containers
 The Kubelet, which talks to the API server, run , and manages containers on its node
 The Kubernetes Service Proxy (kube-proxy), which load-balances network traffic
between application components