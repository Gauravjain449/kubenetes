Day 1: 
---
![Alt text](https://d33wubrfki0l68.cloudfront.net/26a177ede4d7b032362289c6fccd448fc4a91174/eb693/images/docs/container_evolution.svg)

Kubernetes can expose a container using the DNS name or using their own IP address.

Kubernetes provides: Service discovery and load balancing, Storage orchestration, Automated rollouts and rollbacks, Automatic bin packing, Self-healing, Secret and configuration management,

You can deploy and update secrets and application configuration without rebuilding your container images, 

Kubernetes is not a traditional, all-inclusive PaaS (Platform as a Service) system. Since Kubernetes operates at the container level rather than at the hardware level, it provides some generally applicable features common to PaaS offerings, such as deployment, scaling, load balancing, and lets users integrate their logging, monitoring, and alerting solutions. However, Kubernetes is not monolithic, and these default solutions are optional and pluggable.

Does not deploy source code and does not build your application. Continuous Integration, Delivery, and Deployment (CI/CD) workflows are determined by organization cultures and preferences as well as technical requirements.

Day2:
---
![Alt test](https://d33wubrfki0l68.cloudfront.net/7016517375d10c702489167e704dcb99e570df85/7bb53/images/docs/components-of-kubernetes.png)

Control plane components can be run on any machine in the cluster. However, for simplicity, set up scripts typically start all control plane components on the same machine, and do not run user containers on this machine.

Control Plane component that runs controller processes:- 
Logically, each controller is a separate process, but to reduce complexity, they are all compiled into a single binary and run in a single process.

These controllers include:

Node controller: Responsible for noticing and responding when nodes go down.
Replication controller: Responsible for maintaining the correct number of pods for every replication controller object in the system.
Endpoints controller: Populates the Endpoints object (that is, joins Services & Pods).
Service Account & Token controllers: Create default accounts and API access tokens for new namespaces

The following controllers can have cloud provider dependencies:
Node controller: For checking the cloud provider to determine if a node has been deleted in the cloud after it stops responding
Route controller: For setting up routes in the underlying cloud infrastructure
Service controller: For creating, updating and deleting cloud provider load balancers

Day 3:
---
kube-node-lease This namespace for the lease objects associated with each node which improves the performance of the node heartbeats as the cluster scales

Setting the namespace preference
You can permanently save the namespace for all subsequent kubectl commands in that context.

kubectl config set-context --current --namespace=<insert-namespace-name-here>
# Validate it
kubectl config view --minify | grep namespace:
  
Not All Objects are in a Namespace
Most Kubernetes resources (e.g. pods, services, replication controllers, and others) are in some namespaces. However namespace resources are not themselves in a namespace. And low-level resources, such as nodes and persistentVolumes, are not in any namespace.

To see which Kubernetes resources are and aren't in a namespace:

# In a namespace
kubectl api-resources --namespaced=true

# Not in a namespace
kubectl api-resources --namespaced=false


Day 4:
---
https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/
The API currently supports two types of selectors: equality-based and set-based.

Caution: For both equality-based and set-based conditions there is no logical OR (||) operator.

Equality-based requirement are =,==,!=

Set-based requirement are in,notin and exists

Set-based requirements can be mixed with equality-based requirements.
For example: partition in (customerA, customerB),environment!=qa

using equality-based one may write:

kubectl get pods -l environment=production,tier=frontend
or using set-based requirements:

kubectl get pods -l 'environment in (production),tier in (frontend)'


IMP
---
In Service and ReplicationController only equality-based requirement selectors are supported.
e.g. 

selector:
    component: redis
    
Resources that support set-based requirements:-
Newer resources, such as Job, Deployment, ReplicaSet, and DaemonSet, support set-based requirements as well.
e.g.
selector:
  matchLabels:
    component: redis
  matchExpressions:
    - {key: tier, operator: In, values: [cache]}
    - {key: environment, operator: NotIn, values: [dev]}
    
---
Day 5:
https://kubernetes.io/docs/concepts/architecture/nodes/

To mark a Node unschedulable, run: kubectl cordon $NODENAME

Capacity and Allocatable











