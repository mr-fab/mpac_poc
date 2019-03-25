<div align="center">
    <img src="customer_logo.png" height="100%" width="100%"</img> 
    <img src="aporeto_logo.png" height="50%" width="50%"</img> 
</div>

# MPAC & Aporeto Proof Of Concept (POC)

## Introduction

MPAC is the largest assessment jurisdiction in North America, responsible for accurately assessing and classifying more than five million properties in Ontario in compliance with the Assessment Act and regulations set by the Government of Ontario. MPAC has modernized its operations to leverage the cloud (AWS), Kubernetes and Server-less functions (Lambdas). MPAC approached Aporeto in regards to improving security in its modernized environment.

Aporeto provides Application Segmentation and Zero-Trust Network Segmentation using Crypto-Identity as opposed to network primitives (e.g. IP addresses). Aporeto is able to Authenticate, Authorized (segment) and Account (compliance) communication between workload to workload, user to workload and workload to 3rd party API.

## Purpose

The purpose of this document is to facilitate the execution of a proof of concept (POC). This document is based upon the analysis of the MPAC environment as described by MPAC personal.

## POC Executive Overview

### Workload/Network Segmentation
- Container to Container
- Container to Linux
- Linux to Linux
- Linux to CIDR

### Service (User to Service)
- OAUTH2 / OIDC
- Mutual TLS (Certificate)

### Additional Use Cases
- PROD to DEV and DEV to PROD be denied (regardless of workload type)
- Access to Yum repos will only be permitted to officially sanctioned repos
- Limit access to resources based on group identity

## Base Requirements

Linux or Mac host with the following with bash, curl, and git.
Aporeto Account Credentials
AWS Account

## Execution

Your Sales Engineer will assist if you are executing the POC on your environment.

(incomplete below)

### Setup
```bash
git clone https://github.com/jodydadescott/mpac_poc.git
```

### Validation

| Use Case               | Validation |
| ---------------------- | ---------- |
| Container to Container |            |
| Container to Linux     |            |
