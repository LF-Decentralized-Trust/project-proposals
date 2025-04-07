---
layout: default
title: CREDEBL
parent: Incubation
grand_parent: Project Proposals
---

# CREDEBL Project Proposal

## CREDEBL
**CREDEBL** is a Decentralized Identity & Digital Credentialing Platform. It is recognized as a Digital Public Good (DPG) by the Digital Public Good Alliance (DPGA).

# Sponsor(s)
* _Ajay Jadhav (ajay@ayanworks.com_)
* _Kalyan Kulkarni (kalyan@ayanworks.com)_
* _Deepak Ghadge (deepak.ghadge@ayanworks.com)_
* _Ankita Patidar (ankita.patidar@ayanworks.com)_
* _Amit Padmani (amit.padmani@ayanworks.com)_
* _Prasad Kalamkar (prasad.kalamkar@ayanworks.com)_

# Abstract
CREDEBL is an industry-leading Verifiable Credential & Decentralised Identity management platform which helps in building scalable, secure and user-centric SSI solutions. The multi-tenant platform offers straightforward interactions, enabling rapid configuration & deployment of any DID/VC solution.

# Context
CREDEBL Platform is conceptualized & built by AYANWORKS. After building & delivering several decentralized identity systems, AYANWORKS team felt a need of a system which acts as a re-usable core SSI platform and support in building multiple sector-specific use cases of Decentralized Identity & Verifiable Credentials implementation.

Hence, CREDEBL is built with support for multi-tenancy while being agnostic to underlying ledgers/VDRs, DID methods, and Verifiable Credential formats.

# Dependent Projects
- Credo (Current)
- ACA-Py (Soon, for cloud wallets)

# Motivation
The motivation behind CREDEBL is to provide a robust SSI Core for population-scale implementations such as National ID, Digital Travel Credentials, Academic Credentials, etc., and to help increase the adoption of user-centric, Decentralized ID technology.

# Status
- Incubation

We acknowledge that all projects entering LF Decentralized Trust start with Incubation status.

CREDEBL is a production-ready project with a robust 1.0 release with multiple production deployments at national scale.

Our team has reviewed the Project Incubation Exit Criteria and believes we fulfill all the requirements
for "Graduated" status, with the exception of being on-boarded onto Linux Foundation’s tools and build processes.

We are prepared to complete these steps promptly following an approval vote by the Technical Advisory Council (TAC).

Once these final steps are completed, we believe the project will be ready for "Graduated" status and will apply for
this designation immediately.

We anticipate that this designation process will proceed swiftly if the TAC concurs that all criteria have been met.


# Solution
The CREDEBL Codebase is currently hosted as a separate Github Org at https://github.com/credebl

### CREDEBL PLATFORM
Platform provides a set of scalable services to manage decentralized identity and verifiable credentials (VC) system. It enables developers to build Self-Sovereign Identity (SSI) solutions that provide enhanced privacy and security. It is designed for scalability to support population-scale SSI implementations. 

It provides tools for digital credential management and verification, allowing organizations to easily issue and manage credentials with ease. It is built on a micro-services architecture to support large-scale enterprise applications.

Platform supports multiple ledger options (like Indy and Polygon) and also ledger-less credential issuance using methods like did:web, did:key and did:peer.

### CREDEBL STUDIO
Studio is web front-end for the entire Platform, built using Astro, React, Flowbite, and Tailwind CSS, allowing administrators & users to easily access & manage all the Platform features using a simple web interface.

### ARIES AGENT
In the context of decentralized identity systems, an agent generally refers to a software component or service that facilitates peer-to-peer interactions and data exchange operations between various entities in the system.

Agents leverage the Aries protocol implementations built into Credo & Aca-Py.

There are two types of agents that organizations can use, each serving different needs based on the deployment model and use case: Shared Agents and Dedicated Agents.

A shared agent refers to an agent that is used by multiple entities or tenants, rather than being dedicated to a single entity. If the tenancy is set to true, it typically means that the system or agent supports multi-tenancy, or if the tenancy is set to false, it means that the agent does not support the multi-tenancy.

### Mobile SDK
Built on Credo, the Mobile Wallet SDK is a React-Native SDK wrapper that helps mobile developers to easily build SSI features in the existing mobile apps or a new one. It enables interoperability and seamless connectivity for secure data exchange.

# Architecture
Following diagram depicts the overall system architecture of CREDEBL.

All the listed components in this diagram are proposed to be in the scope of contribution under LF Decentralized Trust.

![CREDEBL Architecture](../images/credebl/CREDEBL_OSS_Architecture.png "CREDEBL Architecture")

# Relation with existing identity projects
CREDEBL closely relates to the existing Hyperledger Identus project, and shares many concepts such as use of Aries RFCs, DIF & TrustOverIP specifications.

CREDEBL is focused on population-scale use cases such as National Digital ID, Digital Travel Credentials, mDL, Academic Credentials, etc., while trying to remain flexible & agnostic to ledgers & credential formats.

# Effort and Resources

Following are the current maintainers on the project mainly from AYANWORKS team, and will continue to be under LFDT as well.

With the contribution to LFDT, our goal is to increase organizational diversity of maintainers.

* Ajay Jadhav (https://github.com/ajile-in)
* Prasad Kalamkar (https://github.com/prasadgkalamkar)
* Amit Padmani (https://github.com/amitpadmani-awts)
* Ankita Patidar (https://github.com/ankita-p17)
* Sai Ranjit (https://github.com/sairanjit)
* Tipu Singh (https://github.com/tipusinghaw)
* Krishna Waske (https://github.com/GHkrishna)
* Sheetal Shevalkar (https://github.com/Sheetal-ayanworks)
* Sahil Kamble (https://github.com/KambleSahil3)

# How To
The [CREDEBL Documentation](https://docs.credebl.id) is a good starting point to understand basics, and go through the instructions for setting up the CREDEBL instance in a local or cloud environment.

# Discord
Currently, there is a dedicated Discord Server available for CREDEBL at https://discord.gg/w4hnQT7NJG, which we suggest to move to LFDT's Discord.

# License
All the codebase of CREDEBL is licensed under **Apache 2.0**

# References
* Codebase: https://github.com/credebl
* Docs: https://docs.credebl.id
* CREDEBL Website: https://credebl.id
* DPG Status: https://app.digitalpublicgoods.net/a/11779
* A similar project from Linux Foundation called Janssen Project is also recognized as a DPG - https://app.digitalpublicgoods.net/a/11269

# Closure

Although, we have not set specific metrics, the success criteria of the project measure against the following goals:

- Governance: Achieve effective governance to guide the project's direction, make decisions, and resolve conflicts, contributing to the project's stability and growth.
  
- Community: Foster a community that contributes code, reports bugs, requests features, contributes to documentation, and participates in forums related to project development.

- Sustainability: Attain a diverse contributor base to reduce dependence on a single contributor or company.

- Active Development: Maintain a regular release schedule and commit to addressing bug fixes and new features.

- Adoption: Measure the number of projects developed on top of CREDEBL.

- Best Practices: Adopt & measure the open source development best practices of Linux Foundation Decentralized Trust, such as SBOM, Code Security, etc.