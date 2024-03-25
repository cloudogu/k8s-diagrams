k8s-diagrams
===

A collection of diagrams explaining kubernetes, extracted from our 
- [k8s trainings](https://cloudogu.com/en/trainings/?mtm_campaign=k8sdiagrams&mtm_kwd=trainings&mtm_source=github&mtm_medium=link)
- [k8s AppOps Security eBook](https://my.cloudogu.com/kubernetes-appops-security-ebook) (German)
- [blog articles](https://cloudogu.com/en/blog/tag/k8s-security/?mtm_campaign=k8sdiagrams&mtm_kwd=blog&mtm_source=github&mtm_medium=link) 
- and talks ([k8s sec](https://github.com/cloudogu/k8s-appops-security-talks), [k8s intro](https://github.com/cloudogu/k8s-intro-talk))

===

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
- [Ingresses explained](#ingresses-explained)
- [Rolling Updates explained](#rolling-updates-explained)
- [Authentication and Authorization](#authentication-and-authorization)
- [Role Based Access Control (RBAC) Resources](#role-based-access-control-rbac-resources)
- [PodSecurityPolicy Activation via RBAC](#podsecuritypolicy-activation-via-rbac)
- [Troubleshooting Kubernetes PodSecurityPolicies](#troubleshooting-kubernetes-podsecuritypolicies)
- [GitOps](#gitops)
  - [High-level overview](#high-level-overview)
  - [Details](#details)

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


# Ingresses explained

Progress of a requests from the ingress controller's service to the actual pod, illustrating the role of the `ingress` resource.

![](https://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/cloudogu/k8s-diagrams/master/diagrams/ingress.puml&fmt=svg)


# Rolling Updates explained

![](https://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/cloudogu/k8s-diagrams/master/diagrams/rolling-update.puml&fmt=svg)


# Authentication and Authorization

Flow from user API server request to response: check authn via identity provider, then authz via RBAC.    

![](https://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/cloudogu/k8s-diagrams/master/diagrams/k8s-auth.puml&fmt=svg)

# Role Based Access Control (RBAC) Resources

A simplified display of resources involved in RBAC and their correlations.

Note that 
* `Permission` is not a k8s resource, but a list of rules inside the (Cluster-)roles that make up a kind of permission.  
  It consits of resources and verbs granted on it. For example: 
  * resources: "secrets"
  * verbs: "get"
* `Subject` can be a serviceAccount, user or group 

![](https://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/cloudogu/k8s-diagrams/master/diagrams/rbac.puml&fmt=svg)


# PodSecurityPolicy Activation via RBAC

Connection from Pod to PSP via RBAC (Role, RoleBinding, ServiceAccount).

![](https://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/cloudogu/k8s-diagrams/master/diagrams/psp-rbac.puml&fmt=svg)


# Troubleshooting Kubernetes PodSecurityPolicies

A diagram to help debugging Kubernetes PodSecurityPolicies.

![](https://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/cloudogu/k8s-diagrams/master/diagrams/troubleshooting-k8s-psps.puml&fmt=svg)

# GitOps

Diagrams describing the general concepts of gitOps and distinguishing it from "ciOps".  

See also our
* [GitOps playground](https://github.com/cloudogu/k8s-gitops-playground/) (to experience argocd and flux hands-on in a local k8s cluster), 
* [GitOps glossary](https://cloudogu.com/en/glossary/gitops/) and
* [offerings for consulting](https://cloudogu.com/en/consulting/).

## High-level overview 

![](https://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/cloudogu/k8s-diagrams/master/diagrams/ciops.puml&fmt=svg)

![](https://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/cloudogu/k8s-diagrams/master/diagrams/gitops-simple.puml&fmt=svg)

## Details 
There are different options when implementing GitOps. Some of them are depicted bellow.

![](https://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/cloudogu/k8s-diagrams/master/diagrams/gitops-with-image.puml&fmt=svg)

CI Server writes image version to GitOps Repo.

---

![](https://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/cloudogu/k8s-diagrams/master/diagrams/gitops-with-auto-update.puml&fmt=svg)

CI Server read-only on GitOps Repo; GitOps Operator writes image version to GitOps Repo.

---

![](https://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/cloudogu/k8s-diagrams/master/diagrams/gitops-with-app-repo.puml&fmt=svg)

Infra as Code stays in app repo, CI Server writes to GitOps repo.

## GitOps Patterns

See [cloudogu/gitops-patterns](https://github.com/cloudogu/gitops-patterns) for more details on GitOps and diagrams.
