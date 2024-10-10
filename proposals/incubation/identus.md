---
layout: default
title: Identus
parent: Incubation
grand_parent: Project Proposals
---

# HIP Identifier
Hyperledger Identus v1.0 (was Open Enterprise Agent lab)

# Sponsor(s)
- Jon Bauer - jon@goodfuture.io
- Lance Byrd - lance.byrd@rootsid.com
- Roberto Carvajal - roberto@goodfuture.io  
- Esteban Garcia - esteban.garcia@iohk.io
- Mix Irving - mix@protozoa.nz  
- Rodolfo Miranda - rodolfo.miranda@rootsid.com
- Darrell O’Donnell - darrell.odonnell@continuumloop.com
- Javier Ribo - javier.ribo@iohk.io
- Björn Sandmann - sandmann@codedata.solutions
- Yurii Shynbuiev - yurii.shynbuiev@iohk.io
- Lohan Spies - lohan.spies@iohk.io
- Ben Tairea - ben@ahau.io
- Benjamin Voiturier - benjamin.voiturier@iohk.io
- Marcus Ubani - marcus@larissa.health  

# Abstract
Identus provides components to develop decentralized identity solutions that adhere to widely recognized self-sovereign identity (SSI) standards. 

# Context
Recognizing the limitations of centralized identity systems, [IOG](https://iohk.io/)—the company behind the development of the Cardano Blockchain—has dedicated efforts towards developing an SSI product that emphasizes decentralization and user empowerment. This project is known as Atala PRISM.

At its inception, Atala PRISM drew inspiration from the [Sidetree protocol](https://github.com/decentralized-identity/sidetree), which allowed the management of [decentralized identifiers (DIDs)](https://w3c.github.io/did-core/). In addition to DID management, Atala PRISM allowed the issuance of [verifiable credentials (VCs)](https://www.w3.org/TR/vc-data-model/). To achieve this, the Atala PRISM team implemented a second-layer protocol on the Cardano blockchain. The key idea was to use the blockchain's security and immutability to enable identity solutions that operate independently of centralized controls.

Feedback from early users of Atala PRISM raised concerns about intellectual property considerations and the possibility of vendor lock, which could hinder collaborative efforts. Additionally, it became clear that the project had to align with emerging standards and specifications in the decentralized identity domain. Another challenge faced was establishing effective communication between ecosystem agents.

Considering these insights, the Atala PRISM team developed a second project iteration. The new version focuses on compliance with W3C recommendations, supports some [Hyperledger Aries RFCs](https://github.com/hyperledger/aries-rfcs/blob/main/index.md), and adopted [DIDComm v2](https://identity.foundation/didcomm-messaging/spec/v2.0/). The project has evolved significantly and is on the path to support AnonCreds, SD+JWT, and OID4VC. What started as an API-driven Cloud Agent became extended by Wallet SDKs with a comprehensive support of languages, a standalone DIDComm v2 compatible Mediator, and a generic Cryptographic library providing a flexible foundation for decentralized identity solutions.

As part of the project evolution, in 2023, IOG decided to open-source Atala PRISM's codebase and contribute its main component — the Cloud Agent (previously known as the Open Enterprise Agent) — to [Hyperledger Labs](https://wiki.hyperledger.org/display/labs). In the open-source space, we've engaged with the community, opened communication channels, and hosted regular community meetings, leading to improvements based on user feedback. Our efforts have encouraged the development of several third-party PoCs and nurtured a growing community. While the project still has a few references to its roots as an internal project from IOG, it is already mostly decoupled, and the development is happening not only by developers from IOG but also by the community.

We will increase our involvement in Hyperledger by adding additional decentralized identity components to the Identus project, enabling us to reach a wider audience and promote technology adoption.

## Relationship to Hyperledger Aries

Identus builds upon the foundational protocols defined in Hyperledger Aries RFCs, which provide secure communication and verifiable credential exchange standards.  While adhering to these Aries standards, Identus offers a distinct implementation using the Scala programming language, which aligns with other Aries-inspired frameworks such as AcaPy (Python) and AFJ (JavaScript).

A key difference lies in Identus' adoption of DIDComm v2, the latest version of the DIDComm messaging protocol, while existing Aries implementations currently use DIDComm v1. It's important to note that this difference alone, and potentially other unidentified differences in the implementation, make Aries and Identus not interoperable in the current state. We believe having components under the Aries umbrella that are incompatible with the rest of the Aries code base would be confusing. Meanwhile, the Identus set of components works together cohesively. Therefore, it would be more logical to consider Identus as a standalone project.

## Collaboration Opportunities

Identus and Aries hold the potential for valuable collaboration. Identus' experience with DIDComm v2 could aid in its adoption within Aries. Additionally, exploring the integration of Aries Askar as a secure storage and key management solution for Identus could prove beneficial.

## Choosing Between Identus and Aries

When selecting a framework for decentralized identity solutions, consider the following factors:
- Programming Language Preference: Although writing business logic can be done in any language, if your development team favors Scala (JVM) based backends, Identus offers a natural fit. On the other hand, Aries provides implementations in Python and JavaScript, among others.
- DIDComm Version: If your project's requirements necessitate DIDComm v2, Identus would be the more suitable choice.
- Community: To determine whether Identus and Aries suit your project, you must evaluate the community composition. Although Identus aims to be VDR agnostic, it has a more substantial presence within the Cardano communities due to its association with IOG, which offers better synergies for use cases that target the Cardano ecosystem.

# Dependent Projects
none

# Motivation
Identus addresses the challenges of building decentralized identity solutions. Traditionally, newcomers to the decentralized identity space face steep learning curves. We aim to ease the task by providing comprehensive components, detailed documentation, and adherence to well-known domain standards. Our technology-agnostic approach reduces friction, while our focus on abstracting complexities of SSI technology allows solution builders to concentrate on innovative use cases across Web2 and Web3 landscapes. Identus strives to provide flexibility by supporting multiple credential formats and verifiable credential exchange options.

Most importantly, we've ensured cohesion by conveniently implementing the most sought-after decentralized identity functionalities in one place, making our offering a solution for those looking to streamline the development of decentralized identity systems.

# Status

Incubation

Today, the Cloud Agent is at Hyperledger as the [Open Enterprise Agent - Lab](https://github.com/hyperledger-labs/open-enterprise-agent).
The goal is to contribute more components of Atala PRISM under the Identus Project. The other components we want to make part of Identus are:
- [DIDcomm v2 Mediator](https://github.com/input-output-hk/atala-prism-mediator )
- [DIDcomm v2 Mediator - Test Suite](https://github.com/input-output-hk/didcomm-v2-mediator-test-suite)
- [Apollo Cryptographic library](https://github.com/input-output-hk/atala-prism-apollo/)
- Wallet SDKs
  - [TS Implementation](https://github.com/input-output-hk/atala-prism-wallet-sdk-ts)
  - [Swift Implementation](https://github.com/input-output-hk/atala-prism-wallet-sdk-swift)
  - [KMM Implementation](https://github.com/input-output-hk/atala-prism-wallet-sdk-kmm)

Beyond the components presented here, the proposal extends to other features we plan to develop.

# Solution

The Identus project will consist of the following components:

Cloud Agent: a cloud-based, W3C/Aries standard-compliant agent written in Scala. Key features include Rest API, DIDComm V2 support, W3C-compliant DID methods, credential management (JWT and AnonCreds), HTTP events notification, Cardano ledger integration, secrets management via Hashicorp Vault, and multi-tenancy support.

- Supported Aries RFC’s:
  - [0023-did-exchange](https://github.com/hyperledger/aries-rfcs/tree/main/features/0023-did-exchange)
  - [0434-out-of-band-protocol](https://github.com/hyperledger/aries-rfcs/blob/main/features/0434-outofband/README.md)
  - [0453-issue-credential-protocol](https://github.com/hyperledger/aries-rfcs/tree/main/features/0453-issue-credential-v2)
  - [0454-present-proof-protocol](https://github.com/hyperledger/aries-rfcs/tree/main/features/0454-present-proof-v2)
- DIDComm Protocols Supported:
  - [Mediator Coordinator](https://didcomm.org/mediator-coordination/2.0/)
  - [DIDComm V2 Messaging](https://identity.foundation/didcomm-messaging/spec)
  - [DIDComm V2 Issue Credential](https://github.com/decentralized-identity/waci-didcomm/tree/main/issue_credential)
  - [DIDComm V2 Present Proof](https://github.com/decentralized-identity/waci-didcomm/blob/main/present_proof/present-proof-v3.md)
  - [DIDComm V2 Report Problem](https://identity.foundation/didcomm-messaging/spec/#problem-reports)
  - [DIDComm V2 Routing Protocol](https://identity.foundation/didcomm-messaging/spec/#routing-protocol-20)
- Credential Types Supported:
  - [JWT-VC](https://identity.foundation/jwt-vc-presentation-profile/)
  - SD-JWT-VC
  - [Anoncreds](https://www.hyperledger.org/projects/anoncreds)  
- DID Methods Supported:
  - [did:prism](https://github.com/input-output-hk/prism-did-method-spec/blob/main/w3c-spec/PRISM-method.md)
  - [did:peer](https://identity.foundation/peer-did-method-spec/index.html)

Mediator: is a cloud-based service designed for secure, private, decentralized communication using DIDComm v2. It supports protocols such as BasicMessage 2.0 and MediatorCoordination 2.0 to facilitate logical connections, message encryption, and routing. It is handy for scenarios where edge entities are only occasionally online.

Apollo: is a cryptographic library that enables cryptographic functionality on multiple platforms. It is built with Kotlin Multiplatform and supports various targets such as JS, iOS, Android, and JVM. The library design is to be a collection of cryptographic methods utilized across Identus components.

Wallet SDKs: Identus offers three SDKs intended to facilitate the development of wallet applications across different platforms and programming languages. Each SDK shares core functionalities such as cryptographic operations, management of DIDs, handling verifiable credentials, and supporting DIDComm V2 messaging for secure, peer-to-peer communication. Despite their shared capabilities, each SDK tailors to a specific platform, ensuring developers have the tools to integrate wallet functionalities into their applications, regardless of the underlying technology stack.
- Wallet SDK TypeScript is for web-based applications. This SDK targets Browser and NodeJS applications. 
- Wallet SDK KMM targets Android and JVM-based systems and supports Android API level 21+, Kotlin 1.9.22+, and JVM 17+.
- Wallet SDK Swift is for Apple platforms, including iOS and MacOS. This SDK is compatible with iOS 15+, MacOS 12+, and Xcode 13.4+. 
  
The diagram details how the concepts fit alongside the Identus components in a typical SSI interaction:  

<img src="https://docs.atalaprism.io/assets/images/component-diagram-a45b0d2a1ec970a439e28cbe6409cd75.png">

# Effort and Resources
IOG's Atala PRISM team primarily drives the development of this project.   
https://github.com/yshyn-iohk  
https://github.com/patlo-iog  
https://github.com/elribonazo  
https://github.com/FabioPinheiro  
https://github.com/milosh86  
https://github.com/bvoiturier  
https://github.com/curtis-h  
https://github.com/EzequielPostan  
https://github.com/dorultan  
https://github.com/shotexa  
https://github.com/lohanspies  
https://github.com/milosbackonja  
https://github.com/mineme0110  
https://github.com/CryptoKnightIOG  
https://github.com/goncalo-frade-iohk  
https://github.com/petevielhaber  
https://github.com/mkbreuningIOHK  
https://github.com/amagyar-iohk  
https://github.com/essbante-io  
https://github.com/cristianIOHK  

The project also has maintainers who are unaffiliated with IOG.  
https://github.com/bsandmann  
https://github.com/davepoltorak  

In addition to this core group, we have a growing community of users and contributors who provide valuable feedback, bug reports, and contributions crucial to the project's evolution. 
We understand that a diverse range of expertise fuels the project's long-term success.  A larger pool of contributors will speed up innovation and encourage wider use.  We're actively seeking out ways to bring in more contributors and maintainers.  Our strategy includes tapping into Cardano communities and engaging more closely with Hyperledger groups.  This approach will expose our project to a broader audience, increasing the chance that passionate users will become contributors and maintainers.  

# How To
We suggest following the [Quick Start Guide](https://docs.atalaprism.io/docs/quick-start) to better understand the project's scope. Additionally, you can find a tutorial for the Cloud Agent [here](https://docs.atalaprism.io/tutorials/), and more resources are available in the respective repositories of each component.
- https://github.com/hyperledger-labs/open-enterprise-agent 
- https://github.com/input-output-hk/atala-prism-mediator 
- https://github.com/input-output-hk/didcomm-v2-mediator-test-suite 
- https://github.com/input-output-hk/atala-prism-wallet-sdk-ts 
- https://github.com/input-output-hk/atala-prism-wallet-sdk-kmm 
- https://github.com/input-output-hk/atala-prism-wallet-sdk-swift 
- https://github.com/input-output-hk/atala-prism-apollo/ 
- https://github.com/input-output-hk/atala-prism-docs 

# References
<mark>_**References**. See [citation guide](http://www.chicagomanualofstyle.org/tools_citationguide.html)._
</mark>

# Closure

Although we have not set specific metrics, the success criteria of the project measure against the following goals:
- Governance: Achieve effective governance to guide the project's direction, make decisions, and resolve conflicts, contributing to the project's stability and growth.
- Community: Foster a community that contributes code, reports bugs, requests features, contributes to documentation, and participates in forums related to project development.
- Sustainability: Attain a diverse contributor base to reduce dependence on a single contributor or company.
- Active Development: Maintain a regular release schedule and commit to addressing bug fixes and new features.
- Adoption: Measure the number of projects developed on top of Identus.
