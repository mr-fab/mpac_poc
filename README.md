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
- Two Kubernetes clusters
- Three Linux VM Instances (AWS EC2)

## Execution

Your Sales Engineer will assist if you are executing the POC on your environment.

(incomplete below)

### Installation and Setup

1. Create the namespace /mpac/poc [(https://junon.console.aporeto.com/docs/main/concepts/namespaces/)](https://junon.console.aporeto.com/docs/main/concepts/namespaces/)

1. Install apoctl on your workstation [(https://junon.console.aporeto.com/docs/main/registration/logging-in-with-apoctl/)](https://junon.console.aporeto.com/docs/main/registration/logging-in-with-apoctl/)

1. Deploy Aporeto on both Kubernetes Cluster [(https://junon.console.aporeto.com/docs/main/installation/install-on-kubernetes/)](https://junon.console.aporeto.com/docs/main/installation/install-on-kubernetes/)

1. Install Aporeto Enforcer on Linux [(https://junon.console.aporeto.com/docs/main/installation/install-on-linux/)](https://junon.console.aporeto.com/docs/main/installation/install-on-linux/)

1. On Linux install the PAM module (Your SE will assist you)

1. Deploy application on both Kubernetes cluster and label application app=appx & prod=true

1. Deploy (another) application on both Kubernetes cluster and label application app=appy & prod=true

1. Deploy (another) application on both Kubernetes cluster and label application app=appy & dev=true

1. Install a policy that permits app=appx to communicate with app=appx


### Validation

| Use Case               | Validation |
| ---------------------- | ---------- |
| Container to Container |            |
| Container to Linux     |            |
