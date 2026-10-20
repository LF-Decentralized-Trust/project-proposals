---
layout: default
title: "{NEW-NAME} (formerly Fabric-X)"
parent: Incubation
grand_parent: Project Proposals
---

# Project Identifier

{NEW-NAME} (formerly Hyperledger Fabric-X) Project Proposal v0.1

# Sponsor(s)

- Elli Androulaki <lli@zurich.ibm.com>
- Gabi Zodik <zodik@il.ibm.com>
- Mark Lewis <mark_lewis@uk.ibm.com>
- David Enyeart <enyeart@us.ibm.com>
- Andrew Coleman <andrew_coleman@uk.ibm.com>
- Angelo De Caro <adc@zurich.ibm.com>
- Kaoutar El Khiyaoui <kao@zurich.ibm.com>
- Arne Rutjes <arne.rutjesisc@nl.ibm.com>
- Alessandro Sorniotti <aso@zurich.ibm.com>
- Hagar Meir <hagar.meir@ibm.com>
- Ilie Circiumaru <ici@zurich.ibm.com>
- Liran Funaro <liran.funaro@ibm.com>
- Pasquale Convertini <Pasquale.Convertini@ibm.com>
- Senthilnathan Natarajan <snatara7@in.ibm.com>
- Yoav Tock <tock@il.ibm.com>
- Marcus Brandenburger <bur@zurich.ibm.com>
- Jack Xu <jxu@sign.global>
- Jay Hu <jayhu@sign.global>
- Peter Broadhurst <peter.broadhurst@kaleido.io>
- Jim Zhang <jim.zhang@kaleido.io>
- Matthew Whitehead <matthew.whitehead@kaleido.io>

# Abstract

Fabric-X is a high-throughput, microservice-based distributed ledger for digital assets. Today it is an
incubating sub-project under the Hyperledger Fabric umbrella. This proposal asks the TAC to establish it as an
independent LF Decentralized Trust Incubation project under a new, distinct name ({NEW-NAME}), governed by a
standard single-project technical charter. The code, maintainers and roadmap stay the same. Only the name,
repository locations and governance structure change.

# Context

Fabric-X was contributed to the Hyperledger Fabric ecosystem in 2025 through the Fabric RFC process:

- [RFC #63: Fabric-X, a microservice-based Hyperledger Fabric for high-throughput systems](https://github.com/hyperledger/fabric-rfcs/pull/63)
  (merged July 1, 2025)
- [RFC #64: Fabric Ecosystem Coexistence Model](https://github.com/hyperledger/fabric-rfcs/pull/64)
  (merged June 30, 2025)

To host it, the [Hyperledger Fabric Technical Charter](https://github.com/hyperledger/fabric/blob/main/Hyperledger_Fabric_Technical_Charter.md)
was amended (June 26, 2025) to create a two-layer structure:

- an **Ecosystem Committee** made up of the sub-project TSC chairs;
- one **TSC per sub-project**: the Fabric ("Classic Fabric") TSC and the Fabric-X TSC
  (see [GOVERNANCE.md](https://github.com/hyperledger/fabric/blob/main/GOVERNANCE.md)).

Classic Fabric is a mature, Graduated project. Fabric-X is in Incubation. The two are different projects with
independent codebases, maintainers, development roadmaps and release cycles. Fabric-X reached v1.0.0 in May 2026.

The drawbacks of the umbrella model were anticipated when it was created. RFC #64 lists brand confusion and
increased governance overhead as drawbacks. During review of RFC #63, several community members argued that
Fabric-X should go through incubation as an independent, first-class LFDT project rather than as part of
Fabric. A year of operating under the umbrella has confirmed these concerns (see Motivation).

The LFDT TAC has also hit the limits of the model. Since June 2026 the TAC agenda has repeatedly included
"sub-project maturity levels and governance" and "project lifecycle classification for projects that span
multiple maturity levels under one project umbrella". The review of the
[2026 Fabric / Fabric-X mid-year report](https://github.com/LF-Decentralized-Trust/governance/pull/370#pullrequestreview-5236818574)
noted that "the two parts of the broader Fabric project are at different levels of maturity" and that
"formalising how this can be represented would be useful to TAC members reviewing reports".

This proposal resolves the issue directly by making Fabric-X a project of its own.

# Dependent Projects

**Upstream: Hyperledger Fabric.** Fabric-X reuses Fabric's protobuf definitions (fabric-protos) and the
Broadcast/Deliver gRPC APIs. The `fabric-x-common` repository carries code derived from Fabric v3 (MSP,
policies, configtx and CLI tools). This relationship continues unchanged after the separation. The Fabric
maintainers are being consulted through the Fabric Ecosystem Committee, which must approve the separation under
the Fabric charter.

**Downstream: projects that depend on Fabric-X.** Their maintainers are being informed of this proposal and asked
to sign off.

- [Panurus](https://github.com/LFDT-Panurus/panurus) (formerly the Fabric Token SDK) provides a Fabric-X network
  driver and depends on `fabric-x-common`.
- [Fabric Smart Client](https://github.com/hyperledger-labs/fabric-smart-client) (Hyperledger Lab) is the framework
  for building distributed applications on Fabric and Fabric-X. It provides a dedicated Fabric-X platform
  (`platform/fabricx`), depends on `fabric-x-common`, and is the base of the Fabric-X endorser.
- [fabric-x-ansible-collection](https://github.com/LF-Decentralized-Trust-labs/fabric-x-ansible-collection)
  (LFDT Lab) is the Ansible collection used to deploy Fabric-X networks locally, on Kubernetes and on OpenShift.
- [fabric-x-block-explorer](https://github.com/LF-Decentralized-Trust-labs/fabric-x-block-explorer) (LFDT Lab)
  is a block explorer that ingests blocks from the Fabric-X committer sidecar. It indexes them in PostgreSQL and
  serves blocks, transactions and namespace policies through a REST API and a web UI.

fabric-x-evm, which depends on the committer, common and SDK modules, is part of this project (see Solution)
rather than a dependent project.

# Motivation

Two projects with nearly identical names, under the same `hyperledger/fabric*` repository prefix and a single
umbrella project, cause confusion for every audience.

- **Users and adopters** cannot easily tell the two projects apart. They are unsure which one to choose for a
  given use case, and which maturity level and release cycle applies to the one they choose.
- **Inherited connotations.** The name "Fabric" implies concepts that Fabric-X deliberately dropped:
  - channels: Fabric-X has a single ledger partitioned into namespaces;
  - chaincode: replaced by endorsers built with the Fabric Smart Client, and by peer-to-peer negotiation
    protocols;
  - the monolithic peer: decomposed into independently scalable services.
  - private data collection: are no longer supported. Fabric-X handles privay via the endorsers' peer-to-peer 
    negotiation protocols and ZKP protocols (see Panurus).

  Users and evaluators carry Fabric's assumptions, strengths and limitations over to a system with a different
  design.
- **Brand recognition.** The market does not see Fabric-X as distinct from Fabric. Its distinguishing features,
  such as high throughput, Byzantine-fault-tolerant sharded ordering and a digital-asset focus, get lost.
- **Developers and contributors** find it hard to see where one project ends and the other begins, and which team
  and TSC is responsible for what.
- **Governance and reporting.** LFDT processes assume a flat structure of one project with one lifecycle state.
  The two-layer umbrella makes it hard for the TAC and LFDT staff to track and publicize each project's maturity,
  and to handle its periodic reports. For example, Fabric and Fabric-X currently share one report entry and one
  report document (see the 2026 mid-year report discussion above). Each project carries the overhead of a
  structure designed for a different case.

Separating the projects benefits both:

- Fabric keeps a clear identity as a mature, Graduated platform.
- {NEW-NAME} can build its own brand, community and roadmap around digital assets and high-throughput use cases.
- Each project has a single lifecycle state, a single charter and a single reporting line to the TAC.

# Status

Incubation (continuing). Fabric-X is already an incubating LFDT project, currently held within the Fabric
umbrella. This proposal requests that it continue in Incubation as a standalone project.

## Project Statistics

Measured October 20, 2026.

### Repositories

| Metric | Value |
|--------|-------|
| **Repositories** | 9 (`hyperledger/fabric-x`, `-orderer`, `-committer`, `-common`, `-endorser`, `-sdk`, `-samples`, `-evm`, `-rfcs`); metrics below cover the first seven |
| **Primary language** | Go |
| **License** | Apache License 2.0 |
| **Stars (total)** | 149 |
| **Forks (total)** | 164 |
| **Latest releases** | fabric-x v1.0.2, orderer v1.0.6, committer v1.0.5, common v0.2.10, sdk v0.1.0 |

### Development Activity

| Metric | Value |
|--------|-------|
| **Commits, last 30 days** | 110 |
| **Commits, last 12 months** | 1,246 |
| **Distinct human authors, last 12 months** | ~41 |
| **Merged pull requests (all time)** | 1,424 |
| **Closed issues (all time)** | 819 |
| **Maintainers** | 11 |

The [2026 mid-year report](https://github.com/LF-Decentralized-Trust/governance/pull/370) has a detailed account
of H1 2026 activity. It covers the v1.0.0 release of the orderer and committer, dynamic orderer reconfiguration,
the new EVM and SDK repositories, a unified documentation site, and multi-region performance benchmarks.

# Solution

## Proposed Changes

1. **New name.** Rename Fabric-X to a distinct, unique name ({NEW-NAME}), chosen according to the LFDT
   [Naming Guidelines](https://github.com/LF-Decentralized-Trust/wiki/wiki/Naming-Guidelines) and cleared for
   trademark by the Linux Foundation.
2. **Independent project.** Establish {NEW-NAME} as an independent LFDT Incubation project, separate from the
   Hyperledger Fabric umbrella.
3. **Single-project charter.** Adopt a standard LFDT single-project technical charter, modeled on the
   [original single-TSC Hyperledger Fabric charter](https://github.com/hyperledger/fabric/blob/267b251e32995b8b99aa9c74869f2ec3827de4bd/Hyperledger_Fabric_Technical_Charter.md)
   (adopted August 16, 2024) and the [Panurus charter](https://github.com/LFDT-Panurus/TSC/blob/main/panurus_Charter.pdf)
   (adopted June 18, 2026). There is one TSC, made up of the project's maintainers. The current Fabric-X TSC
   carries over as the {NEW-NAME} TSC.
4. **Same maintainers.** All current Fabric-X maintainers remain maintainers of the corresponding repositories.
5. **Repository renames.** Rename every `hyperledger/fabric-x*` repository that belongs to the project. Two
   naming options are proposed. The maintainers will choose one together with LFDT staff:
   - **Option A: prefixed repositories in a shared organization.** Each repository keeps a project prefix
     (`{new-name}-orderer`) inside an existing or shared GitHub organization.
   - **Option B: dedicated organization.** The project gets its own GitHub organization named after the project,
     and repositories drop the prefix (`{new-name}/orderer`). Other LFDT projects such as Hiero (`hiero-ledger`)
     and Panurus (`LFDT-Panurus`) follow this pattern.

| Current repository | Option A: prefixed | Option B: dedicated org |
|--------------------|--------------------|-------------------------|
| [hyperledger/fabric-x](https://github.com/hyperledger/fabric-x) | `{new-org}/{new-name}` | `{new-name}/{new-name}` |
| [hyperledger/fabric-x-orderer](https://github.com/hyperledger/fabric-x-orderer) | `{new-org}/{new-name}-orderer` | `{new-name}/orderer` |
| [hyperledger/fabric-x-committer](https://github.com/hyperledger/fabric-x-committer) | `{new-org}/{new-name}-committer` | `{new-name}/committer` |
| [hyperledger/fabric-x-common](https://github.com/hyperledger/fabric-x-common) | `{new-org}/{new-name}-common` | `{new-name}/common` |
| [hyperledger/fabric-x-endorser](https://github.com/hyperledger/fabric-x-endorser) | `{new-org}/{new-name}-endorser` | `{new-name}/endorser` |
| [hyperledger/fabric-x-sdk](https://github.com/hyperledger/fabric-x-sdk) | `{new-org}/{new-name}-sdk` | `{new-name}/sdk` |
| [hyperledger/fabric-x-samples](https://github.com/hyperledger/fabric-x-samples) | `{new-org}/{new-name}-samples` | `{new-name}/samples` |
| [hyperledger/fabric-x-evm](https://github.com/hyperledger/fabric-x-evm) | `{new-org}/{new-name}-evm` | `{new-name}/evm` |
| [hyperledger/fabric-x-rfcs](https://github.com/hyperledger/fabric-x-rfcs) | `{new-org}/{new-name}-rfcs` | `{new-name}/rfcs` |

The related LFDT Labs (fabric-x-ansible-collection, fabric-x-block-explorer and fabric-x-migrate) are not part
of this project. Renaming them is at the discretion of their maintainers.

## Transition Plan

1. **Name selection.** Maintainers propose candidate names. LFDT marketing and legal staff check them against
   the naming guidelines and do trademark clearance.
2. **Governance.** The Fabric Ecosystem Committee approves the separation and amends the Fabric charter to remove
   the Fabric-X sub-project. The Fabric `GOVERNANCE.md` is updated. The {NEW-NAME} single-project charter is
   adopted. The Fabric umbrella may revert to a single-project structure, at the Fabric maintainers' discretion.
3. **Repositories.** Rename and transfer the GitHub repositories. GitHub redirects keep existing links and clones
   working. Go module paths are migrated in a new release of each module. The old paths stay buildable and are
   marked deprecated, giving downstream projects (Panurus, Fabric Smart Client, the Ansible collection, the block explorer) a clear upgrade
   path. Container images and binaries are published under the new name.
4. **Community and documentation.** Rename the documentation sites, Discord channels, community calls and LFX
   entries. Publish an announcement blog post. Add a "formerly Fabric-X" note to all READMEs and docs for
   continuity.
5. **Reporting.** From the next reporting period, {NEW-NAME} files its own TAC reports, separate from Fabric.

## Architecture Overview

Fabric-X redesigns Fabric's architecture for digital assets such as central bank digital currencies,
stablecoins, tokenized deposits and tokenized securities. It keeps Fabric's execute-order-validate model,
X.509-based identities (MSP), endorsement policies and Broadcast/Deliver APIs. It replaces the monolithic peer
with independently scalable microservices, and Fabric's ordering service with the **Orderer**, a sharded
Byzantine-fault-tolerant ordering service that orders compact transaction digests. A transaction dependency graph enables
parallel validation. This combination has demonstrated throughput above 100,000 transactions per second
([Fabric-X paper](https://eprint.iacr.org/2023/1717)).

![Fabric vs. Fabric-X](https://raw.githubusercontent.com/hyperledger/fabric-x/main/diagrams/Fabric_vs_Fabric-X.png)

| Component | Language | Description |
|-----------|----------|-------------|
| [Orderer](https://github.com/hyperledger/fabric-x-orderer) | Go | Sharded BFT ordering service: routers, batchers (one group per shard), consenters (SmartBFT) and assemblers that produce a Fabric-compatible block stream |
| [Committer](https://github.com/hyperledger/fabric-x-committer) | Go | Decomposed validation and commit pipeline: sidecar, coordinator (dependency graph), signature verifiers, validator-committers (MVCC) and query service, backed by an SQL database (YugabyteDB or PostgreSQL) |
| [Endorser](https://github.com/hyperledger/fabric-x-endorser) | Go | Endorsement framework built on Fabric Smart Client. It replaces chaincode and supports threshold endorsements |
| [SDK](https://github.com/hyperledger/fabric-x-sdk) | Go | Client SDK for building and submitting transactions to Fabric-X (and Fabric 3) |
| [Common](https://github.com/hyperledger/fabric-x-common) | Go | Shared protobuf APIs, MSP, policy and configuration libraries, and CLI tools |
| [Samples](https://github.com/hyperledger/fabric-x-samples) | Go | Sample networks and applications (devnet, tokens, custom endorser, EVM) |
| [EVM](https://github.com/hyperledger/fabric-x-evm) | Go | Runs Ethereum smart contracts on Fabric-X (and Fabric 3) through a native EVM and an Ethereum JSON-RPC gateway |
| [RFCs](https://github.com/hyperledger/fabric-x-rfcs) | Markdown | Design proposals (RFCs) for the project |
| [Umbrella repo](https://github.com/hyperledger/fabric-x) | Go | Documentation, tools, integration tests and release coordination |

More detail is in the
[orderer architecture](https://github.com/hyperledger/fabric-x-orderer/blob/main/docs/architecture.md) and
[committer architecture](https://github.com/hyperledger/fabric-x-committer/blob/main/docs/architecture.md)
documents.

## Compatibility and Integration

- **Fabric.** {NEW-NAME} will continue to keep compatibility with Fabric through shared protobuf and API
  definitions, as it does today. The separation does not change any interface. Migration from Fabric to Fabric-X
  is supported by the [Fabric-X-Migrate](https://github.com/LF-Decentralized-Trust/lab-proposals/issues/21) lab.
- **Other LFDT projects.** {NEW-NAME} will pursue closer integration with other LFDT technologies, including
  Paladin and Besu's EVM, building on the project's [EVM component](https://github.com/hyperledger/fabric-x-evm) and on Panurus for tokenization.

## Licensing and Trademarks

- All code is licensed under the Apache License 2.0. Documentation is CC-BY-4.0 where noted.
- All commits carry a DCO sign-off.
- The new name will not use the "Hyperledger" or "Fabric" trademarks. The name and any logo will be transferred
  to, and registered by, the Linux Foundation.

## Out of Scope

- No technical change to Hyperledger Fabric (Classic Fabric), its repositories or its governance, other than
  removing the Fabric-X sub-project from the Fabric charter and `GOVERNANCE.md`.
- No change to the Fabric-X codebase, architecture or roadmap beyond the rename.
- No change to the set of maintainers.

# Effort and Resources

The project is maintained by its current 11 maintainers, with about 40 contributors active in the last 12 months.

| Maintainer | GitHub | Repositories |
|------------|--------|--------------|
| Hagar Meir | @HagarMeir | fabric-x, orderer |
| Yoav Tock | @tock-ibm | fabric-x, orderer, common |
| Liran Funaro | @liran-funaro | fabric-x, committer, common |
| Senthilnathan Natarajan | @cendhu | fabric-x, committer, common |
| Marcus Brandenburger | @mbrandenburger | fabric-x, endorser, sdk |
| Ilie Circiumaru | @iliecirciumaru | fabric-x |
| Pasquale Convertini | @pasquale95 | fabric-x |
| Angelo De Caro | @adecaro | endorser |
| Alessandro Sorniotti | @ale-linux | endorser, sdk |
| Arne Rutjes | @arner | sdk |
| Eyal Kushnir | @kushnireyal | sdk |

The rename is a bounded effort for the existing maintainers:

- repository and module renames;
- updates to CI, release and documentation pipelines;
- communication with downstream projects.

LFDT staff support is requested for name and trademark clearance, the charter, GitHub organization setup and
Discord changes. The goal is to complete the transition within one quarter of TAC approval.

# How To

- **Documentation:** [Fabric-X umbrella README](https://github.com/hyperledger/fabric-x/blob/main/README.md),
  [committer docs](https://hyperledger.github.io/fabric-x-committer/) and
  [orderer docs](https://github.com/hyperledger/fabric-x-orderer/tree/main/docs).
- **Deploy a network:** use the [Fabric-X Ansible collection](https://lf-decentralized-trust-labs.github.io/fabric-x-ansible-collection/),
  which supports local, remote, Kubernetes and OpenShift deployments and includes a step-by-step tutorial.
- **Try the samples:** [fabric-x-samples](https://github.com/hyperledger/fabric-x-samples) includes a 4-party
  devnet (BFT orderer and full committer stack), a token application, a custom endorser and an EVM sample.
- **Build and test:** each repository has Makefile targets for unit and integration tests, run in CI with GitHub
  Actions. A version compatibility matrix is published in the umbrella README.

# References

- Hyperledger Fabric RFC #63: [Fabric-X: A Microservice-based Hyperledger Fabric for High-Throughput Systems](https://github.com/hyperledger/fabric-rfcs/pull/63), 2025.
- Hyperledger Fabric RFC #64: [Fabric Ecosystem Coexistence Model](https://github.com/hyperledger/fabric-rfcs/pull/64), 2025.
- [Hyperledger Fabric Technical Charter](https://github.com/hyperledger/fabric/blob/main/Hyperledger_Fabric_Technical_Charter.md), amended June 26, 2025.
- [Hyperledger Fabric GOVERNANCE.md](https://github.com/hyperledger/fabric/blob/main/GOVERNANCE.md).
- LFDT TAC: [2026 Fabric / Fabric-X Mid-Year Report](https://github.com/LF-Decentralized-Trust/governance/pull/370).
- [LFDT Project Lifecycle](https://lf-decentralized-trust.github.io/governance/governing-documents/project-lifecycle/).
- Androulaki et al., [Fabric-X: Scaling Hyperledger Fabric for Asset Exchange](https://eprint.iacr.org/2023/1717), IACR ePrint 2023/1717.
- Manevich, Meir, Elkhiyaoui, Tock, and Buzaglo, [Arma: Byzantine Fault Tolerant Consensus with Horizontal Scalability](https://arxiv.org/abs/2405.16575), arXiv:2405.16575, 2024.
- LFDT blog: [New major contribution to Hyperledger Fabric: purpose-built implementation for next-gen digital assets](https://www.lfdecentralizedtrust.org/blog/new-major-contribution-to-hyperledger-fabric-purpose-built-implementation-for-next-gen-digital-assets).
- [Fabric-X RFCs](https://github.com/hyperledger/fabric-x-rfcs).

# Closure

The proposal succeeds when:

- {NEW-NAME} is approved as an independent LFDT Incubation project with its own single-project charter and TSC.
- All project repositories, Go modules, container images, documentation sites and Discord channels have moved to
  the new name, with redirects and deprecation notices in place for the old ones.
- Downstream projects (Panurus, Fabric Smart Client, the Ansible collection, the block explorer) have adopted the new module paths.
- {NEW-NAME} and Fabric file separate TAC reports, each with a single lifecycle state.
- The Fabric charter and `GOVERNANCE.md` no longer reference Fabric-X.

In the longer term, the project aims to grow its contributor community under its own identity, reach production
deployments, and meet the criteria for Graduated status.

# Incubation Entry Criteria

## Maintainer Community

The project has 11 maintainers, listed under Effort and Resources and in each repository's `MAINTAINERS.md`. Four
were added in the first half of 2026. Many Fabric-X maintainers are also long-standing Fabric contributors and
maintainers.

## Community Calls

Fabric-X currently shares a monthly community call with Fabric, held on the third Wednesday of each month. After
the separation, {NEW-NAME} will hold its own monthly public community call covering development progress, roadmap
and releases.

## Community Communication

The project uses GitHub Issues and Discussions, RFCs in the [fabric-x-rfcs](https://github.com/hyperledger/fabric-x-rfcs)
repository, and LFDT Discord. The following Discord channels will be set up:

- {new-name}
- {new-name}-maintainers
- {new-name}-release

## Documentation

- Unified documentation site, architecture documents for each component, and API references.
- A 12-lesson deployment tutorial in the Ansible collection, plus recorded workshop videos.

## Test Coverage

- Unit and integration tests in every repository.
- End-to-end orderer and committer integration tests.
- Deterministic and randomized failure tests for the orderer.
- Test coverage reporting for the orderer.

## Roadmap

Development is tracked through GitHub Issues and the Fabric-X RFC process. A dated, consolidated roadmap will be
published after the separation and reviewed in community calls.

## CI/CD Pipeline & Release Process

- Pull requests require maintainer approval and passing CI (unit, integration and lint checks) before merging.
- Automated security and dependency scanning (CodeQL, Snyk, Dependabot).
- Releases are tagged with semantic versions. Binaries and container images are built and published automatically
  by GitHub Actions.
- A compatibility matrix across components is maintained.

## Licensing & IP

- Apache License 2.0 across all repositories.
- DCO sign-off on all commits.
