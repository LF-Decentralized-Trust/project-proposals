---
layout: default
title: Hyperledger FireFly
parent: Graduated
grand_parent: Project Proposals
---

# Hyperledger FireFly Graduation Proposal

## Abstract

FireFly began as a [Hyperledger Lab in June, 2021](https://wiki.hyperledger.org/display/TSC/Table+consideration+of+the+FireFly+proposal+for+two+months) and became an [Incubating Project in September, 2021](https://wiki.hyperledger.org/display/TSC/Move+Hyperledger+Lab+Firefly+into+a+Project+in+Incubation). Now, after two years in Incubation FireFly has significantly grown and continued to mature. The project has received significant contributions from committers beyond the set of original maintainers, including a completely new [blockchain connector microservice](https://github.com/hyperledger/firefly-tezosconnect) and corresponding FireFly Core plugin enabling connectivity to Tezos, an entirely new type of blockchain. Additionally, the project now has a diverse set of maintainers representing three different companies.

Given that FireFly now meets or exceeds the [Incubation Exit Criteria](https://toc.hyperledger.org/governing-documents/project-incubation-exit.html) created by the Hyperledger TOC, we are proposing to move FireFly to Graduated Project status. The rest of this document describes in detail how the project meets or exceeds the Incubation Exit Criteria.

## Minimum requirements

### Legal

> All code has been made available under the Apache License and is free of incompatible dependencies
> Project name has been checked for trademark issues

Both of these requirements were met before FireFly moved in the Hyperledger Labs.

### Community support

> The project must have an active and diverse set of contributing members representing various constituencies

FireFly has a very active Discord channel where community members from all over the world regularly chat about project ideas, suggest improvements, ask technical questions, or seek troubleshooting assistance.

The community holds public Community Calls at least once a month where maintainers and contributors discuss architectural proposals, upcoming releases, and demo new features in the project.

> The project is not highly dependent on any single contributor (there are at least 3 legally independent committers and there is no single company or entity that is vital to the success of the project)

#### Committers

According to [LFX Insights](https://insights-v2.lfx.linuxfoundation.org/firefly/technical-contributors/participating-organizations?selectedDateFilterType=DATERANGE&selectedDateRangeKey=3Y), FireFly has 84 committers representing 8 corporations and 12 independent contributors.

#### Maintainers

FireFly has 12 maintainers representing three different companies:

- [Kaleido](https://kaleido.io/)
- [Fidelity](https://www.fidelity.com/)
- [OneOf](https://www.oneof.com/)

It is worth noting that each company has at least one maintainer who is a subject matter expert on one or more specific blockchain connectors, and the most foundational parts of the FireFly technology stack.

For the full list of maintainers, please see the [FireFly Maintainers page](https://wiki.hyperledger.org/display/FIR/Maintainers) in the Hyperledger Wiki.

#### Steering Committee

The FireFly Community is in active discussions of establishing a Steering Committee for the project itself. This would be a role for stakeholders who have a vested interest in the direction and the success of the project but are not necessarily writing or reviewing code on a daily basis. We have several Hyperledger Member companies that have expressed interest in being involved in the project in such a way including:

- [DTCC](https://www.dtcc.com/)
- [OneOf](https://www.oneof.com/)
- [Kaleido](https://kaleido.io/)

#### Maintainer Pipeline

The FireFly Community is actively working to continue to grow the FireFly technical contributors and maintainers through a Maintainer Pipeline. Pipeline activities range from working with organizations such as Grace Hopper Celebration to host open source contribution days, maintaining an active Discord channel, regular community calls, regular FireFly technical workshops, active plans to develop education/ workshop materials with local HL chapters and industry partners such as AWS, along with interactions with technical communities at major web3 community events such as EthDenver, EthCC, Consensus, Devconnect, etc. These pipeline activities aim to cultivate more technical contributions and maintainers from new organizations. We are pleased with the current continued growth in diversity in the project, and this "maintainer pipeline" will allow it to continue growing. Some examples of companies/organizations in various stages of this pipeline:

- [DTCC](https://www.dtcc.com/)
- [LACChain](https://lacnet.lacchain.net/firefly/)
- [CGI Federal](https://www.cgi.com/us/en-us/federal)

> Release plans are developed and executed in public by the community.

Upcoming FireFly feature releases are tracked with [GitHub Milestones](https://github.com/hyperledger/firefly/milestones) with individual work items being tracked in [GitHub Issues](https://github.com/hyperledger/firefly/issues). Releases are also discussed during regular Community Calls.

### Sufficient test coverage

> The project must include a comprehensive unit and integration test suite and document its coverage. Additional performance and scale test capability is desirable.

All code in FireFly Core, shared libraries, FireFly Transaction Manager, and production FFTM-based connectors have 100% unit test coverage.

| Repo | Description | Coverage |
| ------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`firefly`](https://github.com/hyperledger/firefly) | FireFly Core code repo | [![codecov](https://codecov.io/gh/hyperledger/firefly/branch/main/graph/badge.svg?token=QdEnpMqB1G)](https://codecov.io/gh/hyperledger/firefly) |
| [`firefly-common`](https://github.com/hyperledger/firefly-common) | Shared library for common code used across many FireFly microservices | [![codecov](https://codecov.io/gh/hyperledger/firefly-common/branch/main/graph/badge.svg?token=LUX2I5EU0T)](https://codecov.io/gh/hyperledger/firefly-common) |
| [`firefly-signer`](https://github.com/hyperledger/firefly-signer) | Both a runtime and library for Ethereum protocol specific code | [![codecov](https://codecov.io/gh/hyperledger/firefly-signer/branch/main/graph/badge.svg?token=OEI8A08P0R)](https://codecov.io/gh/hyperledger/firefly-signer) |
| [`firefly-transaction-manager`](https://github.com/hyperledger/firefly-transaction-manager) | Base library for building blockchain connectors | [![codecov](https://codecov.io/gh/hyperledger/firefly-transaction-manager/branch/main/graph/badge.svg?token=G6TaoNNBx9)](https://codecov.io/gh/hyperledger/firefly-transaction-manager) |
| [`firefly-evmconnect`](https://github.com/hyperledger/firefly-evmconnect) | Ethereum blockchain connector built on FireFly Transaction Manager | [![codecov](https://codecov.io/gh/hyperledger/firefly-evmconnect/branch/main/graph/badge.svg?token=OEI8A08P0R)](https://codecov.io/gh/hyperledger/firefly-evmconnect) |
| [`firefly-ethconnect`](https://github.com/hyperledger/firefly-ethconnect) | Legacy Ethereum blockchain connector | [![codecov](https://codecov.io/gh/hyperledger/firefly-ethconnect/graph/badge.svg?token=nO6ihSAzpV)](https://codecov.io/gh/hyperledger/firefly-ethconnect) |

- Some specific connectors (non FFTM-based), tooling, etc. may not have 100% unit test coverage, but test coverage is not allowed to decrease with any PR
- Every repo has some sort of automatic test validation that must occur before a PR can be merged
- FireFly has a comprehensive End-to-End test suite that runs against a live system in a robust matrix of possible configurations
- Both the unit test and E2E test suites run against every PR to FireFly Core
- The [FireFly Performance CLI](https://github.com/hyperledger/firefly-perf-cli) is used for testing transaction throughput of a live system in various configurations

### Sufficient user documentation

> The project must including enough documentation for anyone to test or deploy any of the modules.

The [FireFly Docs Site](https://hyperledger.github.io/firefly/) includes comprehensive information about the project. Each of individual microservice within FireFly may have specific information about that service in the `README.md` document in its corresponding GitHub repository.

### Alignment

#### Requirements fulfillment

> The project must document what requirements and use cases it addresses.

The [Understanding FireFly](https://hyperledger.github.io/firefly/overview/) section of the docs covers many topics including what FireFly is, the problems that it solves, and important general concepts within the project.

#### Architecture

> The project must document how it fits within the Hyperledger Architecture

Within the Hyperledger Architecture, FireFly is in the [Connectivity/Integration Gateway](https://www.hyperledger.org/projects/tag/connectivity-integration-gateway) category. The Docs Site has many details about what this means, including FireFly's [Web3 Gateway capabilities](https://hyperledger.github.io/firefly/overview/gateway_features.html) and platform capabilities for building [Multiparty Networks](https://hyperledger.github.io/firefly/overview/multiparty_features.html) powered by blockchains.

#### Compatibility with other Hyperledger projects

> Where applicable, the project should be compatible with other Graduated projects.

FireFly is complementary to all other Hyperledger projects. It also has specific _integrations_ with several including:

- Hyperledger Besu
  - FireFly has a robust Ethereum blockchain connector called [EVMConnect](https://github.com/hyperledger/firefly-evmconnect) which is frequently deployed with Besu blockchain nodes in a production enterprise deployments.
- Hyperledger Fabric
  - FireFly also has a Fabric blockchain connector called [FabConenct](https://github.com/hyperledger/firefly-fabconnect) for connecting to Fabric networks

Sometimes people in the community ask about the differences between Cacti and FireFly. We see both projects as being very complementary to each other, each with slightly different goals. Where Cacti seeks to create interoperability between different blockchains and focuses more on the "on-chain" aspect of interoperability, FireFly focuses more on being an application platform for blockchain applications. A major feature of this platform is coordinating "off-chain" data with "on-chain" events and data. While FireFly does let an application connect to multiple blockchains, its focus is not strictly to bridge or link data, events, or transactions between those different chains, but rather to provide a common platform to accelerate the development of blockchain applications.

#### Release numbering

> The project should use the Hyperledger standard release taxonomy, once that is agreed upon.

FireFly uses [Semantic Versioning](https://semver.org/) for all of its releases, including pre-releases.

#### Project must make a release, even a “developer preview”, before graduation.

To date, FireFly has had [43 releases](https://github.com/hyperledger/firefly/releases) (including release candidates).

### Infrastructure

> - Github repo has been created
> - Mailing lists have been created and are archived
> - Other communication means used, such as chat channels, are set up
> - Project is set up with Continuous Integration
> - All project repos have implemented the common repository structure

All of these requirements were met during the Labs phase.

### Security

> The project must identify key contact points to address security related questions and concerns.

Nicko Guyer, Peter Broadhurst and Andrew Richardson are the primary contacts for security questions or concerns. They may involve other maintainers in the discussion if it pertains to a certain subject matter areas within the project.

### OpenSSF Best Practices Badge

> A team seeking to graduate from Incubation shall have started the OpenSSF Best Practices Badge application and be nearly complete with incomplete badge requirements referenced in their graduation proposal. That does not mean the project must have 100% of all criteria, just 100% of the applicable criteria. This is to allow for projects such as test harnesses, that have “N/A” answers for questions that don't offer that as an option.

FireFly has a passing OpenSSF Best Practices badge

[![OpenSSF Best Practices](https://www.bestpractices.dev/projects/7826/badge)](https://www.bestpractices.dev/projects/7826)

## Additional considerations

In addition to the above, requirements such as the following may be defined at the onset of the project and considered as goals to be met to exit Incubation:

### Sufficient real world use

> The project should be used in real applications and not just in demos. Because not all real applications may be discussed publicly, in such cases statements providing as much details as possible should be made.

FireFly is being used in many production deployments such as:

- Synaptic Health Alliance: A coalition of US healthcare leaders (including Humana, Multiplan, UnitedHealth, Southwestern Health Resources, and more) leveraged Hyperledger FireFly to create a blockchain-based decentralized Provider Data Directory. This directory tackles the challenge of providing access to care via accurate provider data.
- The Institutes RiskStream Collaborative: The largest enterprise-level blockchain consortium in risk management and insurance uses Hyperledger FireFly for First Notice of Loss (FNOL) data sharing between companies, Mortality Monitor which offers a single source of digital decedent information required to process life insurance claims, Surety Bond Verification for Power of Attorney, and Licensing and Appointments micro credentialing.
- Swift: Using FireFly in its CBDC Sandbox for 18 central and commercial banks (including the Banque de France, the Deutsche Bundesbank, the Monetary Authority of Singapore, BNP Paribas, HSBC, Intesa Sanpaolo, NatWest, the Royal Bank of Canada, SMBC, Société Générale, Standard Chartered, and UBS) to collaborate to define the future of CBDCs in cross-border payments
- CGI Federal: Powering digital transformation in government with FireFly helping them break down data silos and enable collaboration in real-time for government agencies. Example projects include bringing auditability to the Department of Defense supply chain, tokenization of the space economy, securing metaverse assets, sharing healthcare data with zero trust, and enabling transparency and accountability in AI.
- DFCRC and Reserve Bank of Australia - CBDC Pilot for Digital Finance Innovation which tested 16 use cases with industry participants (including Mastercard, ANZ, Commonwealth Bank, Intuit, and more) to explore use cases and business models that could be supported by the issuance of a CBDC in Australia.
- OneOf: OnePlatform, a consumer engagement platform for enterprises featuring loyalty software, commerce engines, “digital twin” capabilities, and more
- AscendBit - AscendBit is a company owned by CP Group that is using Hyperledger FireFly to launch supply chain tracking initiatives, as well as its own company coin.
- LACChain is a blockchain infrastructure project designed for enabling inclusive and scalable projects and solutions on web 3.0 for Latin American and the Caribbean. FireFly is a key component of their tech stack and they have written up a tutorial for deploying FireFly onto LACChain.

It is worth noting that this is a list of projects that are publicly known to be using FireFly in production. There are additional significant proprietary projects that are not able to be listed here at this time.

### Sufficient scalability

> The project must demonstrate sufficient scalability and document its scalability over various dimensions

#### Transaction Throughput

Because FireFly is a modular, pluggable microservice architecture, there are an almost infinite number of variables involved in measuring or tuning performance and scalability. The biggest factor in transaction throughput usually ends up being the blockchain itself.

Independent testing by separate companies has concluded that FireFly does not create a bottleneck on transaction throughput above that of the blockchain itself.

#### Test Coverage

The test coverage requirement for firefly-core, firefly-common, firefly-transaction-manager, and firefly-evmconnect is 100% and this is enforced in Pull Requests. Other specific microservices may not have 100% coverage yet, but it is enforced that their coverage must not decrease with any code change.

## Conclusion

Given that FireFly meets the above requirements created by the Hyperledger TOC for a project to move from Incubation to Graduated status, we propose that FireFly be promoted to a Graduated Project.
