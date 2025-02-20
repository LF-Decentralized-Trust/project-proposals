# VelcoityCore Project Proposal

## Identifier
VelocityCore 1.0

## Sponsor
Andres Olave andres.olave@velocitycareerlabs.com

## Abstract

The VelocityCore is enterprise software for creating a "pay-to-verify"
Verifiable Credentials network utilizing blockchain as distributed
secure key distribution network and for anchoring the trust framework
that is compatible with global consumer data protection regulations.

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

None

## Project Motivation

VelocityCore is a fully integrated solution for a pay-to-verify
Verifiable Credentials network. The network is designed to ensure trust,
privacy, and incentivization for participants. The key requirements of
the network include:

-   Data Standardization -- Ensuring data is structured and intelligible
    across the network to enable seamless interoperability.

-   Personal Data Ownership -- Empowering individuals to own and control
    their data, deciding who has access to it

-   Privacy -- Enforcing strict privacy controls, including no tracking
    of credential usage and no storage of personal data or hashes on
    blockchains.

-   Data trust -- Guaranteeing that data received by Relying Parties is:

    -   Issued by reputable entities

    -   Tamper proof

    -   Revocation aware, ensuring validity at time of use

-   Survivability - Allowing credentials to remain usable even if the
    original issuer no longer exists (eg. Due to bankruptcy or merger)

-   Counterparty Trust -- Ensuring individuals can trust the
    organizations and services they interact with on the network

-   Pay-to-Verify Model -- Establishing compensation mechanisms for all
    contributors, including issuers, node operators, and administrators
    who enforce the network's rules

-   Legal Framework -- integrating a balanced legal structure that
    ensures accountability while promoting fact-based credential
    issuance.

-   Enterprise Readiness -- Ensuring the technology meets the stringent
    security, compliance, and data handling policies required by
    enterprises and governments

### Software Components and Their Roles:

#### Trust Registry
The Trust Registry serves as the backbone of the ecosystem maintaining a
verified directory of organizations and services on the network. It
provides the necessary trust framework for participants to confidently
interact and exchange credentials.

-   Ensures compliance with network rules, including jurisdiction and
    liability agreements.

-   Enables Know Your Business (KYB) verification for all organizations
    before approval.

-   Acts as an oracle for decentralized network components, including
    blockchain contracts.

-   Flexible credential type support driven by participant need

Without the Trust Registry, the network's viability and trustworthiness
would be significantly compromised.

#### Blockchain Contracts

The network utilizes Hyperledger Besu smart contracts to:

-   Securely store and distribute encrypted keys and credential metadata
    issued within the network.

-   Enforce access controls that ensure credentials are only issued by
    correctly accredited organizations, and only verified after payments
    have been made

-   Manage decentralized organizational permissions transparently and
    efficiently

#### Credential Agent

The Credential Agent is a software solution used by Issuers and Relying
Parties to securely issue, verify, and manage credentials on the
network. Key features include:

-   Flexible authentication mechanisms -- for issuers to validate
    credential requests.

-   Secure data isolation architecture -- ensuring privacy and
    compliance.

-   Enterprise-grade APIs -- that simplify integration for SaaS
    providers and large organizations.
    
#### Wallet SDKs

The Wallet SDKs implement exchange protocols and advanced trust
assurance mechanisms leveraging information from network oracles. They
are used in the reference mobile and web wallets, and third party
wallets that integrate with VelocityCore. VelocityCore wallets include
specialized features such as:

-   Credential categorization for better user experience

-   Dynamic credential rendering supporting the latest credentials
    without new releases

-   Enhanced trust visualization to help users understand credential
    authenticity

-   Support for rendering attachments related to credentials

As part of the Linux Foundation initiative, Velocity Career Labs hope to
to open source the reference device and web wallets in a separate
project proposal.

## Status
Proposal

## Solution

All components described below are licensed under the Apache License.
Significant efforts have been made to ensure that all dependencies do
not utilize copyleft licenses such as GPL, LGPL, MPL, etc. The
components are stored in a monorepo. There are GitHub actions that run
on every PR, and via the use of NX, only affected packages have their
tests run. Each component comes with a style configuration and a
thorough suite of integration tests with coverage of the entire
repository at more than 98%.

Unless noted otherwise, the codebase utilizes NodeJS for servers, React
for UIs and Mongo for databases. There is the possibility of extending
the systems to support other databases.

The software architecture of the network is included in the following
diagram. The proposed contributions that make up the proposed
**VelocityCore** project from the existing Velocity Network software
components are shaded in light blue:

![LF Architecture](https://github.com/user-attachments/assets/bcaaf450-573b-430d-a941-6b932c680cbf)

### Trust Registry

The trust registry consists of four main parts: Organization Registar,
Organization Oracle, Credential Registry & Network Event Processing. The
server side of all three share a number of traits: written in NodeJS and
connect to Mongo databases. They also utilize email and storage services
via adapters. The current set of adapters provided are for AWS.

#### Organization Registrar

A user interfaces and set of APIs that enables both human and systems
for CRUD transactions for users, organizations, and services for
authorized members of those organizations.

Users are needed for authentication and authorization.

Organizations have profiles on the network including names, brands,
registration numbers, and key personnel. To register an organization
must have a Decentralized identifiers (DID) with the DID:WEB method the
only method currently supported (previously DID:ION had been supported
as well). Custodial services are offered for those organizations that
require a DID Document and Key service provider. All information on the
registrar is available to the network using the Organization Oracle.

Organizations also have network services such as "issuing service",
"relying party service" or "credential agents". These services are
hosted at particular URLs or by particular service providers. Each
service must be registered on the network and is separately approved by
the network administrators.

Service providers are developers with either self-hosted or SaaS
products. They need a streamlined process to onboard their existing
clients who are the issuers or relying parties. The registrar supports
providers sending invitations to clients, prefilling the profile and
service information on their clients' behalf, to simplify the onboarding
process.

Certain actions require consent of the organization signatories to
create legally binding contracts. These processes include sending
notification/reminder emails.

The UI supports both the custodial and non-custodial use case for
organizations. It is written in ReactJS utilizing the Material UI
framework.

#### Organization Oracle

Firstly, the organization registry provides public APIs for
decentralized components to query and obtain DID resolution services,
public key resolution services, last resort resolution for accreditation
documentation, and Organization search.

#### Credential Registrar

To meet the aim of data standardization and interoperability, the
credential registrar contains the credential type information for any
credential issued on the network, including a credential schema,
multilingual display descriptors, and categorization details. To add
credentials the user must be able to authenticate as an organization
member.

#### Network Event Processing

The events on the network that need to be processed include:

-   Rewarding Issuers by analysing issuing events

-   Updating management information systems by processing token mint,
    burn, and transfer events

### Blockchain & Contracts

The network leverages Hyperledger Besu to establish a permissioned
private network among VelocityCore node operators. Besu's enhanced
control over node membership allows VelocityCore instances to require
agreement with legal contracts --- beyond the standard requirements of
public network node operators. Any Besu-supported consensus algorithm
can be utilized.

The Contracts cover:

-   Permissions on-chain that restrict writes and reads based on network
    administrator approvals

-   Credential metadata

    -   Support writing credential metadata to the blockchain for
        permissioned issuers

    -   "Pay to verify" that permits access to encrypted metadata upon
        proof of payment for registered relying parties

-   Coupons with expiration dates contract based on ERC-721 (NFT)

The blockchain contracts are written in Solidity.

### Credential Agent

The Credential Agent is a software solution designed for both Issuers
and Relying Parties, featuring dedicated modules addressing their
specific use cases. At its core the Agent is issuing and verifying
Verifiable Credentials using W3C Decentralized Identifiers for key
management. The agent currently supported W3C Verifiable Credentials
v1.1 compliant credentials that use the JWT (RFC7519) proof format.
Signatures can be generated using SECP256K1, with PRs already open to
also support RS256 and P-256 signatures. 1EdTech Open Badge v3.0 is also
supported as any of our particpants already use the Open Badge format
for expressing simpler achievements.

Furthermore, the Credential Agent supports enterprise and SaaS providers
by offering:

-   Multi-tenant support with data isolation at the repository level.

-   Pluggable KMS or HSM integration for managing signing keys.

-   Event-based data ingestion, enabling inclusion in KPIs and
    management dashboards.

#### Operator configuration

The Credential Agent is fully programmable via API and operator
endpoints for:

-   Tenant management -- CRUD APIS are used to add and manage agent
    tenants. The organization information must be preregistered on the
    Trust Registry and have activated services on the.

-   Tenant key import and rotation -- Keys are used for signing
    blockchain transactions, decentralized authentication, and assertion
    traceability.

-   Service configuration management via CRUD APIs -- Issuers and
    Relying Parties can configure services using a Disclosure entity,
    which supports DIF Presentation Exchange for requesting credentials.
    Issuance additionally supports preauthorization codes for user
    authentication.

-   Deep link and QR code generation -- Deep links and QR codes can be
    created for specific services and can optionally configured to
    contain authentication details for specific users.

-   Credential offers -- Credential offers are linked to a specific user
    identifier

-   Credential revocation -- Credentials can be revoked with status
    stored on an on-chain status list conforming to the W3C Status List
    2021 specification

#### Wallet Interaction

The Credential Agent hosts endpoints for interacting with Verifiable
Credential wallets supporting both Relying Party and Issuer user cases
through dedicated modules.

##### Relying Party module

A Relying Party creates a service and configures the credential types it
requires along with the terms for data sharing. Once a user accepts the
terms and selects matching credentials the wallet sends the data to the
Credential Agent.

To receive the credentials from the agent, the Relying Party must deploy
a presentation reception webhook.

Since VelocityCore requires payment for verification, the agent allows a
Relying Party to receive credentials initially without verification.
Verification can be triggered later via API once payment is made. There
are two webhook variants for receiving credentials

-   Automatic verification -- Credentials are immediately verified, and
    all checks are performed.

-   Deferred verification -- Credentials are received without
    verification

###### Credential Verification Checks

The Relying Party Module performs multiple verification checks to ensure
the authenticity and validity of received credentials:

-   Proof check -- Verifies the credential's digital signature for
    integrity and authenticity

-   Issuer check -- Ensures that

    -   The credential's key was created by the Issuer

    -   The Issuer is approved on the Trust Registry to issue the
        specific credential type

    -   If the Issuer is a third-party, they are accredited for
        providing third-party attestations.

-   Revocation check -- Ensures the credential has not been revoked,
    using W3C Status List without phoning home to the original Issuer

-   Holder check -- Confirms that the credential is being presented by
    the intended credential recipient

-   Validity check -- Ensures that the credential is within its validity
    period.

##### Issuer module

An issuer creates a service, the user authentication modes, and sets the
terms for credential issuance, including how authentication data is
handled.

While Relying Parties must always implement webhooks Issuers can either:

-   Implement webhooks to support real-time data sourcing.

-   Preconfigure the Agent via API so that it can process credential
    issuance requests independently.

In both cases two steps must be handled:

-   User authentication -- Authentication can be based on credentials
    already in the user's possession or by utilizing preauthorization
    codes generated by an authorization service controlled by the
    Issuer.

-   Credential Offer -- Generating credentials for the authenticated
    user. Webhooks can also support deferred issuing where an
    authenticated user may need to wait before receiving a credential.
    This applies to cases such as semi-automated IdV processes for
    issuing driver's license credentials.

##### Standards & Roadmap

Credential Agents implement the above use cases using the open-source
Velocity Network Credential Exchange Protocol.

A near-term roadmap item includes adding support for OpenID Connect for
Verifiable Credentials (OID4VCI & OID4VP). The team responsible for
developing the Agent is participating in standards development with the
OpenID Foundation and is exploring utilizing open-source
implementations, including Credo, a Linux Foundation sister project
under the Open Wallet Foundation.

### Wallet SDK

There are four SDKs that have been implemented in Swift for iOS, Kotlin
for Android, ReactNative and NodeJS for device and server wallets. They
implement the Velocity Network Credential Exchange Protocol and provide
APIs for wallet applications to bind to. They cover both the transport
layer and the trust layer of the protocol.

The SDKs are utilized on all reference wallets and a number of other
wallets.

## Effort and Resources

Velocity Career Labs will provide at least 5 developers covering all
elements of the solution.

Sertifier will provide a developer to support the Wallet SDKs.

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

TBD
