![Header](https://github.com/jodydadescott/mpac_poc/blob/master/header.png?raw=true)

# MPAC & Aporeto Proof Of Concept (POC)

## Introduction

MPAC is the largest assessment jurisdiction in North America, responsible for accurately assessing and classifying more than five million properties in Ontario in compliance with the Assessment Act and regulations set by the Government of Ontario. MPAC has modernized its operations to leverage the cloud (AWS), Kubernetes and Server-less functions (Lambdas). MPAC approached Aporeto in regards to improving security in its modernized environment.

Aporeto provides Application Segmentation and Zero-Trust Network Segmentation using Crypto-Identity as opposed to network primitives (e.g. IP addresses). Aporeto is able to Authenticate, Authorized (segment) and Account (compliance) communication between workload to workload, user to workload and workload to 3rd party API.

## Purpose

The purpose of this document is to facilitate the execution of a proof of concept (POC). This document is based upon the analysis of the MPAC environment as described by MPAC personal.

## POC Validation

| Item     | Validation |
| ---      | ---  |
| Container to Container |      |

### Segmentation
- Container to Container
- Container to Linux
- Linux to Linux
- PROD to DEV will be denied
- DEV to PROD will be denied
- Service (User to Service)
- OAUTH2 / OIDC
- Mutual TLS (Certificate)

### Linux
- Users’s (including root) will be permitted to access local YUM repo’s only.
- Users will not be permitted to access internet
- Users of group “redwood” will be permitted to access a resource labeled “modern”
- Users of group “paloalto” will be denied access to rescue labeled “modern”

## Base Requirements

Linux or Mac host with the following with bash, curl, and git.
Aporeto Account Credentials
AWS Account

## Execution

Your Sales Engineer will assist if you are executing the POC on your environment.
```bash
git clone https://github.com/jodydadescott/mpac_poc.git
```
