* Kubernetes is a portable, extensible, open-source platform for managing containerized workloads and services.
* Google open-sourced the Kubernetes project in 2014.

https://d33wubrfki0l68.cloudfront.net/26a177ede4d7b032362289c6fccd448fc4a91174/eb693/images/docs/container_evolution.svg

* **Canary deployments are a pattern for rolling out releases to a subset of users or servers. The idea is to first deploy the change to a small subset of servers, test it, and then roll the change out to the rest of the servers.**

* Kubernetes can expose a container using the DNS name or using their own IP address. If traffic to a container is high, Kubernetes is able to load balance and distribute the network traffic so that the deployment is stable.

* Kubernetes allows you to automatically mount a storage system of your choice, such as local storages, public cloud providers, and more.

* Since Kubernetes operates at the container level rather than at the hardware level, it provides some generally applicable features common to PaaS offerings, such as deployment, scaling, load balancing, logging, and monitoring.

* Does not limit the types of applications supported. Kubernetes aims to support an extremely diverse variety of workloads, including stateless, stateful, and data-processing workloads. If an application can run in a container, it should run great on Kubernetes.

## The Kubernetes API

* The kubectl command-line tool can be used to create, update, delete, and get API objects.
* Kubernetes also stores its serialized state (currently in etcd) in terms of the API resources.

## Understanding Kubernetes Objects

* Most often, you provide the information to kubectl in a .yaml file. kubectl converts the information to JSON when making the API request.

### Kubernetes Object Management



