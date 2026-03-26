---
layout: default
title: Bob
parent: Incubation
grand_parent: Project Proposals
---

# Sponsor(s)
Kanchan Kaur (kanchan.kaur@consensys.net) - LFDT TAC Member
Rob Dawson (rob.dawson@consensys.net) - General Member, Governing Board
Sally MacFarlane (sally.macfarlane@consensys.net) - Besu Maintainer
Justin Florentine (justin.florentine@consensys.net) - Besu Maintainer
Jason Frame (jason.frame@consensys.net) - Besu Maintainer

# Abstract
Linea is a production-grade, EVM-equivalent ZK rollup providing a complete Layer 2 stack for Ethereum, including execution, consensus, proving, and bridging. It enables scalable, low-cost transactions with cryptographic finality and is designed for open-source, foundation-governed development. The Linea Stack has been deployed on Ethereum Mainnet and is hosted at https://github.com/Consensys/linea-monorepo.

# Context
The Linea Stack was developed by Consensys as the technical foundation of the Linea Mainnet, a public Ethereum Layer 2 network governed by the Linea Consortium. It utilises Besu — an existing LFDT Graduated project — as its principal EVM execution layer.

The Linea Stack is publicly available under Apache 2.0 and MIT licences with an active contributor base and growing external community. This proposal covers the open-source Linea Stack and its governance only — not the operation of Linea Mainnet or Linea Sepolia networks.

# Dependent Projects
Linea depends on the following existing LFDT project:

1. Besu – Linea’s L2 execution layer relies heavily on Besu. Linea uses Besu with L2-specific plugins that tailor its behaviour to meet Linea’s requirements. The Besu team has been closely involved in supporting these integrations and optimising performance.
2. Web3j - Linea’s L2 uses Web3j as a Java library to interact with the L1 and the L2. This integration is used mostly in the coordinator, Maru consensus layer, and Besu plugins.


# Motivation
Ethereum's base layer faces well-documented constraints in throughput, transaction cost, extensibility, and sovereignty that limit its use for enterprise applications. Layer 2 rollup technology addresses these constraints directly, but the ecosystem currently lacks a production-grade, foundation-governed open-source L2 stack.

The Linea Consortium is proposing the Linea Stack for LFDT hosting as a strategic decision to place its core open-source infrastructure under vendor-neutral foundation governance. This advances several key goals:

- Vendor-neutral governance: The Linea Consortium is establishing a governance structure for the Linea Stack that is independent of any single commercial entity, increasing trust among ecosystem participants, enterprise adopters, and institutional partners.
- Progressive decentralisation: Moving stewardship of the Linea Stack to a neutral foundation demonstrates the Linea Consortium's commitment to progressive decentralisation and vendor-neutral governance.
- Broader contributor base: Lowering barriers to entry for external contributors and incentivising participation from organisations that require vendor-neutral governance before contributing.
- Enterprise and institutional confidence: Enterprise adopters increasingly require vendor-neutral governance, IP cleanliness, and open-source foundation hosting as procurement criteria. LFDT hosting satisfies these requirements by default.
- Competitive differentiation: No other major L2 project (Optimism, Arbitrum, Polygon, zkSync, Scroll, Starknet) is hosted under LFDT or a comparable foundation. The Linea Stack would be the first, creating a lasting advantage in enterprise perception.
- Long-term sustainability: Ensuring the Linea Stack has a durable open-source home that outlasts any single company's involvement or strategic direction.

Compared to existing Layer 2 solutions, this project differentiates itself through its EVM equivalence, production readiness, and commitment to vendor-neutral, foundation-led governance. This combination enables stronger enterprise adoption, broader contributor participation, and long-term sustainability relative to alternative approaches.

# Status
Incubating project.

# Solution
The Linea Stack is a complete, EVM-equivalent ZK rollup implementation. Transactions are executed on the L2, batched, proven with a zero-knowledge proof, and finalized on Ethereum L1. The stack requires no modifications to the Ethereum base layer and is designed for deployment on any EVM-compatible network.

# Core Components
| Component | Language(s) | Description |
|----------|------------|-------------|
| L2 Execution Layer | Java / Kotlin | EVM-equivalent execution environment built on Besu, with L2-specific plugins adapting its behaviour to L2 requirements. |
| L2 Consensus Layer (Maru) | Kotlin | Client responsible for L2 consensus coordination, sequencing, and block production. |
| Coordinator | Kotlin | Backend component orchestrating the finalization pipeline between the sequencer, prover, and L1 contracts. |
| Prover | Go | High-performance ZK proving stack generating zero-knowledge proofs for transaction batches, relying on gnark as an upstream dependency. |
| Arithmetization | Go / zkASM | Specification and implementation of zkEVM ISA constraints, including the execution tracer. |
| L1 & L2 Smart Contracts | Solidity | On-chain contracts governing finalization, messaging, token bridging, and yield mechanisms. |
| Postman | TypeScript | Cross-chain message passing backend. |
| SDK / Client Libraries | TypeScript | Developer libraries for interacting with the system. |
| Documentation | Markdown / MDX | Technical documentation, architecture guides, and API references. |

# Security Model
The Linea Stack maintains a rigorous security posture appropriate for production-grade infrastructure:
- Audit process: Comprehensive security audits are conducted for all Linea Stack components prior to release, with particular focus on L1 and L2 smart contracts. Audit reports are made publicly available.
- Security fast-track process: The Maintainers will follow the documented security and vulnerability disclosure process outlined in SECURITY.md, which enables rapid response to critical vulnerabilities while maintaining appropriate transparency. Critical security decisions require a unanimous vote of the Maintainers or Board ratification.

# Out of Scope
The following are explicitly outside the scope of this project:
- Operation of the Linea Mainnet and Linea Sepolia networks, including sequencer operation, validators, governance token, and Security Council activities, as well as Consensys-internal operational infrastructure such as deployment configurations, runbooks, and internal monitoring tooling.
- Applications developed specifically for Linea Mainnet (Linea Hub, custom bridge UI, Linea Token).
- The gnark and gnark-crypto libraries, which remain under Consensys ownership and are referenced as upstream open-source dependencies.

# How To
Getting started resources, contribution guides, and technical documentation are available at the following locations:
| What | Link |
|------|------|
| Documentation site | https://docs.linea.build/ |
| Technical Charter [still in draft format] | TBC |
| Getting started / Installation guide | https://docs.linea.build/stack/quickstart |
| Architectural overview | https://docs.linea.build/network/overview |
| Contributing Guide | https://github.com/Consensys/linea-monorepo/blob/main/docs/contribute.md |
| Developer forum (Discourse) | https://community.linea.build/ |

# References
| What | Link |
|------|------|
| Linea Monorepo | https://github.com/Consensys/linea-monorepo |
| Linea Security Council Charter | https://github.com/Consensys/linea-monorepo/blob/main/contracts/docs/security-council-charter.md |
| Linea Immunefi Bug Bounty | https://immunefi.com/bug-bounty/linea/information/ |
| Linea blog post / public announcement | https://linea.build/blog |
| Linea community call recordings or webinar | https://www.youtube.com/playlist?list=PLJ06SwdM0bLoTMaxUIJmPBuWnJUc57ZaU |

# Closure
The aim is to establish the Linea Stack as a vendor-neutral, foundation-governed open-source ZK rollup — providing the ecosystem with a production-grade, credibly neutral implementation of EVM-equivalent Layer 2 technology. Ultimately, the project aims to build a diverse and active maintainer community under LFDT governance and meet the requirements to become a Graduated LFDT project.

Ultimately, it aims to build a diverse and active maintainer community under LFDT governance and meet the requirements to become a Graduated LFDT project.

# Incubation Entry Criteria
Maintainer Community
There are currently 30 proposed Maintainers of Linea, mostly from Consensys. The team is well-established and fully committed to the project, with a proven track record of active contribution to the Linea codebase. 

| Name | GitHub |
|------|--------|
| François Bojarski | letypequividelespoubelles |
| Olivier Bégassat | OlivierBBB |
| Anonymous | amkCha |
| David Pearce | DavePearce |
| Lorenzo Gentile | lorenzogentile404 |
| Anonymous [Pending Consent] | fluentcrafter |
| Roman Vaseev | Filter94 |
| Gaurav Ahuja | gauravahuja |
| Jones Ho | jonesho |
| Anonymous [Pending Consent] | thedarkjester |
| Anonymous | kyzooghost |
| Victorien Gauch | VGau |
| Alain Nicolas | alainncls |
| Alexandre Belling | AlexandreBelling |
| Anonymous [Pending Consent] | gusiri |
| Srinath Nandakumar | srinathln7 |
| Azam Soleimanian | Soleimani193 |
| Anonymous [Pending Consent] | bogdanbear |
| Arijit Dutta | arijitdutta67 |
| Anonymous [Pending Consent] | FlorianHuc |
| Julien Marchand | julien-marchand |
| Gautam Botrel  | gbotrel |
| Anonymous [Pending Consent] | ThomasPiellard |
| Anonymous [Pending Consent] | ivokub |
| Anonymous [Pending Consent] | Tabaie |
| Yao Galteland | YaoJGalteland |
| Anonymous [Pending Consent] | nadeemb53 |
| Anonymous [Pending Consent] | fab-10 |
| Anonymous [Pending Consent] | daniellehrner |

The maintainer structure is still being refined, and it is expected that a smaller group of core maintainers will be responsible for governance, oversight, and key technical decision-making, in line with LFDT best practices.

A clear path for external contributors to become Maintainers will be documented in MAINTAINERS.md, based on sustained contribution, code quality, community participation, and domain expertise.

# Community Calls
Monthly community calls will be established, open to the public, to discuss development progress, roadmaps, and upcoming releases. Call scheduling and logistics will be coordinated with LFDT staff.
Monthly community calls will follow a fixed schedule. First Wednesday of each month, open to the public, with a recurring format: monthly development recap, rotating technical deep-dive across stack components, roadmap preview, and open Q&A. All calls will be recorded and published on YouTube, with written summaries across LFDT's blog, twitter, discord. A quarterly “community spotlight” slot will feature external contributors and adopters.

# Community Communication
The project will utilize LFDT Discord as a primary channel for community discussion, contributor engagement, and project coordination, alongside GitHub Issues in the linea-monorepo for tracking work, bugs, and feature requests.

Channels and structure in Discord will be defined following onboarding, and are expected to support general discussion, maintainer coordination, release communications, roadmap updates, security-related topics (in accordance with the project’s security policy), and contributor support.

GitHub Issues will serve as the primary system of record for technical discussions, issue tracking, and development workflows, while Discord will enable real-time collaboration and community engagement, ensuring transparency in line with LFDT practices.

# Documentation
The Linea project will maintain comprehensive technical documentation, covering architecture, getting started guides, API references, and contributor resources.

# Test Coverage
The Linea codebase maintains comprehensive test coverage across unit tests, and e2e tests. All pull requests must pass CI test suites before merging. Unit test coverage can be found at https://app.codecov.io/gh/Consensys/linea-monorepo. Version upgrades are conducted on lower environments, starting from Linea Devnet, to Linea Sepolia, then to Linea Mainnet.

# Roadmap
Linea will align with the approach used by Besu for community engagement. LFDT’s Discord server will serve as the primary channel for community communication, with project updates, discussions, and announcements shared there. In parallel, the linea-monorepo GitHub issues will be used to discuss and track tasks.

Linea's Discourse will be sunset following the LFDT announcement.

# CI Pipeline & Release Process
The Linea project operates a structured CI and release process:
- Branch protections are enabled requiring a minimum of 1 maintainer approval before merging if made by a maintainer, or 2 maintainers if it’s from an external contributor
- PRs must pass unit tests, and e2e tests before merging
- Releases are automated through GHAs, artifacts are pushed to Docker Hub
- Release notes are tracked in the documentation website at https://docs.linea.build/release-notes 

# Licensing & IP
- The linea-monorepo is already open-sourced under Apache 2.0 and MIT licences, consistent with LFDT requirements.
- DCO sign-off will be enforced on all commits prior to transfer.
- A comprehensive IP and patent audit of all monorepo components will be conducted prior to transfer, with particular attention to ZK prover circuits.
- All dependencies will be audited for licence compatibility using automated tooling.
