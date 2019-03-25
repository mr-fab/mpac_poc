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

- Network Segmentation / Micro Segmentation
- Service/API AAA using OAUTH2/OIDC or Certificate
- Bastion Linux Host (UID PAM)

## Customer Specific Use Cases

- The yum utility will only be able to access local repos
- Workloads marked prod will only talk to other workloads marked prod (Prod/Dev Segmentation)

## Base Requirements

- Linux or Mac host with the following with bash, curl, and git.
- Aporeto Account Credentials

## Installation and Setup

### Your Aporeto SE will work with you to create specific instructions on how to deploy the POC in your desired environment. This is a general overview of the steps that will be necessary. Ideally the setup will be scripted by you SE before the scheduled POC.

### In your cloud or datacenter enviroment

- Install apoctl on your workstation 
- Provision a Kubernetes Clusters named kube1 with two or more nodes
- Provision two Linux VM's named linux1 and linux2

### Using your preferred OIDC provider

- create a web application and record id and key
- add users such as bob and alice
- assign users group membership
- make sure group is part of default scope

### Using the Aporeto apoctl utility or UI

- create namespaces
- create External Networks
- create network policies
- create enforcer profiles
- create service policies

### On the Linux VM's

- install the Aporeto Enforcer and Register with the Orchestrator
- configure pam.d
- configure wrapped services

### On the Kubernetes clusters

- use helm charts to install Aporeto
- deploy test applications

## Validation

### Each use case will be validated. Once validated both MPAC and Aporeto can initial the validation.

| Use Case                                                            | MPAC Agent | Aporeto Agent |
| ------------------------------------------------------------------- | ---------- | ------------- |
| Network Segmentation                                                |            |               |
| Ingress Service/API AAA via OAUTH2/OIDC                             |            |               |
| Ingress Service/API AAA via Certificate                             |            |               |
| Bastion Linux Host (UID PAM)                                        |            |               |
| Yum utility will only be able to access local repos                 |            |               |
| Workloads marked prod will only talk to other workloads marked prod |            |               |


