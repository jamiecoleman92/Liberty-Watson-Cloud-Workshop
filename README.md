# Cloud-native Java Workshop with Watson and Cloudant

This workshop demonstrates the use of MicroProfile, Docker, Kubernetes and Istio technologies for implementing, deploy and update a set of cloud-native microservices. The workshop has be structured as four modules:
* **Module 1** covers the foundational technologies for producing and consuming REST services with some added extras like talking to Watson and storing your data in a no-sql database.
* **Module 2** covers the technologies essential for developing and deploying microservices at scale where the microservices are the responsibility of autonomous teams.
* **Module 3** covers the observability operational needs of microservice deployments at scale, such as tracing request and understanding microservice health.
* **Module 4** covers the deployment, scaling and updating of microserivces at scale, through Kubernetes.

Each workshop module consists of a number of Open Liberty Guides each of which demonstrates a key cloud-native microservice technology. Each Guide is
designed to be taken independently so if you just want to learn about a specific technology you can just take that guide. If, however, you're goal is to learn about all the technologies, then working through them in the order shown below is recommended.

## Table of Contents
- [Cloud-native Java Workshop](#cloud-native-java-workshop)
  - [Table of Contents](#table-of-contents)
  - [Workshop Preparation](#workshop-preparation)
    - [Pre-requisites](#pre-requisites)
    - [Downloads](#downloads)
- [Introduction](#introduction)
- [Module 1: REST Foundation with Watson and Cloudant](#module-1-rest-foundation-with-watson-and-cloudant)
    - [Creating a RESTful web service](#creating-a-restful-web-service)
    - [Injecting dependencies into microservices](#injecting-dependencies-into-microservices)    
    - [Consuming RESTful services with template interfaces](#consuming-restful-services-with-template-interfaces)
    - [Utilizing a Watson service on the IBM Cloud](#utilizing-a-watson-service-on-the-ibm-cloud)
    - [Storing data on the cloud with Cloudant](#Storing-data-on-the-cloud-with-cloudant)
- [Module 2: Scalable Microservice Development](#module-2-scalable-microservice-development)
    - [Configuring Microservices](#configuring-microservices)
    - [Building fault-tolerant microservices with the @Fallback annotation](#building-fault-tolerant-microservices-with-the-fallback-annotation)
    - [Securing microservices with JSON Web Tokens](#securing-microservices-with-json-web-tokens)
    - [Documenting RESTful APIs](#documenting-restful-apis)
- [Module 3: Microservice Observability](#module-3-microservice-observability)
    - [Providing metrics from a microservice](#providing-metrics-from-a-microservice)
    - [Adding health reports to microservices](#adding-health-reports-to-microservices)
    - [Enabling distributed tracing in microservices](#enabling-distributed-tracing-in-microservices)
- [Module 4: Microservice Deployment and Update](#module-4-microservice-deployment-and-update)
    - [Deploying microservices to Kubernetes](#deploying-microservices-to-kubernetes)
    - [Configuring microservices running in Kubernetes](#configuring-microservices-running-in-kubernetes)
    - [Checking the health of microservices on Kubernetes](#checking-the-health-of-microservices-on-kubernetes)
    - [Deploying microservices to IBM Cloud](#deploying-microservices-to-ibm-cloud)



## Workshop Preparation

To save time during the workshop, it's best to set up your machine beforehand. The instructions below show the pre-requisites to install and how to avoid lengthy downloads.

### Pre-requisites

To use these guides you need the following pre-requisites:
1. A Java 8 JDK (e.g. https://adoptopenjdk.net/?variant=openjdk8&jvmVariant=openj9)
2. Apache Maven 3.5.4 or later (https://maven.apache.org/). Older versions may not work.
3. A git client
4. An editor with Java support (e.g. Eclipse, VS Code, IntelliJ)
5. Docker & Kubernetes:
   1. Windows: https://docs.docker.com/docker-for-windows/#kubernetes
   2. Mac: https://docs.docker.com/docker-for-windows/#kubernetes
   3. Linux: https://github.com/kubernetes/minikube#installation)
6. Helm V2.13.1: https://github.com/helm/helm/releases/tag/v2.13.1
7. IBM Cloud CLI:

    MAC: `curl -fsSL https://clis.cloud.ibm.com/install/osx | sh`

    LINUX: `curl -fsSL https://clis.cloud.ibm.com/install/linux | sh`

    WINDOWS: Open command prompt as an administrator and run the following command.
    `powershell -command "Set-ExecutionPolicy Unrestricted; iex(New-Object Net.WebClient).DownloadString('https://clis.cloud.ibm.com/install/powershell')"`
8. IBM Cloud Container Registry plug-in: To install the container registry plug-in, run the following command: `ibmcloud plugin install container-registry`
9. IBM Cloud Kubernetes Service plug-in: To install the Kubernetes registry plug-in, run the following command: `ibmcloud plugin install kubernetes-service`

### Downloads

If you will be taking the workshop at a location with limited network bandwidth, it is recommended you do the following beforehand in order to populate your local .m2 repo and Docker cache.

```
git clone https://github.com/gcharters/workshop-cloud-native-java.git
cd workshop-cloud-native-java
mvn install
docker build -t prime:mym2 .
```

# Introduction

Cloud-native is an approach to application development and deployment.  It's the product of a number of industry movements over the past 10-15 years - agile development practices, DevOps, Microservices and Cloud.  Cloud-native applications are developed using agile practices, use continuous integration/continuous delivery to streamline deployment, are architected around team-aligned microservices, and leverage the cloud for rapid deployment at scale.

When choosing which technologies to use for cloud-native microservices, the combination of open source and open standards can be very important.  The combination enables a low cost (free) of entry and at the same time avoids being locked in to a single vendor implementation.  

Eclipse MicroProfile is a set of industry specifications for developing and deploying cloud-native Java Microservices.  The specifications address the important challenges of cloud-native microservices, such as toleration of service failures, security, service metrics and health, and more.  Open Liberty is an open source, lightweight, composable Java server that implements the MicroProfile specifications.

Kubernetes is an Open Source platform for deployment, scaling and managing containers and services.  It uses a declarative yaml-based approach to describe deployments, for example, the containers to be deployed, their scaling requirements, the services they provide, and so on.

This workshop demonstrates how to address cloud-native microservice requirements using the combination of MicroProfile, Docker and Kubernetes technologies.  The workshop guides can be taken independently, or in the order they are introduced, below.

If you have feedback on a specific guide, we'd appreciated a github issue or pull request against that guide, and similarly if you have feedback on this workshop document, please raise an issue or submit a pull request.

# Module 1: REST Foundation with Watson and Cloudant


### Creating a RESTful web service

Learn how to create a REST service with JAX-RS, JSON-P, and Open Liberty that will expose the JVM’s system properties.

The Guide: https://openliberty.io/guides/rest-intro.html

If you have feedback or find problems, please raise an issue here: https://github.com/OpenLiberty/guide-rest-intro


### Injecting dependencies into microservices    

Learn how to use Contexts and Dependency Injection to manage and inject dependencies into RESTful web services.      

The Guide: https://openliberty.io/guides/cdi-intro.html

If you have feedback or find problems, please raise an issue here:
https://github.com/OpenLiberty/guide-cdi-intro


### Consuming RESTful services with template interfaces    

Learn how to use MicroProfile Rest Client to invoke RESTful microservices over HTTP in a type-safe way.      

The Guide: https://openliberty.io/guides/microprofile-rest-client.html

If you have feedback or find problems, please raise an issue here:
https://github.com/openliberty/guide-microprofile-rest-client

### Utilizing a Watson service on the IBM Cloud
Learn how to create a microservice using MicroProfile to talk to an online cloud service using provided API's.

The Guide: https://github.com/jamiecoleman92/guide-watson-openliberty

If you have feedback or find problems, please raise an issue here:
https://github.com/jamiecoleman92/guide-watson-openliberty

### Storing data on the cloud with Cloudant
Learn how to store your data (JSON) on the cloud using a no-sql database called cloudant.

The Guide: https://github.com/jamiecoleman92/guide-cloudant-openliberty

If you have feedback or find problems, please raise an issue here:
https://github.com/jamiecoleman92/guide-cloudant-openliberty

# Module 2: Scalable Microservice Development

### Configuring Microservices

Learn how to inject external static and dynamic configuration to microservices using MicroProfile Config.

The Guide: https://openliberty.io/guides/microprofile-config.html

If you have feedback or find problems, please raise an issue here:
https://github.com/OpenLiberty/guide-microprofile-config


### Building fault-tolerant microservices with the @Fallback annotation

Learn how to use the MicroProfile Fault Tolerance specification to enable applications to function even when one
of the microservices is unavailable.

The Guide: https://openliberty.io/guides/microprofile-fallback.html

If you have feedback or find problems, please raise an issue here:
https://github.com/OpenLiberty/guide-microprofile-fallback


### Securing microservices with JSON Web Tokens

You’ll explore how to control user and role access to microservices with MicroProfile JSON Web Token (MicroProfile JWT).

The Guide: https://openliberty.io/guides/microprofile-jwt.html

If you have feedback or find problems, please raise an issue here:
https://github.com/OpenLiberty/guide-microprofile-jwt


### Documenting RESTful APIs

Explore how to document and filter RESTful APIs from code or static files by using MicroProfile OpenAPI.

The Guide: https://openliberty.io/guides/microprofile-openapi.html

If you have feedback or find problems, please raise an issue here:
https://github.com/OpenLiberty/guide-microprofile-openapi


# Module 3: Microservice Observability


### Providing metrics from a microservice

Learn how to provide system and application metrics from a microservice using MicroProfile Metrics.

The Guide: https://openliberty.io/guides/microprofile-metrics.html

If you have feedback or find problems, please raise an issue here:
https://github.com/OpenLiberty/guide-microprofile-metrics


### Adding health reports to microservices

Learn how to provide and check the health of a microservice using MicroProfile Health.

The Guide: https://openliberty.io/guides/microprofile-health.html

If you have feedback or find problems, please raise an issue here:
https://github.com/OpenLiberty/guide-microprofile-health


### Enabling distributed tracing in microservices

Explore how to enable and customize tracing of JAX-RS and non-JAX-RS methods by using MicroProfile OpenTracing.

The Guide: https://openliberty.io/guides/microprofile-opentracing.html

If you have feedback or find problems, please raise an issue here:
https://github.com/OpenLiberty/guide-microprofile-opentracing


# Module 4: Microservice Deployment and Update


### Deploying microservices to Kubernetes

Deploy microservices in Open Liberty Docker containers to Kubernetes and manage them with the Kubernetes CLI, kubectl.

https://openliberty.io/guides/kubernetes-intro.html

If you have feedback or find problems, please raise an issue here:
https://github.com/OpenLiberty/guide-kubernetes-intro


### Configuring microservices running in Kubernetes

Explore how to externalize configuration using MicroProfile Config and configure your microservices using Kubernetes ConfigMaps and Secrets.

https://openliberty.io/guides/kubernetes-microprofile-config.html

If you have feedback or find problems, please raise an issue here:
https://github.com/OpenLiberty/guide-kubernetes-microprofile-config


### Checking the health of microservices on Kubernetes

Learn how to check the health of microservices on Kubernetes by setting up readiness probes to inspect MicroProfile Health Check endpoints.

https://openliberty.io/guides/kubernetes-microprofile-health.html

If you have feedback or find problems, please raise an issue here:
https://github.com/OpenLiberty/guide-kubernetes-microprofile-health


### Deploying microservices to IBM Cloud

Explore how to deploy microservices to IBM Cloud Kubernetes Service (IKS) and IBM Cloud Private (ICP).

https://openliberty.io/guides/cloud-ibm.html

If you have feedback or find problems, please raise an issue here:
https://github.com/OpenLiberty/guide-cloud-ibm
