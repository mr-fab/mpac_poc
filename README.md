# MPAC (Municipal Property Assesment Corporation)
<div align="left">
    <img src="customer_logo.png" height="50%" width="50%"</img> 
    <img src="aporeto_logo.png" height="13%" width="13%"</img> 
</div>

# Aporeto Proof Of Concept (POC)

## Introduction

MPAC is the largest assessment jurisdiction in North America, responsible for accurately assessing and classifying more than five million properties in Ontario in compliance with the Assessment Act and regulations set by the Government of Ontario. MPAC has modernized its operations to leverage the cloud (AWS), Kubernetes and Server-less functions (Lambdas). MPAC approached Aporeto in regards to improving security in its modernized environment.

Aporeto provides Application Segmentation and Zero-Trust Network Segmentation using Crypto-Identity as opposed to network primitives (e.g. IP addresses). Aporeto is able to Authenticate, Authorized (segment) and Account (compliance) communication between workload to workload, user to workload and workload to 3rd party API.

## Purpose

The purpose of this document is to facilitate the execution of a proof of concept (POC). This document is based upon the analysis of the MPAC environment as described by MPAC personal.

## Major Use Cases

- Network Segmentation (Linux & Windows)
- Micro Segmentation (Kubernetes, Docker, Mesos, etc)
- Ingress Service/API AAA via OAUTH2/OIDC or Certificate (Mutual TLS)
- Egress Service/API AAA via OAUTH2/OIDC or Certificate (Mutual TLS)
- Bastion Linux Host (UID PAM)

### Customer Specific Use Cases

MPAC has defined the following uses cases that shall be included in this POC.
- The yum utility will only be able to access local repos
- Workloads marked prod will only talk to other workloads marked prod (Prod/Dev Segmentation)

## Base Requirements

- Linux or Mac host with the following with bash, curl, and git.
- Aporeto Account Credentials

## Execution

Your Sales Engineer will assist if you are executing the POC on your environment.

(incomplete below)

### Installation and Setup (General Overview)

Your Aporeto SE will assist you with this.

1. In your cloud or datacenter enviroment
- Install apoctl on your workstation 
- Provision a Kubernetes Clusters named kube1 with two or more nodes
- Provision two Linux VM's named linux1 and linux2

1. Using the Aporeto apoctl utility or UI create the following namespaces
- poc in account /mpac
- linux and kube in /mpac/poc
- kube1 in /mpac/poc/kube

1. Using the Aporeto apoctl utility or UI create the following External Networks in /mpac/poc
- localrepo with CIDR (Your local repo), protocol TCP, any ports and the tag localrepo=true
- internet with CIDR 0.0.0.0/0, protocol any, any ports and tag internet=true
- dns with CIDR 0.0.0.0/0, protocol UDP, port 53 and tag dns=true

1. Using the Aporeto apoctl utility or UI create the following Network Policies in /mpac/poc
- permit $identity=processingunit to dns=true
- permit Linux group nginx to nginx=true

1. Using the Aporeto apoctl utility or UI create the following Network Policies in /mpac/poc/kube/kube1
- permit role=frontend to role=backend
- permit internet=true to role=frontend

1. On the Linux VM's 
- install the Aporeto Enforcer and Register with the Orchestrator
- add line 'session required /lib/x86_64-linux-gnu/security/pam_trireme.so' to /etc/pam.d
- configure and start nginx as wrapped process with label nginx=true

1. On the Kubernetes clusters
- use helm charts to install Aporeto
- deploy application beer in namespace beer1 and beer2
- expose via service role=frontend


### Validation

Your SE will now work with you to demonstrate the following.

| Use Case                                | Validation |
| ------------------------------------------------------------------- | ---------- |
| Network Segmentation                                                |            |
| Ingress Service/API AAA via OAUTH2/OIDC                             |            |
| Ingress Service/API AAA via Certificate                             |            |
| Bastion Linux Host (UID PAM)                                        |            |
| Yum utility will only be able to access local repos                 |            |
| Workloads marked prod will only talk to other workloads marked prod |            |


