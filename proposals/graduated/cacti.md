---
layout: default
title: Hyperledger Cacti
parent: Graduated
grand_parent: Project Proposals
---

# Overview

Hyperledger Cacti was [created in late 2022](https://www.hyperledger.org/blog/2022/11/07/introducing-hyperledger-cacti-a-multi-faceted-pluggable-interoperability-framework) as a merger of two mature projects:
- Cactus, which started its open source journey in 2020, and
- Weaver Lab, which started its open source journey in 2021.
Over the past year, the Cactus and Weaver code bases and CI pipelines have been integrated, and packages released under a common Cacti namespace, following Hyperledger release and versioning guidelines. The project has created a vibrant community around the topic of interoperability, its code has been used (and its designs have been validated) in several real world use cases by business consortia, especially in CBDC applications, and it has acquired a high profile in the blockchain/DLT community through articles, research papers, talks, and panel discussions. As a full-featured generic interoperability framework and toolkit designed to be extensible, Cacti is ready to be a graduated Hyperledger project.

# Incubation Exit Criteria

We describe how Cacti fulfils Hyperledger's graduation criteria below.

## Minimum Requirements

### Legal Obligations and Licensing

- All code is licensed under Apache 2: [see here](https://github.com/hyperledger/cacti#readme)
  * Both Cactus and Weaver complied with this as Hyperledger Labs, before the creation of Cacti
- Additionally: there is a check (for licenses) configured in `package.json` files for NPM packages
  * Mandatory for PRs to pass

### Community Support

- Active maintainers from three major companies: Accenture (3), Fujitsu (2), IBM (2)
- Diverse code contributions:
  * 79 unique contributors since the project’s inception
  * 10-15 making substantial contributions
  * No single company or maintainer dominating
  * PR submissions and reviews balanced across maintainers
- Public maintainers’ call held every week with active participation
  * Recordings uploaded on YouTube
- Cacti Discord channels, especially #cacti-users and #cacti-contributors, have high volumes of activity
- Usage: 235 forks, 276 stars
  * Last 2 weeks: 12641 clones with 581 unique cloners, 5523 views with 350 unique visitors
- Popular target for candidate Hyperledger Mentees
  * 5 in 2023, 5 in 2022, 2 in 2021

### Test Coverage and Q/A

- Unit tests configured for all individual packages and modules, and integration tests for protocols and examples
  * Configured as GitHub Actions, mandatory for PRs to pass
- Currently we don’t have a unified test coverage report, but we are planning to generate a table with coverage for each package listed

### User Documentation

- Usage and tutorial documentation exist for the Cactus and Weaver packages respectively
  * Instructions to build and deploy (through a local web server) exist
  * Contain details of setups, prerequisites, installations, and evaluations (end-to-end sample runs)
- An integrated Cacti documentation website with tutorials and reference information is in the works
  * Built according to Tracy’s mkdocs template
  * Publish trigger will be configured through a GitHub Action
- Copious documentation of modular specifications and example use cases exist
  * Cactus whitepaper
  * Weaver RFCs

### Alignment

- The goals, mission, and use case scenarios addressed by Cacti are amply documented in README files as well as in the whitepaper, RFCs, and tutorial docs
- As a project [designed to promote and enable interoperability](https://github.com/hyperledger/cacti#scope-of-project), Cacti conforms to, fulfils, and augments, the Hyperledger architecture and mission
  * Not just compatible with, but also enhances the capabilities of Hyperledger blockchain technologies like Fabric, Besu, Sawtooth, and Iroha, by making cross-network transactions possible and seamless, and without impacting the networks’ internal operations
  * Also supports non-Hyperledger DLTs like R3 Corda (and Polkadot), allowing Hyperledger blockchains to be interoperable with non-Hyperledger systems without internal modifications
  * Will use Caliper for performance benchmarking and ensure interoperability with Firefly in the future
- Periodic releases have been made, with 2.0.0-alpha.1 the current one (2.0.0-final targeted soon)
* Uses Hyperledger standard release taxonomy
* GitHub actions configured to publish packages in various languages (JS, Go, Java, Rust) and triggered by tagging a given commit with an updated version as label

### Infrastructure

- We fulfilled all the requirements when Cactus and Weaver Lab existed as separate projects: GitHub repositories, mailing lists, calendars, Discord channels, CI pipelines, and sensible repository structures with easy navigability
- The merge of the two code bases into a new Cacti repository was seamless, and also fulfils the infrastructural requirements
  * [Repository location](https://github.com/hyperledger/cacti)
  * Commit histories of the two projects were merged chronologically
  * Weaver code was migrated to a subfolder within Cacti
  * CI pipelines were integrated, and the packages were published under a common Cacti namespace
  * Mailing lists, calendars, and Discord channels were renamed while inheriting the communication history
  * We are making steady progress with “deeper” integration, which will happen incrementally in each new release, using the [integrated architecture](https://github.com/hyperledger/cacti/blob/main/ROADMAP.md#cacti-v2) as the aspiration
- We produced (in collaboration with the LF) an exhaustive [checklist](https://wiki.hyperledger.org/display/CA/Merging+Projects+Checklist) for project merging that is also on the Hperledger Wiki for other projects to use in the future

### Security

- Security vulnerability reporting guidelines are in place: SECURITY.md in the root folder of the Cacti repository
  * This states the last agreed-upon Hyperledger security policy
  * Whenever the new security policy and reporting template are finalized by the TOC, this file will be replaced accordingly
- SPOC for security reporting: Peter Somogyvari (maintainer)
  * Subscribed to security mailing list
  * Participates in Hyperledger Foundation security discussions
  * Extra SPOCs will be identified from the maintainers once the new policy is framed

### OpenSSF Best Practices Badge

- We have obtained the OpenSSF Best Practices Badge: [see here](https://github.com/hyperledger/cacti#readme)
- We also follow all the recommendations in the Hyperledger TOC’s [Project Best Practices guidelines](https://github.com/hyperledger/toc/blob/gh-pages/guidelines/project-best-practices.md)

## Additional Considerations

### Real World Use

- Fujitsu, together with ConsenSys, R3 and Soramitsu, has delivered a PoC of a cross border securities settlement system launched by Asian Development Bank (ADB)
  * Use cases: securities DvP across Permissioned Ethereum, Corda (via Web API) and Iroha ledgers
  * Reference links: https://www.adb.org/publications/market-infrastructures-asean3-project-tridecagon, https://www.fujitsu.com/global/about/resources/news/press-releases/2023/0615-02.html, https://www.fujitsu.com/global/about/research/article/202306-connectionchain-casestudy-adb.html
- IBM delivered a PoC for Banque de France (BdF) and HSBC in the form of an experimental CBDC application suite built under the Digital Euro initiative.
  * Use cases: data-sharing and DvP across Fabric and Corda ledgers
  * Presented at the CBDC Workshop in HGF 2022.
  * Reference links: https://www.finextra.com/newsarticle/39417/banque-de-france-demos-ledger-interoperability-in-cbdc-trials, https://www.gbm.hsbc.com/en-gb/feed/innovation/the-interoperability-of-cbdcs-across-networks-and-currencies
- IBM built a DvP (atomic swap) demo between a Casper Labs network and a Fabric network
  * Demonstrated in the Blockchain Hub in Davos in 2022
  * Presented at HGF 2022 
  * Reference link: https://www.casperlabs.io/blog/casperlabs-x-ibm-demo-at-the-blockchain-hub-davos-2022
- Climate Action and Accounting SIG: used Fabric and Besu/Quorum connectors

### Ease of Use and Consumption

- Modular code and composable scenarios
- Plugin-based architecture
- Components can be downloaded and imported directly or built locally from source
  * Docker images, libraries maintained in NPM/Go/Maven/Crate registries
  * Clear instructions and scripts to build locally or to import and run

### Scalability

- Interoperability enabled through a combination of:
  * REST APIs
  * In-network apps running on unmodified DLT stacks
  * External components incurring minimal processing overhead and trust footprint
- We have not conducted formal benchmarking studies yet
  * There is an ongoing mentorship project around benchmarking bridges, which will help benchmark Cacti components and end-to-end protocols
- But we believe that the Cacti framework and toolkit is intrinsically scalable
  * APIs are designed to be horizontally scalable
  * Informal TPS and latency measurements of relay modules indicated that they were not the bottlenecks in cross-chain communications
  * Cacti is just the glue between DLT systems that have their own scalability challenges

### Standardization

- We are closely involved and aligned with standardization efforts
- Maintainers and long-time contributors are actively involved in open community (and academic) efforts to create standards around DLT interoperability
- There is an official IETF Working Group that was established in early 2023
  * _Title_: Secure Asset Transfer Protocol (SATP)
  * Authorized to draft RFCs
  * Cacti maintainer (Ramakrishna) and contributor (Rafael Belchior) are active participants and draft co-authors
  * Early version of the protocol (then called ODAP) spec was implemented in Cactus by Rafael and Andre Augusto as the [odap-hermes plugin](https://github.com/hyperledger/cacti/tree/main/packages/cactus-plugin-odap-hermes)
  * Latest version of the SATP protocol is [being implemented](https://wiki.hyperledger.org/display/INTERN/Cacti%3A+Implement+Standardized+Secure+Asset+Transfer+Protocol) using relays by Hyperledger Mentee (Zakwan Jaroucheh)
- Another standards’ forum: [SODA Inter-Op Group](https://sodapublicmoney.org/the-interoperability-group/): focused on high-level APIs and legal/regulatory aspects
  * Ramakrishna and Hart Montgomery are participants
- As we are embedded in this ecosystem, we will ensure that Cacti code conforms to emerging standards created through community consensus, increasing Cacti’s visibility and value in the community

### Graduation Benefits for Community

- Code is already suitable for production usage, to integrate and couple DLT systems in different modes
  * Proven by real world usage
- Graduated status will give enterprises and DLT providers looking for generic interoperation tools
  * A canonical location to look for those tools or to co-develop or contribute features
  * More confidence in the maturity of the Cacti code base
- New contributors will be more enthusiastic about using as well as contributing (we have received communication of interest)
- A graduated Cacti project can create a fulcrum of innovation in the interoperation area within Hyperledger
  * Act as a reference for other interoperation projects like Yui and Harmonia Labs, and also related projects like Firefly
