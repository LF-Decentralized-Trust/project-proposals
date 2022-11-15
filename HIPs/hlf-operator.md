---
layout: default
title: Hyperledger Fabric Operator Proposal
parent: Hyperledger Improvement Proposals
---

# HIP Identifier
[HIPs/hlf-operator.md](./hlf-operator.md)

# Sponsor(s)

- David Viejo [dviejo@kfs.es](mailto:dviejo@kfs.es)
- Baohua Yang [baohua.yang@oracle.com](mailto:baohua.yang@oracle.com)
- Aditya Joshi [adityaprakashjoshi1@gmail.com](mailto:adityaprakashjoshi1@gmail.com)

# Abstract

HLF Operator is a Kubernetes operator that helps simplify the deployments of Hyperledger Fabric in Kubernetes. It is based on the Hyperledger Fabric Helm charts and provides a Kubernetes native way to deploy and manage Hyperledger Fabric networks.

# Context

There are many ways to deploy Hyperledger Fabric, but most of the alternatives focus on Docker and manually performed deployments, not to mention there's no support to perform operations like:

- Renewal of the certificates
- Upgrades
- Channel management

HLF-operator solves this by introducing the concept of the Kubernetes operator, which is a program that runs within Kubernetes and extends it with functionality specific to HLF that makes managing networks way easier than other alternatives such as Docker-based.

# Dependent Projects

Hyperledger Fabric Operator only requires **Hyperledger Fabric** to run.

# Motivation

When building Hyperledger Fabric networks, there are several barriers to starting using and deploying Hyperledger Fabric:

- How do I deploy a network in Kubernetes?
- How do I manage the certificate authorities/peers/orderers in a production environment?
- How do I renew the certificates?

Several projects try to achieve the same goal, such as:

- https://github.com/KompiTech/hyperledger-fabric-operator
- https://github.com/hyperledger-labs/fabric-operator
- https://github.com/raftAtGit/hl-fabric-operator

# Status

Proposal

# Solution

The solution is to rely on the features that Kubernetes offers in order to:

- Achieve high availability
- Scalability
- Monitor the components

![Chaincode development - Page 2.svg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/68971bab-6c4d-4b0c-8c5e-3234257b4c51/Chaincode_development_-_Page_2.svg)

# Effort and Resources

The hlf-operator code base’s current version is in production with some consortiums. The proposed code base includes the current version (1.8.0) in GoLang.

We have the following companies committed to contributing as of this proposal:

- Kung Fu Software: 2 developers to contribute to hlf-operator

# How To

There's a guide in the documentation of the project that shows how to deploy a sample network in a KinD cluster:

[https://labs.hyperledger.org/hlf-operator/docs/getting-started](https://labs.hyperledger.org/hlf-operator/docs/getting-started)

# References

N/A

# Closure

The goal of Hyperledger Fabric Operator is to speed up the adoption of Hyperledger Fabric and ease the management of HLF networks at scale. The success of the project can be measured by the community on Discord, companies using it and meetups/videos on youtube about this project.