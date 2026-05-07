---
layout: default
title: Hyperledger Token SDK
parent: Incubation
grand_parent: Project Proposals
---

# Sponsor(s)

- Angelo De Caro <adc@zurich.ibm.com>
- Elli Androulaki <lli@zurich.ibm.com>
- Gabi Zodik <zodik@il.ibm.com>
- Kaoutar El Khiyaoui <kao@zurich.ibm.com> 
- Arne Rutjes <arne.rutjesisc@nl.ibm.com>
- Akram Bitar <akram@il.ibm.com>
- Alessandro Sorniotti <aso@zurich.ibm.com>
- Frédéric Faure <Frederic.FAURE@banque-france.fr>
- Corentin Simon <Corentin.SIMON@banque-france.fr>
- Antoine Arnould <Antoine.ARNOULD2@ibm.com>
- Saoussen Marouani <Saoussen.MAROUANI@ibm.com>
- Joris Huynh <joris.huynh@ibm.com>
- Mathilde Ffrench <mathilde.ffrench@fr.ibm.com>
- Thibaud Germain <Thibaud.GERMAIN1@ibm.com>
- Marcus Brandenburger <bur@zurich.ibm.com>
- Jack Xu <jxu@sign.global>

# Abstract

The Hyperledger Token SDK, currently a hyperledger-labs project known as Fabric Token SDK, is a mature, production-grade framework for issuing, transferring, and managing tokens on permissioned blockchain networks. Active since 2021 with proven deployments in wholesale CBDC experiments (Banque de France DL3S, Bank of Canada Project Samara), the SDK provides comprehensive token infrastructure including fungible and non-fungible token support, multiple privacy levels (cleartext FabToken and privacy-preserving ZKAT-DLog with zero-knowledge proofs), and a complete service layer for transaction orchestration, identity management, auditing, and cross-chain atomic swaps. Its driver-based architecture enables network agnosticity across Hyperledger Fabric, FabricX, and other DLT platforms, allowing core application logic to remain portable while the SDK handles backend-specific integration. By standardizing token models and flows under vendor-neutral LFDT governance, the SDK reduces duplication across projects, strengthens security through collaborative review, and establishes a reusable tokenization layer for enterprise blockchain deployments handling real-world financial assets.

# Context

The Token SDK originated in the Hyperledger Fabric ecosystem to address repeated, bespoke implementations of token functionality in chaincode and client applications. Multiple production and pilot deployments have independently implemented tokens for assets such as cash equivalents, loyalty points, supply‑chain units, and carbon credits, all re‑solving similar problems: defining token semantics, handling issuance and transfer logic, encoding privacy requirements, and integrating with Fabric's endorsement and identity mechanisms.

Today, token support in Fabric is not exposed as a cohesive, reusable subsystem. Instead, each project maintains its own chaincode, client code, and operational conventions. The Token SDK extracts common patterns into a shared, well‑tested library and associated components. While it originated in the Fabric ecosystem, its architecture intentionally separates token logic, transaction orchestration, and network integration so that the same core services can be reused across multiple backend implementations. For that reason, the SDK is better positioned as an independent project with its own lifecycle and governance, while remaining closely aligned with Fabric and other LF Decentralized Trust projects.

The project is closely related to Hyperledger Fabric (core platform) and to any existing or emerging LFDT efforts around asset/token standards and identity. We have initiated discussions with the Fabric maintainers and TAC to ensure that this SDK complements rather than duplicates in‑tree features and to clarify the right hosting and governance model under LFDT.

# Dependent Projects

- **Fabric Smart Client (FSC)** – The orchestration platform that provides the Token SDK's runtime environment and core infrastructure services. FSC supplies the view-based programming model for multi-party workflows, peer-to-peer communication channels for off-chain coordination, state management and caching layers, and the plugin architecture that enables the Token SDK to integrate as a modular component. The Token SDK leverages FSC's service abstractions for identity management, storage, and network communication, allowing it to focus on token-specific logic while delegating infrastructure concerns to FSC.

- **Hyperledger Fabric** – The primary permissioned blockchain platform providing the foundational infrastructure for token operations. The Token SDK depends on Fabric's chaincode APIs for on-chain validation logic, endorsement and validation mechanisms for transaction processing, MSP/identity framework for X.509-based authentication. The Fabric driver implements the network interface to translate token operations into Fabric-specific chaincode invocations and transaction submissions.

- **Hyperledger FabricX** – A new implementation of the Fabric protocol designed for high throughput and low latency. FabricX reimagines the Fabric architecture to optimize performance for demanding workloads while maintaining protocol compatibility. The Token SDK's FabricX driver enables applications to leverage this high-performance backend through the same token APIs, allowing seamless migration from traditional Fabric deployments to FabricX for improved scalability. The driver abstracts the protocol differences, enabling token operations to benefit from FabricX's performance characteristics without requiring application-level changes.

# Motivation

Enterprise networks built on Hyperledger Fabric frequently require tokenization of assets: representing money‑like instruments, loyalty units, supply‑chain goods, carbon credits, and other domain‑specific assets as tokens that can be issued, transferred, redeemed, burned, audited, and exchanged atomically according to shared rules. In practice, each project today designs its own token model, writes bespoke chaincode and client logic for issuance and transfer, and couples business logic tightly to that implementation.

This leads to several problems:

- **Duplication and inconsistency** – similar functionality is re‑implemented in different ways, increasing development and maintenance costs.
- **Difficult interoperability and audits** – with no consistent token semantics or transaction flows, it is harder for auditors, regulators, and integrators to reason about behavior and risk.
- **Weaker security posture** – bespoke implementations are more likely to contain subtle bugs, and there is no shared testing and review focus.
- **Slower adoption** – teams must solve low‑level token engineering concerns before focusing on their domain logic.

The Token SDK addresses these issues by providing a shared, extensible framework for tokenization on Fabric and more. It aims to become the default way to build token‑based applications on Fabric while also establishing a reusable tokenization layer that is not bound to a single ledger implementation, offering:

- Well‑defined abstractions for fungible and non‑fungible tokens and common operations.
- Pluggable policies for confidentiality, endorsement, and compliance.
- A reference implementation that can be reviewed, audited, and improved collaboratively by the community.

By hosting this project under LF Decentralized Trust, we ensure neutral governance, open collaboration across organizations, and alignment with other decentralized‑trust building blocks.

# Status

The project is proposed as a new LF Decentralized Trust project in an **incubation** phase. The Token SDK has been in active development since 2021, with a mature codebase implemented in Go, comprehensive documentation, extensive test coverage, and production deployments. The proposal seeks TAC approval to bring the project under LFDT governance, establish vendor-neutral governance, grow a diverse maintainer group, and evolve the SDK to a stable, production‑ready, and widely adopted component under foundation stewardship.

## Project Statistics

## Project Statistics

The following metrics demonstrate the project's maturity, active development, and community engagement (April 16, 2026 at 12:19 CEST):

### Repository Metrics

| Metric | Value |
|--------|-------|
| **Repository** | [github.com/hyperledger-labs/fabric-token-sdk](https://github.com/hyperledger-labs/fabric-token-sdk) |
| **Primary Language** | Go |
| **License** | Apache License 2.0 |
| **Stars** | 98 |
| **Forks** | 91 |
| **Watchers** | 8 |
| **Total Contributors** | 39 |

### Community Standards Compliance
| Standard | Status |
|----------|--------|
| README | ✅ [Complete](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/README.md) |
| CONTRIBUTING | ✅ [Complete](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/CONTRIBUTING.md) |
| CODE_OF_CONDUCT | ✅ [Complete](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/CODE_OF_CONDUCT.md) |
| LICENSE | ✅ [Complete](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/LICENSE) |
| SECURITY Policy | ✅ [Complete](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/SECURITY.md) |

### Development Activity
| Metric | Count |
|--------|-------|
| **Commits (Last 30 Days)** | 74 |
| **Open Issues** | 63 |
| **Closed Issues** | 425 |
| **Open Pull Requests** | 21 |
| **Closed Pull Requests** | 1,047 |

### Contributors

IBM Contributor List (18):
- Angelo De Caro (@adecaro)
- HagarMeir (@HagarMeir)
- Marcus Brandenburger (@mbrandenburger)
- Said Altury (@SaidAltury-ibm)
- Saptha Surendran (@sapthasurendran)
- Thibaud Germain (@thibaudgermain) and Thibaud G. (@Grimnir777)
- Nir Drucker (@drucker-nir)
- Alessandro Sorniotti (@ale-linux)
- KElkhiyaoui (@KElkhiyaoui)
- aaadir (@aaadir)
- Arne (@arner)
- Akram Bitar (@AkramBitar)
- Bar Haim (@barvhaim)
- sreenidhidrIBM (@sreenidhidrIBM)
- Mathilde Ffrench (@mffrench)
- HayimShaul (@HayimShaul)
- nitsatiisc (@nitsatiisc)
- Dave Kelsey (@davidkel)

The rest, 21 contributors, are outside of IBM. 

These statistics reflect a healthy, actively maintained project with:
- **Sustained development velocity** – 70 commits in the last 30 days demonstrates ongoing feature development and maintenance
- **Strong community engagement** – 39 contributors and 87 forks indicate broad adoption and collaborative development
- **Mature issue management** – 418 closed issues vs 64 open shows effective issue resolution and project maintenance
- **Robust code review culture** – 1,036 closed pull requests demonstrates thorough peer review and quality control
- **Complete governance foundation** – All community standards files in place, ready for LFDT governance transition

### Community Engagement and Mentorship

The project actively participates in LFDT mentorship programs to grow the contributor base and engage the broader community. In 2026, the Token SDK is running two mentorship programs:

1. **[Fabric Token SDK - Mentorship Program 1](https://mentorship.lfx.linuxfoundation.org/project/cf3aa0ed-f564-44fd-b11d-ef3fec61e798)** – Focused on onboarding new contributors to core SDK development, driver implementations, and service layer enhancements.

2. **[Fabric Token SDK - Mentorship Program 2](https://mentorship.lfx.linuxfoundation.org/project/851ff636-3a15-4f95-9c6c-9f68ad7500bb)** – Dedicated to expanding documentation, creating tutorials, and developing sample applications to improve developer experience.

These mentorship initiatives demonstrate the project's commitment to community growth, knowledge transfer, and sustainable long-term development under LFDT governance.

# Solution

The Token SDK provides a structured way to define and operate tokens, with the following core elements.

## Core Components

| Component | Language | Description |
|-----------|----------|-------------|
| Token API | Go | High-level developer API for token operations (issue, transfer, redeem) with wallet management and transaction orchestration |
| Driver API | Go | Interface defining the contract for token implementations, enabling pluggable token technologies |
| FabToken Driver | Go | Cleartext UTXO-based token implementation using X.509 identities for transparent auditing |
| ZKAT-DLog Driver | Go | Privacy-preserving token implementation using Pedersen commitments, zero-knowledge proofs, and Idemix for owner anonymity |
| TTX Service | Go | Token Transaction orchestration service managing the complete lifecycle from assembly to finality |
| Network Service | Go | Bridge layer translating token operations to backend-specific formats (Fabric, FabricX, Ethereum) |
| Identity Service | Go | Internal identity management for cryptographic materials, signatures, and wallet operations (X.509, Idemix, multisig, HTLC) |
| Storage Service | Go | SQL-based persistence layer managing token state, transaction history, and identity metadata (SQLite, PostgreSQL) |
| Selector Service | Go | Strategic UTXO selection with locking mechanism to prevent double-spending in concurrent environments |
| Auditor Service | Go | Compliance and oversight tools for authorized auditors to inspect transactions and verify system rules |
| Interop Service | Go | Cross-chain operations via HTLC (Hashed Timelock Contracts) for atomic swaps |
| NFTTX Service | Go | Specialized support for Non-Fungible Tokens with uniqueness constraints and metadata handling |
| Token Chaincode | Go | On-chain validation logic for Fabric networks (optional for FabricX deployments) |
| Tokengen CLI | Go | Utility for generating public parameters, cryptographic materials, and chaincode packages |
| Integration Tests | Go | Comprehensive test suites covering fungible tokens, NFTs, DVP, atomic swaps, and security scenarios |
| Documentation | Markdown | Technical documentation, architecture guides, API references, and developer tutorials |

## Token Models and Operations

The SDK defines clear interfaces and data models for:

- **Fungible tokens** – representing divisible, interchangeable units (e.g., cash‑like instruments, loyalty points). The SDK uses a UTXO (Unspent Transaction Output) model with configurable precision for fractional values.
- **Non‑fungible tokens (NFTs)** – representing unique assets (e.g., physical items, certificates) with support for custom metadata and uniqueness constraints.
- **Hybrid and extensible types** – allowing domain‑specific metadata and policies through driver-specific extensions.

Standard operations include:
- **Issuance**: Creating new tokens by authorized issuers
- **Transfer**: Moving token ownership between parties with automatic UTXO selection
- **Split/Merge**: Automatically handled during transfers to satisfy exact amounts
- **Redemption**: Retiring tokens from circulation (requires issuer approval)
- **Upgrade flows**: Migrating tokens between driver versions (in-place or burn-and-reissue)
- **Atomic exchange patterns**: Cross-chain swaps via HTLC (Hashed Timelock Contracts) through the [Interop Service](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/docs/services/interop.md)

These operations are captured as token transactions with explicit invariants and validation logic, enabling consistent behavior across supported network backends and applications. The [Token Transaction (TTX) Service](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/docs/services/ttx.md) orchestrates the complete lifecycle from assembly to finality.

## Integration with Fabric Network and Clients

On‑chain, the SDK integrates with Fabric token chaincode and validation flows for token state management and transaction validation, while its privacy-preserving drivers and off-chain services handle confidential metadata, auditing data, and client orchestration. Off‑chain, it provides client‑side libraries and helpers to:

- Construct and sign token transactions.
- Enforce client‑side checks (e.g., balances, authorization) before submission.
- Integrate with existing Fabric client SDKs and identity / MSP tooling.

The SDK is designed as an add‑on layer: it does not require changes to the Fabric network protocol or consensus, and it can be deployed incrementally into existing networks via standard chaincode deployment and client updates.

## Confidentiality, Compliance, and Extensibility

The SDK is built to support privacy and compliance requirements commonly seen in regulated and enterprise environments:

- **Confidentiality** – Multiple privacy levels through pluggable drivers:
  - **FabToken**: Cleartext tokens with X.509 identities for transparent auditing
  - **ZKAT-DLog (No Graph Hiding)**: Privacy-preserving tokens using Pedersen commitments and zero-knowledge proofs to hide token types and values while revealing the spending graph. Supports Idemix for owner anonymity and unlinkability. [Technical specification](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/docs/drivers/dlogwogh.md)
  - Integration points for additional cryptographic schemes through the [Driver API](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/docs/driverapi.md)

- **Policy‑driven behavior** – Configurable rules enforced through:
  - Public parameters defining authorized issuers and auditors
  - Endorsement policies for transaction validation
  - Auditor approval requirements via the [Auditor Service](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/docs/services/auditor.md)
  - Role-based wallet management through the [Identity Service](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/docs/services/identity.md)

- **Traceability and testing** – Comprehensive validation:
  - Validator ensures conservation of supply, authorization checks, and cryptographic proof verification
  - [Integration test suites](https://github.com/hyperledger-labs/fabric-token-sdk/tree/main/integration/token) covering fungible tokens, NFTs, DVP, atomic swaps, and malicious transaction scenarios
  - [Benchmark tools](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/docs/drivers/benchmark/benchmark.md) for performance validation

The design is explicitly modular so that future LFDT projects in identity, cryptography, or privacy can plug into the token flows without breaking existing adopters. The [Network Service](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/docs/services/network.md) provides the abstraction layer enabling this extensibility.

## Backward Compatibility and Network Effects

Because the SDK relies on existing Fabric primitives, it does not introduce forks or protocol changes. Existing Fabric networks can:

- Introduce token functionality by deploying SDK‑based chaincode alongside existing applications.
- Gradually migrate bespoke token logic to SDK‑based implementations.
- Co‑exist with legacy token implementations while converging on shared models over time.

The proposal acknowledges that some projects already run production token code. For them, the SDK aims to offer:

- Migration patterns and tooling.
- A path to align semantics incrementally rather than via disruptive rewrites.

## Security Model

The Token SDK maintains a rigorous security posture appropriate for production-grade infrastructure handling financial assets:

### Audit Process

- **Driver Audits**: Comprehensive security reviews are conducted for token drivers, with particular focus on cryptographic implementations (zero-knowledge proofs, Pedersen commitments, Idemix signatures)
- **Smart Contract Audits**: Token chaincode implementations undergo security audits prior to production deployment
- **Dependency Audits**: All dependencies are continuously monitored for known vulnerabilities through automated scanning

### Security Fast-Track Process

The project follows a documented security and vulnerability disclosure process outlined in [SECURITY.md](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/SECURITY.md), which enables rapid response to critical vulnerabilities while maintaining appropriate transparency. Critical security decisions require maintainer consensus and are documented publicly after responsible disclosure periods.

### Cryptographic Security

- **Zero-Knowledge Proofs**: The ZKAT-DLog driver implements cryptographically sound zero-knowledge proofs for privacy-preserving transactions
- **Idemix Integration**: Leverages battle-tested Idemix implementation from Hyperledger Fabric for anonymous credentials
- **Key Management**: Supports both software-based (BCCSP) and hardware security module (HSM via PKCS11) key storage

### Validation and Integrity

- **Transaction Validation**: Multi-layer validation ensures conservation of supply, authorization checks, and cryptographic proof verification
- **Audit Trail**: Comprehensive audit capabilities through the Auditor Service enable compliance and forensic analysis
- **Double-Spending Prevention**: Token locking mechanism and UTXO model prevent concurrent spending of the same tokens

## Production Deployment 

### Banque de France DL3S

The Banque de France (BdF) leverages the **Token SDK** as the core token management layer of **DL3S** (Distributed Ledger for Securities Settlement System), its proprietary private and permissioned DLT platform built on Hyperledger Fabric. Within DL3S, the Token SDK powers the full lifecycle of **Exploratory Cash Tokens (ECT)** — the digital form of wholesale central bank money (wCBDC) — enabling National Central Banks (NCBs) to **mint** (issue), **transfer**, and **burn** (redeem) ECT through role-based wallet abstractions.

The SDK's UTXO model, wallet-based key management, auditability features, and support for fungible tokens map directly onto the operational roles defined in DL3S: NCBs hold an *ECT Issuer* role to mint and redeem tokens, while a *Dedicated Cash Wallet Manager* role allows them to allocate and manage sub-wallets for payment banks and their clients.

Crucially, the Token SDK's **HTLC-based atomic swap** primitive is used to implement DvP (Delivery versus Payment) settlement across heterogeneous DLTs — specifically, to synchronize ECT transfers on DL3S with the digital asset leg settled on an external market DLT operated by a third party, enabling the Full-DLT Interoperability model endorsed by the Eurosystem.

This architecture, which has underpinned over a dozen wholesale CBDC experiments involving institutions such as JP Morgan, HSBC, and multiple Italian banks, demonstrates how the Token SDK can serve as the programmable cash settlement rail for real-world tokenized financial market infrastructure. [Reference: ECB Eurosystem Report](https://www.ecb.europa.eu/press/intro/news/ecb.mipnews231213_annex2.en.pdf)

### Bank of Canada Project Samara

Project Samara's Samara Platform made direct use of the **Token SDK** to implement its cash ledger, which hosted tokenized wholesale central bank deposits (W-CAD). As described in section 4.1.2 of the Bank of Canada's staff analytical paper, the Token SDK provides a comprehensive set of APIs and services for developing token-based distributed applications within the Hyperledger Fabric framework.

The SDK's adoption of the **UTXO model** for transaction management, wallet-based key management, and configurable privacy levels made it well-suited to represent and control W-CAD balances across the permissioned ledger's participants — namely the Bank of Canada, Export Development Canada, RBC, and TD.

Settlement of the tokenized EDC bond against W-CAD was achieved atomically via an **HTLC-based interledger protocol** coordinated by Hyperledger Weaver across the separate bond and cash ledgers, enabling real-time T+0 Delivery versus Payment (DvP) without a central clearing counterparty.

This architecture — with the Token SDK anchoring the cash leg of the transaction — demonstrated that open-source, enterprise-grade token infrastructure can underpin real-world capital markets operations at institutional scale. [Reference: Bank of Canada Staff Analytical Note](https://www.bankofcanada.ca/wp-content/uploads/2026/03/sap2026-8.pdf)

## Network Agnosticity Through Driver Architecture

The Token SDK achieves a degree of network portability through a driver-based architecture that decouples token operations from the underlying Distributed Ledger Technology (DLT). This design allows core application logic to be reused across supported backends such as Hyperledger Fabric and FabricX, and it provides an implementation path for other platforms such as Ethereum. That portability is a key reason the SDK should evolve as an independent project: its scope is broader than a single Fabric runtime, and its abstractions, APIs, and governance concerns extend beyond features that would naturally belong inside the Fabric codebase alone.

### The Driver Pattern

At the core of this architecture is the driver pattern, which consists of two key interfaces:

- **Driver interface** – acts as a factory, creating network instances based on configuration parameters such as network name and channel.
- **Network interface** – defines a comprehensive contract that all network implementations must fulfill, providing methods for transaction submission, endorsement requests, state queries, finality tracking, and public parameter management.

This abstraction reduces backend-specific coupling by exposing a stable interface for transaction submission, endorsement, state queries, finality tracking, and public parameter management. 
In practice, portability is configuration-driven for implemented backends, while additional platforms require a corresponding network driver implementation.

### Implementation and Benefits

The SDK currently provides network implementations for:

- **Fabric driver** – uses traditional chaincode-based endorsement on Hyperledger Fabric peers. [Implementation details](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/docs/services/network-fabric.md)
- **FabricX driver** – leverages Fabric Smart Client nodes as endorsers for optimized performance. [Implementation details](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/docs/services/network-fabricx.md)

An [Ethereum implementation guide](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/docs/services/network-ethereum.md) demonstrates how the architecture can be extended to support EVM-compatible blockchains through either smart contract validation or pre-order execution with FSC endorsers.

Network selection is entirely configuration-driven: applications specify which network and channel to use in YAML configuration files, and the Network Provider automatically selects the appropriate driver, initializes connections, and caches instances for reuse.

This design delivers significant benefits and also justifies independent project status:

- **Portability** – applications can reuse core logic across implemented backends with configuration-driven network selection.
- **Testability** – mock drivers enable testing without real network connections.
- **Flexibility** – different token management systems can use different networks within the same application.
- **Future-proofing** – new blockchain platforms can be supported by implementing the driver interface without changing existing applications.
- **Project neutrality** – the token model, transaction orchestration, wallet abstractions, and upgrade flows can evolve under neutral governance without being coupled to the release cadence or architectural boundaries of any single backend project.

### Technical Architecture

The Network Service acts as a bridge layer between high-level token operations and low-level blockchain protocols. 
When an application initiates a token transfer, it calls methods on the Network wrapper, which delegates to the appropriate driver implementation:

- **In Fabric** – the approval request invokes the token chaincode on endorsing peers and collects signed proposal responses.
- **In FabricX** – the same method contacts FSC endorser nodes via the view protocol and collects off-chain endorsements.
- **In Ethereum** – an implementation could either submit a transaction to a smart contract or collect FSC endorsements for pre-validated state updates.

The driver translates the generic token request into a platform-specific transaction envelope, which is then broadcast to the network's ordering or consensus service. 
Finality tracking is similarly abstracted: implemented drivers monitor their respective ledgers—such as block delivery streams for Fabric and async event queues for FabricX—while other platforms can follow the same integration pattern.

This consistent interface across diverse blockchain platforms enables the Token SDK to support complex use cases like atomic swaps, privacy-preserving transactions, and multi-network deployments while maintaining a clean separation of concerns between business logic and infrastructure.

### Ethereum Integration Feasibility

The SDK's architecture can support Ethereum and EVM-compatible blockchains through two distinct implementation approaches, each with different trade-offs:

**Approach 1: Smart Contract Validation** – The smart contract performs full validation logic on-chain, similar to Fabric's chaincode model. 
The contract validates token requests, maintains unspent token mappings or serial numbers, performs double-spending checks, and executes all validation logic in the EVM. 
This approach is simpler to implement (modulo the crypto operations) but incurs higher gas costs due to on-chain computation.

**Approach 2: Pre-Order Execution with FSC Endorsers** – FSC nodes validate token requests off-chain and endorse state updates, similar to the FabricX model. 
Endorsers sign pre-validated state deltas, which the smart contract then verifies and applies. 
The contract only performs signature verification and double-spending checks on-chain, significantly reducing gas costs. 
This approach requires FSC endorser infrastructure but provides greater flexibility for complex validation logic and privacy requirements.

## Licensing and Intellectual Property

- **License**: The Token SDK codebase is licensed under the Apache License, Version 2.0. All dependencies are compatible with this license, ensuring open-source compliance and enterprise adoption.
- **DCO Sign-off**: All commits to the repository require Developer Certificate of Origin (DCO) sign-off, enforced through CI checks.
- **Trademarks**: The project uses "Hyperledger" and "Fabric" trademarks in accordance with the Linux Foundation's trademark usage guidelines. No additional trademarks are claimed by this project.
- **IP Audit**: A comprehensive intellectual property audit has been conducted on all components, with particular attention to cryptographic implementations (Idemix, zero-knowledge proofs, Pedersen commitments).
- **Dependency Licensing**: All dependencies have been audited for license compatibility using automated tooling integrated into the CI pipeline.

## Out of Scope

The following are explicitly outside the scope of this project proposal:

- **Network Operations**: Operation of specific Fabric networks, including orderer nodes, peer nodes, and certificate authorities. The SDK is infrastructure-agnostic and can be deployed on any Fabric network.
- **Application-Specific Logic**: Business logic specific to particular use cases (e.g., custom compliance rules, domain-specific token types). The SDK provides the framework; applications build on top.
- **Fabric Core Protocol**: Changes to the Hyperledger Fabric core protocol, consensus mechanisms, or chaincode execution model. The SDK operates within existing Fabric capabilities.
- **Upstream Dependencies**: Maintenance of upstream projects like Hyperledger Fabric, Fabric Smart Client, Idemix libraries, or cryptographic libraries (mathlib). These remain under their respective project governance.
- **Operational Tooling**: Deployment configurations, runbooks, monitoring dashboards, and operational procedures specific to individual organizations. The SDK provides monitoring integration points but not operational tooling.

# Effort and Resources

Initial maintainers are committed to:

- **Continuing development and maintenance** of the SDK (bug fixes, new features, documentation)
- **Establishing and operating CI pipelines**: The project already has:
  - [GitHub Actions workflows](https://github.com/hyperledger-labs/fabric-token-sdk/tree/main/.github/workflows) for continuous integration
  - Automated unit tests, integration tests, and code quality checks
  - [CodeQL security scanning](https://github.com/hyperledger-labs/fabric-token-sdk/actions/workflows/codeql-analysis.yml)
  - [Coverage reporting](https://coveralls.io/github/hyperledger-labs/fabric-token-sdk) integrated into the development workflow
  
- **Quality gates and best practices**:
  - [golangci-lint](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/.golangci.yml) for code quality enforcement
  - Comprehensive [testing guidelines](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/docs/development/testing.md) and [idiomatic Go practices](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/docs/development/idiomatic.md)
  - [Makefile-based](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/Makefile) development workflow with targets for linting, testing, and building
  
Several organizations already using or interested in the SDK have expressed willingness to contribute engineering time, documentation, and real‑world use cases. The project targets a 12–24 month roadmap to:

- Stabilize core APIs and data models with versioned releases
- Support a well‑defined set of token use cases (payments‑like, loyalty, supply chain, sustainability assets, NFTs, atomic swaps)
- Achieve a documented set of adopters with clear upgrade and compatibility guarantees
- Expand the driver ecosystem and network backend support

# How To

The project provides comprehensive resources for developers and adopters:

- **Repository and documentation** – The public code repository at [github.com/hyperledger-labs/fabric-token-sdk](https://github.com/hyperledger-labs/fabric-token-sdk) includes:
  - [Comprehensive documentation](https://github.com/hyperledger-labs/fabric-token-sdk/tree/main/docs) covering architecture, APIs, drivers, and services
  - [Contribution guidelines](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/CONTRIBUTING.md) and [development guide](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/docs/development/development.md)
  - [API documentation](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/docs/tokenapi.md) and [usage guide](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/docs/token_sdk_usage.md)
  
- **Quickstart environments** – Multiple ready-to-run examples:
  - [Fabric Samples Token SDK](https://github.com/hyperledger/fabric-samples/tree/main/token-sdk) – Complete sample application with REST API for issuing, transferring, and redeeming tokens
  - [Integration test suites](https://github.com/hyperledger-labs/fabric-token-sdk/tree/main/integration/token) demonstrating fungible tokens, NFTs, and delivery-versus-payment (DVP) scenarios
  - Network Orchestrator (NWO) for programmatically spinning up test networks
  
- **Testing guidance** – Comprehensive testing infrastructure:
  - [Testing documentation](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/docs/development/testing.md) with unit, integration, and benchmark test guidelines
  - [Makefile targets](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/Makefile) for running tests across different configurations
  - Integration tests covering multiple drivers (FabToken, ZKAT-DLog) and network backends (Fabric, FabricX)
  
- **Deployment guidelines** – Production-ready guidance:
  - [Configuration documentation](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/docs/configuration.md) for TMS setup, wallets, and storage
  - [Public parameters lifecycle](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/docs/public_parameters.md) management
  - [Upgradability guide](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/docs/upgradability.md) for token, driver, and storage migrations
  - [Monitoring and metrics](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/docs/development/monitoring.md) integration

These materials serve both as onboarding for new contributors and as a reference manual for adopters.

# References

## Technical Documentation

- **Token SDK Documentation**: [github.com/hyperledger-labs/fabric-token-sdk/docs](https://github.com/hyperledger-labs/fabric-token-sdk/tree/main/docs)
  - [Token SDK Overview](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/docs/tokensdk.md) – Architecture and key concepts
  - [Token API](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/docs/tokenapi.md) – High-level developer API
  - [Driver API](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/docs/driverapi.md) – Interface for token implementations
  - [Services Documentation](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/docs/services.md) – TTX, Network, Identity, Storage services
  - [FabToken Driver](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/docs/drivers/fabtoken.md) – Cleartext UTXO implementation
  - [ZKAT-DLog Driver](https://github.com/hyperledger-labs/fabric-token-sdk/blob/main/docs/drivers/dlogwogh.md) – Privacy-preserving implementation with zero-knowledge proofs

- **Hyperledger Fabric**: [hyperledger-fabric.readthedocs.io](https://hyperledger-fabric.readthedocs.io/) – Core platform documentation (architecture, chaincode, MSP, private data)

- **Fabric Smart Client**: [github.com/hyperledger-labs/fabric-smart-client](https://github.com/hyperledger-labs/fabric-smart-client) – Underlying orchestration platform

## Code and Examples

- **Main Repository**: [github.com/hyperledger-labs/fabric-token-sdk](https://github.com/hyperledger-labs/fabric-token-sdk)
- **Fabric Samples**: [github.com/hyperledger/fabric-samples/tree/main/token-sdk](https://github.com/hyperledger/fabric-samples/tree/main/token-sdk) – Quickstart application with REST API
- **Integration Tests**: [github.com/hyperledger-labs/fabric-token-sdk/tree/main/integration/token](https://github.com/hyperledger-labs/fabric-token-sdk/tree/main/integration/token) – Fungible, NFT, and DVP examples

## Educational Resources

- **Webinar (March 17, 2022)**: ["Tokens in Hyperledger Fabric: What's possible today and what's coming"](https://www.hyperledger.org/learn/webinars/hyperledger-in-depth-tokens-in-hyperledger-fabric-whats-possible-today-and-whats-coming) – Hyperledger Foundation member webinar by IBM Research team
- **Tutorial (October 12, 2023)**: ["How to create a currency management app and deploy it to a Hyperledger Fabric network"](https://www.youtube.com/watch?v=PX9SDva97vQ) – Comprehensive video guide covering token application development and deployment
- **AI-Powered Documentation**: [CodeWiki for Token SDK](https://codewiki.google/repo/hyperledger-labs/fabric-token-sdk) – Interactive exploration and architecture overviews

## Production Deployments

- **Banque de France DL3S**: [ECB Eurosystem Report (Annex 2)](https://www.ecb.europa.eu/press/intro/news/ecb.mipnews231213_annex2.en.pdf) – Wholesale CBDC experiments using Token SDK for ECT (Exploratory Cash Tokens) and DvP settlement
- **Bank of Canada Project Samara**: [Staff Analytical Note (Section 4.1.2)](https://www.bankofcanada.ca/wp-content/uploads/2026/03/sap2026-8.pdf) – W-CAD tokenization and HTLC-based atomic swaps

# Closure

The aim is to establish the Token SDK as a vendor-neutral, foundation-governed open-source tokenization framework — providing the ecosystem with a production-grade, credibly neutral implementation of token functionality for permissioned blockchains.

We consider the project successful when:

- The SDK is adopted by multiple independent networks and applications in production or advanced pilot stages (building on existing deployments like Banque de France DL3S and Bank of Canada Project Samara).
- Its APIs and data models are stable, well‑documented, and versioned, with clear upgrade paths and backward compatibility guarantees.
- The project has a diverse maintainer base across organizations, with active community contributions, regular community calls, and transparent issue resolution.
- Quality metrics are met: high test coverage (>80%), continuous integration across supported networks, automated security scanning, and at least one external security review of critical components.
- The SDK is recognized by the Fabric and LFDT communities as the standard way to implement tokens on Fabric, and is integrated or referenced by related LFDT projects where appropriate.
- A clear path for external contributors to become maintainers is documented and actively followed.

Ultimately, the project aims to build a diverse and active maintainer community under LFDT governance and meet the requirements to become a Graduated LFDT project.

# Incubation Entry Criteria

## Maintainer Community

The project currently has active maintainers from IBM Research and other contributing organizations. The maintainer structure will be formalized under LFDT governance, with a clear path for external contributors to become maintainers based on sustained contribution, code quality, community participation, and domain expertise.

A MAINTAINERS.md file will document the governance structure, decision-making processes, and criteria for maintainer nomination and approval.

## Community Calls

Monthly community calls will be established, open to the public, to discuss development progress, roadmaps, and upcoming releases. Calls will follow a fixed schedule with a recurring format:
- Monthly development recap
- Technical deep-dive on specific components (rotating across drivers, services, and network backends)
- Roadmap preview and feature discussions
- Open Q&A session

## Community Communication
The project will utilize:
- **LFDT Discord** as the primary channel for real-time community discussion, contributor engagement, and project coordination
- **GitHub Issues** in the fabric-token-sdk repository for tracking work, bugs, and feature requests
- **GitHub Discussions** for architectural discussions and RFC-style proposals
- **Mailing lists** for announcements and governance decisions

Discord channels will support general discussion, maintainer coordination, release communications, roadmap updates, security-related topics (in accordance with SECURITY.md), and contributor support.

## Documentation

The project maintains comprehensive technical documentation at [github.com/hyperledger-labs/fabric-token-sdk/docs](https://github.com/hyperledger-labs/fabric-token-sdk/tree/main/docs), covering:
- Architecture and design patterns
- Getting started guides and tutorials
- API references and usage examples
- Driver specifications and implementation guides
- Service documentation
- Development guidelines and contribution processes

## Test Coverage

The Token SDK maintains comprehensive test coverage across:
- **Unit tests**: Testing individual components and functions
- **Integration tests**: End-to-end scenarios covering fungible tokens, NFTs, DVP, atomic swaps, and malicious transaction handling
- **Benchmark tests**: Performance validation and regression detection

All pull requests must pass CI test suites before merging. Test coverage is tracked and reported through [Coveralls](https://coveralls.io/github/hyperledger-labs/fabric-token-sdk).

## CI Pipeline & Release Process

The project operates a structured CI and release process:
- **Branch protections** requiring maintainer approval before merging
- **Automated testing** via [GitHub Actions](https://github.com/hyperledger-labs/fabric-token-sdk/actions) including unit tests, integration tests, linting, and security scanning
- **Code quality enforcement** through golangci-lint with zero-tolerance policy
- **Security scanning** via CodeQL for vulnerability detection
- **DCO enforcement** on all commits
- **Automated releases** with semantic versioning and comprehensive release notes

## Roadmap

The project will align with LFDT best practices for community engagement:
- LFDT Discord will serve as the primary channel for community communication
- GitHub Issues and Discussions will track technical work and architectural decisions
- Quarterly roadmap updates will be published and discussed in community calls
- Major features and breaking changes will follow an RFC process for community input

Key roadmap items for the next 12-24 months:
- Stabilize core APIs with v1.0 release
- Expand driver ecosystem (additional privacy-preserving implementations)
- Enhance network backend support (additional DLT platforms)
- Improve developer experience with enhanced tooling and examples
- Grow production deployment case studies
- Establish security audit cadence for critical components