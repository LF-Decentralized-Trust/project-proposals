# VelocityCore Project Proposal

## Identifier
VelocityCore 1.0

## Sponsor
Andres Olave andres.olave@velocitycareerlabs.com

## Abstract

The VelocityCore is enterprise software for creating a "pay-to-verify"
Verifiable Credentials network utilizing a distributed ledger as a
secure key distribution network and for anchoring a trust framework
compatible with global consumer data protection regulations.

## Context

The Velocity Network Foundation is a nonprofit membership organization
established in 2019 with the mission of transforming the way career and
education data is exchanged. By leveraging blockchain technology, the
Foundation aims to break down data silos within employers and
educational institutions, empowering individuals to securely own and
control their professional achievements.

This vision led to the development of VelocityCore, a decentralized
infrastructure that provides individuals with verifiable digital
credentials, effectively forming a trustworthy, tamper-proof resume that
can be universally recognized. Technically VelocityCore is built on top
of the seminal specifications of W3C Decentalized Identifers v1.0 and
W3C Veriable Credentials Data Model v1.1.

## Dependent Projects

Currently VelocityCore is dependent on Hyperledger Besu, though there has been interest in making the same platform available on public ledgers that can be pay-gated.

## Project Motivation

VelocityCore objective is to create a network agnostic pay-to-verify trust-centric Verifiable Credentials ecosystem. The software is designed to ensure trust,
privacy, and incentivization for participants. The key requirements of the network include:

-   Data Layer Interoperability -- Ensuring data is structured and intelligible
    across the network to enable seamless interoperability.

-   Transport Layer Interoperability -- Ensuring data can be exchanged seamlessly between network participants, and between other ecosystems.

-   Personal Data Ownership -- Empowering individuals to own and control
    their data, deciding who has access to it

-   Privacy -- Enforcing strict privacy controls, including no tracking
    of credential usage and no storage of personal data or hashes on
    blockchains.

-   Trusted Data -- Guaranteeing that data received by Relying Parties is:

    -   Issued by reputable entities

    -   Tamper proof

    -   Revocation aware, ensuring validity at time of use

-   Trusted Counterparties -- Ensuring individuals can trust the
    organizations and services they interact with on the network

-   Survivability - Allowing credentials to remain usable even if the
    original issuer no longer exists (eg. Due to bankruptcy or merger)

-   Pay-to-Verify Model -- Establishing compensation mechanisms for all
    contributors, including issuers, node operators, and administrators
    who enforce the network's rules

-   Legal Framework -- integrating a balanced legal structure that
    ensures accountability while promoting fact-based credential
    issuance.

-   Enterprise Readiness -- Ensuring the technology meets the stringent
    security, compliance, and data handling policies required by
    enterprises and governments

## Status
Proposal. Having been in production usage for over two years across multiple organizations having had millions of credentials issued 
it is hoped it can graduate in short time. 

Licensing is already restricted to public licenses _without_ copyleft provisions. Contribution will include mature GitHub action pipelines that run on affected packages only. Test coverage is over 98%.

## Solution

The software architecture of the network is included in the following
diagram. The proposed contributions that make up the proposed
**VelocityCore** project from the existing Velocity Network software
components are shaded in light blue:

![LF Architecture](https://github.com/user-attachments/assets/bcaaf450-573b-430d-a941-6b932c680cbf)

### Potential Objections
A potential objection to accepting VelocityCore is that it doesnt differ significantly from other projects that exist in LF as part of the Decentralized Trust and Open Wallet Foundation. The objection, however, would not be accurate because:
1. VelocityCore focus is on providing a framework to build a trust-centric ecosystem
2. Pay-to-verify features are unique in non-commercial software.
3. Current work items that we continue to develop aim to utilize Credo within VelocityCore to provide OID4CVC and MDL support to the existing software stack. This shows that the VelocityCore builds on top of the contributions of other projects.

### Trust Registry & Registrar Portal
A NodeJS Fastify API with a Portal having a ReactJS Frontend, the Trust Registry serves as the backbone of the ecosystem maintaining a
verified directory of organizations, services & credential types in the ecosystem. It
provides the APIs to create trust framework underpinned by ecosystem administration processes for participants to confidently
interact and exchange credentials.

### Blockchain Contracts

Solidity smart contracts for:

-   Secure storage and distributition of encrypted keys and credential metadata
    issued within the network

-   Pay-to-verify support using an NFT-like mechanism

-   Access control to ensure credentials are only issued and verified by accredited organizations

### Credential Agent

A NodeJS Fastify API used by Issuers and Relying Parties to securely issue, revoke, replace & verify credentials on the network. Unique capabilities include:

-   Multi-tenant with mature data isolation architecture -- ensuring privacy and
    compliance.

-   Enterprise-grade APIs & Data Feeds -- that simplify integration for SaaS
    providers and large organizations to start issuing Credentials that can be accepted
    by the entire network.

-   Flexible authentication mechanisms -- for issuers to validate credential requests.

-   Pay-to-Verify support

-   Integrated credential verification including of issuer trust checks for credentials issued by trusted third parties (aka notaries)
    
### Wallet SDKs

The Wallet SDKs exist for NodeJS, native iOS, native Android, and ReactNative. Targeted at end-user devices, they implement the VelocityCore exchange protocols for network interoperability and integrate into the trust registry for data interoperability, counterparty trust, and data trust.

The SDKs are utilized on reference wallets and a number of other
wallets. The reference wallet may be contributed as a separate project in the near future.


### Standards & Roadmap

Credential Agents implement the above use cases using the open
Velocity Network Credential Exchange Protocol.

A near-term roadmap item includes adding support for OpenID Connect for
Verifiable Credentials (OID4VCI & OID4VP). The team responsible for
developing the Agent & SDK is participating in standards development with the
OpenID Foundation and is exploring utilizing open-source
implementations, including Credo, a Linux Foundation sister project
under the Open Wallet Foundation.

## Effort and Resources

- Andres Olave https://github.com/sloops77
- Nassan Paul https://github.com/nassan
- Michael Avoyan https://github.com/michaelavoyan
- Nataliya Pyvovartseva https://github.com/npyvovartseva
- Itay Podhajcer https://github.com/ItayPodhajcer
- Anil Asimbilen https://github.com/anilasimbilen

Velocity Career Labs and Sertifier provide these developers.

## How To

The project is a monorepo containing the Trust Registry modules, the
Credential Agent modules, the NodeJs Wallet SDK, server packages and all
shared libraries. The build tools used are Lerna & NX. Docker images are
created for each server that is intended to run together using Github
Action pipelines.

### Running Locally

1.  Install dependencies
```
yarn
```

2.  Run integration tests

```
yarn test
```

3.  Run with docker

```
docker compose up
```

**References**

\[W3C Decentralized Identifiers v1.0\] <https://www.w3.org/TR/did-1.0/>

\[W3C Verifiable Credentials Data Model v1.1\]
<https://www.w3.org/TR/2022/REC-vc-data-model-20220303/>

\[RFC7515 JSON Web Signature\] <https://www.rfc-editor.org/rfc/rfc7515>

\[RFC7518 JSON Web Algorithm\]
<https://www.rfc-editor.org/rfc/rfc7518.html>

\[RFC7519 JSON Web Token\] <https://www.rfc-editor.org/rfc/rfc7519>

\[W3C Status List 2021\]
<https://www.w3.org/community/reports/credentials/CG-FINAL-vc-status-list-2021-20230102/>

\[DIF Presentation Exchange v1.0.0\]
<https://identity.foundation/presentation-exchange/spec/v1.0.0/>

\[OpenID for Verifiable Credential Issuance\]
<https://openid.github.io/OpenID4VCI/openid-4-verifiable-credential-issuance-wg-draft.html>

\[OpenID for Verifiable Presentations\]
<https://openid.github.io/OpenID4VP/openid-4-verifiable-presentations-wg-draft.html>

Velocity Network Credential Exchange Protocol
<https://www.velocitynetwork.foundation/main/basics-disclosures-and-verifications>

<https://www.velocitynetwork.foundation/main/basics-issuing>

**Closure**

The end goal would be for 2-3 ecosystems to configure & deploy Velocity Core. Confguration would be for:
1. Credential exchange protocols
2. Credential format protocols
3. Credential types and schemas
4. Payments
5. and more based on community feedback.

