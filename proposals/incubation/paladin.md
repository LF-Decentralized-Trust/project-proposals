---
layout: default
title: Paladin
parent: Incubation
grand_parent: Project Proposals
---

# LFDT Paladin Incubating Project

# Sponsor(s)

 - Steve Cerveny (steve.cerveny@kaleido.io)
 - Peter Broadhurst (peter.broadhurst@kaleido.io)  
 - Jim Zhang (jim.zhang@kaleido.io)
 - Andrew Richardson (andrew.richardson@kaleido.io)
 - Matthew Whitehead (matthew.whitehead@kaleido.io)
 - Enrique Lacal (enrique.lacal@kaleido.io)
 - Sanjam Garg, Associate Professor in Cryptography at UC Berkeley (sanjamg@berkeley.edu) 
 - Guru Vamsi Policharla, PhD Candidate in Cryptography at UC Berkeley (guruvamsi.policharla@gmail.com)
 - Matthew Gregoire, PhD Candidate in Cryptography at UNC Chapel Hill (mattyg@cs.unc.edu)
 - Arka Rai Choudhuri, Cryptography Research Scientist at Nexus (arkarai.choudhuri@gmail.com)
 - Keewoo Lee, Cryptography Researcher at UC Berkeley (keewoole@gmail.com)

# Abstract

Paladin is a modular runtime for programmable privacy on EVM.

It provides the common wallet/vault functions that are needed to interact with all forms of privacy preserving smart contracts. It also provides a model for atomic programmability across these privacy preserving smart contracts, harnessing the power of the underlying EVM shared ledger.

There are two primary types of privacy preserving smart contract accounted for in the design:

1. Tokens.
   Value/data that can be proved as owned across the whole chain, regardless of the transaction within which it originated.

2. Privacy groups.
   Private EVM smart contracts executed between a set of parties, where the outcome is irrefutable via proof on the chain, but the data is private.

Atomic transactions across these types can be performed including DvP and PvP, with private agreement logic independent from the tokens.

Hardened reference implementations are provided out of the box as part of the Paladin project, which are focussed on real world enterprise use cases.

  - Zeto: Zero-knowledge Proof (ZKP) tokens, providing implementations of enterprise features such as allow-listing and post-quantum lattice based encryption in CIRCOM.
  - Noto: Notarized tokens, using issuer co-signatures with EIP-712 to provide privacy to all ecosystem participants. Notary logic can be coded in private EVM.
  - Pente: Support for any EVM smart contract via lightweight ephemeral execution of the Besu EVM, and full proof of execution on-chain.
    - Successor of the Tessera project

All of these reference implementations use standard EVM smart contracts as the source of truth for the finalization of the transaction, and verification of the private logic. Zero modifications are required to the underlying blockchain, and any permissioned or public EVM can be used.

A strong design principle of the project is that existing privacy preserving tokens should be able to become compatible with Paladin wallet/vault functions and programmability with limited changes. Work towards a formal EIP proposal to help with this is underway.

The app-layer components plugin via a modular and efficient gRPC interface, proven with multiple embedded runtimes (Java, Go, WebAssembly). This provides extensibility of the system across cryptography systems, including new ZKP toolkits and circuits, as well as Fully Homomorphic Encryption (FHE) and other cryptography approaches.


It was launched as an LFDT Lab in 2024 and has been in active development ever since, with 11 releases in the past 12 months. Interest in Paladin’s EVM-based privacy model has been extremely high, with demos and proof-of-concepts successfully run with numerous international financial institutions.

The project is moving towards a v1.0 release in the coming months, a strong indicator of its maturity and stability and a measure of the confidence the contributors have in the technology.

# Context
Paladin and Zeto are currently independent LFDT Labs. Paladin provides a pluggable framework for different privacy domain models. Zeto provides a zero-knowledge-proof based token implementation and implements Paladin’s domain plugin interface, making it available as one of Paladin’s out-of-the-box privacy domains.

While Zeto has standalone use-cases outside of Paladin, its development has been done in parallel with Paladin and it is primarily used as a privacy domain for Paladin. As such this proposal includes bringing Paladin and Zeto into a single LFDT incubating project, albeit with the intention to keep the codebases in their own LFDT repositories.

Bringing the two labs together will offer cohesion for those users who only use Zeto through Paladin, and will allow more valuable dialogue on the two technologies, for example in a single LFDT community call.

Additional resources that provide more background on Paladin:

 - Kaleido blog article: https://www.kaleido.io/resources/paladin-release-webinar
 - Intro to Paladin webinar: https://www.youtube.com/watch?v=Wy2QN6VlD5w
 - Paladin deep-dive webinar: https://www.youtube.com/watch?v=AFcai4dJDyg 

# Dependent Projects

None

# Motivation
The Ethereum Virtual Machine (EVM) powers the majority of global blockchain projects, making it the 'de facto' runtime environment for both enterprise and permissionless networks.
However, there are requirements for enterprise use cases that are not met by the core standard of EVM. The Paladin project brings latest generation of innovation in solving these requirements in the EVM ecosystem, and provides a comprehensive enterprise grade Apache 2.0 open source stack to deliver them.

 - Anonymity for all parties involved in transactions
 - Confidential transaction details
 - Transaction history masking to prevent tracking
 - Selective data sharing
 - Confidential business logic
 - Privacy preserving smart contracts
 - Private token and asset management
 - Atomic transactions across privacy domains

# Status

Incubating project

# Solution
This project hosts the entire code base for the Paladin and Zeto implementations, which contains the following functionalities:
 - Privacy preserving token smart contract samples
   - using Zero Knowledge Proofs, like zeto
   - using the Notary certificates (included in this project)
   - using the multi-party flows with EVM private smart contracts (included in this project). This provides function similar to that provided by the Tessera project with additional interoperability and other enhancements
 - Sidecar runtime next to a Besu node
 - Secure channels of communication to other Paladins over which it can selectively disclose private data
 - High performance transaction manager that coordinates transaction assembly, submission and confirmation across Paladin runtimes
 - Enterprise grade key management integration
 - Development, configuration, and deployment pipeline for privacy preserving smart contracts

Paladin supports token implementations that obey these basic principles:
 - use the EVM base ledger as the source of truth for order and finality of transactions
 - transactions from different tokens involved in a higher level flow like DvP or PvP are atomically interoperable via the base EVM ledger
 - store states in the EVM base ledger in a securely masked format preserving:
   - Confidentiality: the data is protected via cryptography, and selectively disclosed on a need to know basis
   - Anonymity: the parties involved in a transaction, or set of transactions, cannot be determined without access to the confidential data

# Effort and Resources

Paladin and Zeto are technically advanced projects with a multitude of capabilities. Paladin requires complex Ethereum transaction processing and indexing features, including the ability to manage gas fees on public chains and accommodate chain reorgs on chains that do not exhibit instant finality. It uses primarily Golang for the majority of the project’s function, but incorporates integration with existing Besu libraries implemented in Java to offer private EVM state management for privacy groups. Zeto uses the Circom libraries to implement zero knowledge circuits and requires a reasonable working knowledge of zero knowledge techniques.

Between them the two projects have 8 maintainers who have actively been contributing in the past 12 months. As outlined below in the incubation entry criteria, many of the active maintainers have a long history of contributing to graduated LFDT projects.

# How To
The Paladin documentation provides detailed “Getting started” guides  (see https://lf-decentralized-trust-labs.github.io/paladin/head/getting-started/installation/) and tutorials (see https://lf-decentralized-trust-labs.github.io/paladin/head/tutorials/) to help both users and contributors get going with the project.

# References
N/A

# Closure
The project’s aim is to become the industry standard framework for managing private and public transactions with pluggable privacy domains and out-of-the-box privacy solutions suitable for production deployments. The intention is to have a growing number of real-world deployments of Paladin over the coming 12-24 months as the codebase matures and the community adoption grows.

By way of a comparison, LFDT FireFly is the leading Web2 middleware project for blockchain application runtimes and continues to have a healthy maintainer base, regular releases, and new plugin contributions from third parties. Paladin aims to have a similar degree of contributor diversity, release cadence, and new feature development. Ultimately Paladin aims to meet the requirements to become a graduated LFDT project.

# Incubation entry criteria

Below is the LFDT incubation entry criteria and demonstrates how Paladin meets those criteria.

## Maintainer community
There are currently 11 maintainers of Paladin and Zeto. Currently they are all from the Kaleido organisation but there has been active involvement with Zeto from a number of researchers from UC Berkeley and UNC Chapel Hill who have contributed both designs and code (some are listed in the sponsor list).

In the past 12 months there have been 8 active contributors.

The lead maintainers are all familiar with open source and more specifically LFDT projects. These include:

 - @peterbroadhurst (active maintainer of LFDT Hyperledger FireFly)
 - @jimthematrix (active maintainer of LFDT FireFly and previous LFDT TAC member)
 - @awrichar (active maintainer of LFDT FireFly)
 - @matthew1001 (active maintainer of LFDT FireFly, LFDT Besu, and a member of the LFDT TAC)

Our collective experience with LFDT projects puts us in an excellent position to meet the LFDT project requirements such as annual and quarterly reports.

## Community calls

As part of the proposal we will be setting up monthly community calls to provide a place to discuss development progress, roadmaps, and upcoming releases.

## Discord communication

There are currently 3 discord channels across the the two labs:

 - paladin
 - paladin-maintainers
 - zeto

As part of graduating we propose to move to the following discord channel structure:

 - paladin
 - paladin-maintainers
 - paladin-release
 - paladin-zeto
 - paladin-noto
 - paladin-pente

The last two - paladin-noto and paladin-pente - will be used for discussion specific to the other two reference domains - Noto and Pente - and are natural peers of paladin-zeto which will replace the current zeto lab channel.

## Documentation

This has been a lot of effort by the community to mature the documentation ahead of a v1.0 release. The current documentation can be viewed here 

 - https://lf-decentralized-trust-labs.github.io/paladin/head/
 - https://hyperledger-labs.github.io/zeto/latest/

Some of the areas the community has focused on include troubleshooting, FAQs, and other topics that are important for new users of the project.

The documentation provides extensive examples and getting started material, for both developers and users. There is a complete reference section for the JSON/RPC APIs and comprehensive architecture material explaining the Paladin framework and how the codebase is structured.

## Test coverage

Test coverage is not currently reported in the project homepage but is currently tracking in the mid-80% and active development branches show >90%. The aim for the project is to reach 100% in the 12 months after graduating to incubating.

## Roadmap

The project maintainers endeavour to follow LFDT guidelines on the use of public boards for roadmap and release planning. The current board can be found here https://github.com/orgs/LF-Decentralized-Trust-labs/projects/2/views/1?template_dialog_tab=all&layout_template=table and outlines the items being tracked towards the v1.0 release.

Following the v1.0 release a focus of the community will be discussing the roadmap for the next 12 months.

## CI/CD Pipeline & Release Process

 - Branch protections are enabled requiring a minimum of 1 maintainer approval before merging
 - PRs must pass unit tests, component tests, and integration tests before merging
 - Releases are automated through GHAs
 - The release pipeline automatically performs version-to-version upgrade testing
 - Release notes are tracked in the Github releases
 - Scorecard will shortly be added to the repo as will LFX insights

## Other incubation criteria

 - The labs are already open sourced under Apache 2 license
 - DCO sign off is enabled for both repositories


