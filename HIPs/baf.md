---
layout: default
title: BAF
parent: Hyperledger Improvement Proposals
---

# HIP Identifer
Blockchain Automation Framework HIP v0.1

# Sponsor(s)
<mark>_**Sponsor(s)** name and contact details including email address_</mark>

- Tracy Kuhrt, Accenture (tracy.a.kuhrt@accenture.com)

# Abstract
<mark>_**Abstract** (less than 50 word) description of the project._</mark>

The Blockchain Automation Framework (BAF) is an accelerator by which developers can consistently deploy production-ready distributed networks across public and private cloud providers.

# Context
<mark>_**Context** if any, what is this project derived from? What if any is it related to?_</mark>

In October, 2019, Accenture [proposed](https://github.com/hyperledger-labs/hyperledger-labs.github.io/pull/102) Blockchain Automation Framework to Hyperledger Labs [1]. It was quickly approved by the Lab stewards.

# Dependent Projects
<mark>_**Dependent Projects** if any, must be listed, and each dependent project\'s maintainers must sign off on the proposal before it is considered by the TSC._</mark>

BAF utilizes:
* [Ansible](https://docs.ansible.com/ansible/latest/index.html) is an automation command line tool that helps IT technicians easily achieve system configuration, software deployment and other complex tasks in orchestration. BAF extensively uses Ansible playbooks along with roles to spin up a DLT/Blockchain network.
* [Kubernetes (K8s)](https://kubernetes.io/) is an open-source system for automating deployment, scaling and maintaining containerized applications. BAF leverages Kubernetes’ various features for deploying a DLT/Blockchain network along with other required services in one or more K8s clusters.
* [Helm](https://helm.sh/) is a package manager for K8s. Helm Charts are configuration files designed for K8s to help define, install and upgrade complex K8s applications. BAF uses Helm Charts for designing and configuring the architecture of each DLT/Blockchain platform for its own network set-up.
* [HashiCorp Vault](https://www.vaultproject.io/) provisions a secure approach to store and gain secret information such as tokens, passwords and certificates. BAF relies on Vaults for managing certificates used in each node of a DLT/Blockchain network during the lifecycle of a deployment, and it is a prerequisite that the Vault is installed and unsealed prior to deployment of a DLT/Blockchain network.
* [GitOps](https://www.weave.works/technologies/gitops/) introduces an approach that can make K8s cluster management easier and also guarantee the latest application delivery is on time. BAF uses Weavework’s Flux for the implementation of GitOps and executes an Ansible role called setup/flux defined in the BAF GitHub repo.

# Motivation
<mark>_**Motivation** for this project, a longer justification of the project may be a couple of hundred words. Why is this project better at solving a problem compared to parallel proposals or implemented projects?_</mark>

Setting up a new DLT/Blockchain network or maintaining an existing DLT/Blockchain network in a production-scale environment is not straightforward. For the existing DLT/Blockchain platforms, each has its own architecture, which means the same way of setting up one DLT/Blockchain network cannot be applied to others.

Therefore, when blockchain developers are asked to use an unfamiliar DLT/Blockchain platform, it requires significant effort for even experienced technicians to properly setup the DLT/Blockchain network. This is especially true in large-scale production projects across heterogeneous corporate environments which require other key aspects such as security and service availability.

Being aware of the potential difficulty and complexity of getting a production-scale DLT/Blockchain network ready, cloud vendors have provisioned their own managed Blockchain services (aka Blockchain as a Service or BaaS) to help alleviate various pain-points during the process. However, limitations can still be identified in these BaaS solutions (e.g., limited network size, locked to all nodes on a single cloud provider, limited choice of DLT/Blockchain platform).

The objective of BAF is to provide a consistent means by which developers can deploy production-ready distributed networks across public and private cloud providers. This enables developers to focus on building business applications, knowing that the framework upon which they are building can be adopted by an enterprise IT production operations organization. BAF is not intended solely to quickly provision _development_ environments which can be done more efficiently with other projects/scripts. Likewise, Blockchain Automation Framework is not intended to replace BaaS offerings in the market, but instead, BAF is an alternative when existing BaaS offerings do not support a consortium’s current set of requirements.

# Status
<mark>_**Status** of the project: See [project lifecycle](https://hyperledger.github.io/tsc/project-lifecycle.html)._</mark>

Proposal

# Solution
<mark>_**Solution** to the problem addressed in the motivation section. Try to make this as detailed as possible._</mark>

# Effort and Resources
<mark>_**Effort and resources** committed (coders and any other resources that are needed) and timeline._</mark>

Since being accepted as a Hyperledger Lab in October 2019, BAF has had 39 total contributors with 32 contributors having more than one commit (based on metrics from the Hyperledger community tools project reports [2]). There have been 27 contributors in the past year and 15 contributors in the past 6 months. The [LF Insights Commit Report through July 18, 2021](https://tinyurl.com/yfckjkeu) [3], 2021 shows that there have been commits from at least 6 separate organizations.

# How To
<mark>_**How to**: How to host and test the project. How to deploy and use. How does one know that it works._</mark>

The Blockchain Automation Framework documentation [4] provides detailed [Operation Guide](https://blockchain-automation-framework.readthedocs.io/en/latest/operationalguide.html) and [Developer Guide](https://blockchain-automation-framework.readthedocs.io/en/latest/developerguide.html). In addition, a [supply chain sample application](https://blockchain-automation-framework.readthedocs.io/en/latest/example/supplychain.html) is provided for the general DLT platforms, and a [Hyperledger Indy reference application](https://blockchain-automation-framework.readthedocs.io/en/latest/example/indy-refapp.html) is provided for Hyperledger Indy. These sample applications allow the user to test their DLT deployments completed via BAF.

# References
<mark>_**References**. See [citation guide](http://www.chicagomanualofstyle.org/tools_citationguide.html)._</mark>

[1] [Blockchain Automation Framework Lab proposal](https://github.com/hyperledger-labs/hyperledger-labs.github.io/pull/102)

[2] [Hyperledger community tools project reports](https://github.com/tkuhrt/hyperledger-community-management-tools/tree/master/project-reports)

[3] [LF Insights Commit Report through July 18, 2021](https://tinyurl.com/yfckjkeu)

[4] [Blockchain Automation Framework Read the Docs](https://blockchain-automation-framework.readthedocs.io/en/latest/index.html)

# Closure
<mark>_**Closure** how do we know that the project succeeded. This has to be measurable if possible. Make references to successor projects if any._</mark>

# FAQ
Additional [FAQs](https://blockchain-automation-framework.readthedocs.io/en/latest/faq.html) can be found in the Blockchain Automation Framework documentation [4].

## What is the Blockchain Automation Framework?
The Blockchain Automation Framework is an automation framework for delivering consistent production ready DLT networks on cloud based infrastructures.

## How is Blockchain Automation Framework different from Blockchain as a Service (BaaS)?
* The Blockchain Automation Framework deployment scripts can be reused across cloud providers like AWS, Azure, GCP, DigitalOcean and OpenShift
* Can deploy networks and smart contracts across different DLT/Blockchain platforms
* Supports heterogeneous deployments in a multi-cloud, multi-owner model where each node is completely owned and managed by separate organizations
* Bring Your Own Infrastructure (BYOI) - You provide GIT, Kubernetes cluster(s), and Hashicorp Vault services provisioned to meet your specific requirements and enterprise standards
* No network size limit
* Specifies only the number of organizations and the number of nodes per organization in a network.yaml file uniquely designed in the Blockchain Automation Framework for a new DLT/Blockchain network set-up and its future maintenance
* Provides a sample supply chain application which runs on multiple DLT/Blockchain platforms that can be used as a reference pattern for how to safely abstract application logic from the underlying DLT/Blockchain platform

## What DLT Platforms are currently supported?
* Corda Open Source and Enterprise
* Hyperledger Fabric
* GoQuorum
* Hyperledger Indy
* Hyperledger Besu

See the [Compatibility Matrix](https://blockchain-automation-framework.readthedocs.io/en/latest/compatibilitymatrix.html) for specific information and versions.
