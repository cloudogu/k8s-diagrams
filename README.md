k8s-diagrams
===

A collection of diagrams explaining kubernetes, extracted from our [trainings](https://cloudogu.com/en/trainings/),
[articles](https://cloudogu.com/en/blog/tag/k8s-security/) and talks 
([k8s sec](https://github.com/cloudogu/k8s-appops-security-talks), [k8s intro](https://github.com/cloudogu/k8s-intro-talk)).

The diagrams are realized using [PlantUML](https://plantuml.com/), so they're basically text and can be adjusted easily.  
Note that the diagrams don't use UML notation. They are rather box and line diagrams.

# Table of contents

<!-- Update with `doctoc --notitle README.md`. See https://github.com/thlorenz/doctoc -->
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Deployment ➜ Pod ➜ Container](#deployment-%E2%9E%9C-pod-%E2%9E%9C-container)
- [Pod ➜ Node](#pod-%E2%9E%9C-node)
- [Services, Nodes and Pods explained](#services-nodes-and-pods-explained)
- [Services, Nodes and Pods explained (including IP addresses)](#services-nodes-and-pods-explained-including-ip-addresses)
- [Rolling Update](#rolling-update)
- [Authentication and Authorization](#authentication-and-authorization)
- [PodSecurityPolicy Activation via RBAC](#podsecuritypolicy-activation-via-rbac)
- [Troubleshooting Kubernetes PodSecurityPolicies](#troubleshooting-kubernetes-podsecuritypolicies)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


# Deployment ➜ Pod ➜ Container

Relationship between Deployment, Pod and Container.  
Simplified - leaves out ReplicaSets for brevity.

![](https://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/cloudogu/k8s-diagrams/master/diagrams/deploy-pod-container.puml&fmt=svg)


# Pod ➜ Node

Relationship between Pod and Node.  

![](https://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/cloudogu/k8s-diagrams/master/diagrams/pod-node.puml&fmt=svg)


# Services, Nodes and Pods explained

Traffic flow from Cloud LoadBalancer via Service to Pods running on Nodes.

![](https://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/cloudogu/k8s-diagrams/master/diagrams/services.puml&fmt=svg)


# Services, Nodes and Pods explained (including IP addresses)

Traffic flow from Cloud LoadBalancer via Service to Pods running on Nodes.
Including different address IP address ranges and ports:

* external IP,
* node internal and external IP and node port,
* service IP,
* pod IP and target port (on container)

![](https://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/cloudogu/k8s-diagrams/master/diagrams/services-with-ip.puml&fmt=svg)


# Rolling Update

![](https://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/cloudogu/k8s-diagrams/master/diagrams/rolling-update.puml&fmt=svg)


# Authentication and Authorization

Flow from user API server request to response: check authn via identity provider, then authz via RBAC.    

![](https://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/cloudogu/k8s-diagrams/master/diagrams/k8s-auth.puml&fmt=svg)


# PodSecurityPolicy Activation via RBAC

Connection from Pod to PSP via RBAC (Role, RoleBinding, ServiceAccount).

![](https://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/cloudogu/k8s-diagrams/master/diagrams/psp-rbac.puml&fmt=svg)


# Troubleshooting Kubernetes PodSecurityPolicies

A diagram to help debugging Kubernetes PodSecurityPolicies.

![](https://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/cloudogu/k8s-diagrams/master/diagrams/troubleshooting-k8s-psps.puml&fmt=svg)
