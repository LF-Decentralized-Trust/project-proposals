---
layout: default
title: PROJECT
parent: Hyperledger Improvement Proposals
---

# Sponsor(s)
- Alex Popowycz (Hedera) [<a@hedera.com>](mailto:a@hedera.com)
- Samson Goddy (Hedera) [<samson@hedera.com>](mailto:samson@hedera.com)
- Richard Bair (Hashgraph) [<richard@hashgraph.com>](mailto:richard@hashgraph.com)
- Leemon Baird (Independent) [<leemon@swirldslabs.com>](mailto:leemon@swirldslabs.com)
- Hendrik Ebbers (Hashgraph) [<hendrik.ebbers@hashgraph.com>](mailto:hendrik.ebbers@hashgraph.com)
- May Chan (HashPack) [<may@hashpack.app>](mailto:may@hashpack.app)
- Shyam Nagarajan (IBM) [<shyam@us.ibm.com>](mailto:shyam@us.ibm.com)
- Suma Nair (IBM) [<sumapnair@us.ibm.com>](mailto:sumapnair@us.ibm.com)
- Katerina Sanchez-Schilling (DLT Science Foundation) [<Katerina.Sanchez-Schilling@dltscience.org>](mailto:Katerina.Sanchez-Schilling@dltscience.org)
- Paolo Tasca (DLT Science Foundation) [<pt@dsf.xyz>](mailto:pt@dsf.xyz)
- Nikhil Vadgama (DLT Science Foundation) [<nv@dsf.xyz>](mailto:nv@dsf.xyz)

# Abstract
This proposal outlines the plan to move Hedera’s core network software to the Linux Foundation’s Decentralized Trust Foundation.
The Hedera network is a public distributed ledger technology (DLT) offering high throughput, low latency, and strong security.
We are requesting to contribute Hedera’s core network software which includes our unique hashgraph consensus algorithm
and related software and governance model to the Linux Fouundation's Decentralized Trust ecosystem.
We want to leverage and contribute to the existing community and resources for further development and adoption across
the Decentralized Trust ecosystem in a vendor-neutral process.
Under the new foundation, the project will be rebranded and trademarked as `PROJECT`. 

# Context
`PROJECT` offers a robust decentralized ledger platform leveraging a unique consensus mechanism known as Hashgraph,
which provides asynchronous Byzantine Fault Tolerance (aBFT), making it secure, fast, and fair.
By joining with the existing Hyperledger project under the umbrella of the Decentralized Trust Foundation,
`PROJECT` will aim to enhance collaboration with other blockchain and DLT projects,
contribute to the open-source community, and accelerate the adoption of enterprise-grade DLT solutions.

# Dependent Projects
None

# Motivation
Hedera envisions significant mutual benefits by donating the `PROJECT` codebase to LF Decentralized Trust.
Introducing Hedera's advanced consensus algorithm will create synergies between diverse blockchain technologies and
promote enhanced collaboration and integration both within and outside the LF Decentralized Trust Foundation.
Our contribution will enrich the array of open-source consensus mechanisms, bolstering the versatility and robustness
of its blockchain solutions.
Moreover, Hedera will contribute to ongoing standards development within the community, while also serving as a
vital link to the existing Hedera ecosystem and its Web3 developer community.
This collaboration with the Linux Foundation and its LF Decentralized Trust will also offer Hedera access to a broader
community of enterprise developers and valuable insights into incorporating open-source governance best practices.

Among the primary rationale for moving `PROJECT` to Linux Foundation’s Decentralized Trust includes:
- Enhanced Collaboration: Foster cross-community collaboration with other leading blockchain projects and leverage
  the existing Hyperledger community and governance framework.
- Increased Adoption: Accelerate enterprise adoption through Linux Foundation's established ecosystem and the
  opportunities presented by enhanced interoperability and purposeful standards .
- Resource Sharing: Benefit from shared development resources, tooling, and infrastructure provided by
  Linux Foundation’s Decentralized Trust.
- Vendor Neutrality: Ensure a vendor-neutral governance model that promotes equal participation from all
  community members, mitigating the risk of any single entity exerting undue influence over the project.
  This fosters a more open and inclusive environment, encouraging broader industry participation and trust in 
  the project’s development and deployment.

# Status
We acknowledge that all projects entering Hyperledger start with Incubation status.
`PROJECT` is a production-ready project with a robust 1.0 release, multiple production deployments, and a vibrant,
active community.
Our team has meticulously reviewed the Project Incubation Exit Criteria and believes we fulfill all the requirements
for Graduated status, with the exception of being onboarded onto Linux Foundation’s tools and build processes.
We are prepared to complete these steps promptly following an approval vote by the Technical Oversight Committee (TOC).
Once these final steps are completed, we believe the project will be ready for Graduated status and will apply for
this designation immediately.
We anticipate that this designation process will proceed swiftly if the TOC concurs that all criteria have been met.

# Solution
A `PROJECT` network is based on several individual components.
The following diagram gives an overview of all components that are needed to run a network and interact with the network.

![Components of a network](../assets/hedera-structure.svg "Components of a network")

The components shown in the diagram will be described in the following sections.

## Consensus Node
The Consensus Node is the core software that runs a `PROJECT` network like the Hedera public network.
The node is responsible for maintaining the public ledger, processing requested transactions, holding all accounts and other entities,
and running the Consensus Service, the Token Service, and the Smart Contract Service to fulfill service requests.
The node is written in Java and runs on the JVM.

## Mirror Node
The Mirror Node acts as a query node and stores historical data for the network.
The node consumes the transaction data provided by Consensus Nodes and may additionally provide value-added services
such as APIs, auditing, analytics, visibility services, security threat modeling, data monetization services, etc.
The node can also run additional business logic to support applications.

## Mirror Node Explorer
A visual Explorer interface built on top of a Mirror node providing a human interface for a network.

## Exchange Rate Tool
Tool to calculate and send the median of exchange rates from various exchanges to `PROJECT` network to
establish the cost of transactions.

## JSON-RPC-Relay
Allows Ethereum clients to interact with a `PROJECT` network.
This project is an implementation of the Ethereum JSON RPC APIs that delegates to both the
Consensus and Mirror Nodes to fulfill the JSON RPC Specification.

## Client SDKs (Java, JavaScript, Go, C++, Rust, Swift)
The SDKs for interacting with a `PROJECT` network: the official distributed consensus platform built using the
hashgraph consensus algorithm for fast, fair, and secure transactions.

## Solo
Solo provides a framework and associated tools for conducting end-to-end and full stack tests against a `PROJECT` network.

## Licenses and dependencies of the sub-projects
All sub-projects of `PROJECT` use the Apache license V2.0 (https://www.apache.org/licenses/LICENSE-2.0.txt).
Since all the subprojects are part of separate repositories and even created in different programming languages,
their dependencies differ. Based on that, it doesn’t make sense to provide a global list of dependencies.
All dependencies and related licenses can be identified by automatic project analysis.
Today, Snyk is used to create automatic dependency and license overviews of the subprojects.
The attached file [`dependencies-client-sdks.csv`](../assets/hedera-licenses-sdks.csv) contains a list of all
dependencies of our SDK projects.
Next to that, the attached file [`licenses.cvs`](../assets/hedera-licenses.csv) contains an overview of all licenses that
we found in dependencies of all sub-projects.
Linux Foundation can receive access to the Snyk reports of the projects or analyze them based on the LF tooling. 

# Effort and Resources
We propose the creation of the following projects and their repositories GitHub as the initial contributed projects:

- `https://github.com/PROJECT/SUBPROJECT` - This repository contains the gRPC Web Proxy that today can be found at https://github.com/hashgraph/hedera-grpcWeb-proxy
- `https://github.com/PROJECT/SUBPROJECT` - This repository contains the Exchange Rate Tool that today can be found at https://github.com/hashgraph/hedera-exchange-rate-tool
- `https://github.com/PROJECT/SUBPROJECT` - This repository contains the SDK TCK that today can be found at https://github.com/hashgraph/hedera-sdk-tck
- `https://github.com/PROJECT/SUBPROJECT` - This repository contains the Mirror Node Explorer that today can be found at https://github.com/hashgraph/hedera-mirror-node-explorer
- `https://github.com/PROJECT/SUBPROJECT` - This repository contains the Smart Contracts that today can be found at https://github.com/hashgraph/hedera-smart-contracts
- `https://github.com/PROJECT/SUBPROJECT` - This repository contains the JSON RPC Relay that today can be found at https://github.com/hashgraph/hedera-json-rpc-relay
- `https://github.com/PROJECT/SUBPROJECT` - This repository contains the Local Node that today can be found at https://github.com/hashgraph/hedera-local-node
- `https://github.com/PROJECT/SUBPROJECT` - This repository contains the Mirror Node that today can be found at https://github.com/hashgraph/hedera-mirror-node
- `https://github.com/PROJECT/SUBPROJECT` - This repository contains the Services that today can be found at https://github.com/hashgraph/hedera-services
- `https://github.com/PROJECT/SUBPROJECT` - This repository contains the JavaScript SDK that today can be found at https://github.com/hashgraph/hedera-sdk-js
- `https://github.com/PROJECT/SUBPROJECT` - This repository contains the Swift SDK that today can be found at https://github.com/hashgraph/hedera-sdk-swift
- `https://github.com/PROJECT/SUBPROJECT` - This repository contains the Rust SDK that today can be found at https://github.com/hashgraph/hedera-sdk-rust
- `https://github.com/PROJECT/SUBPROJECT` - This repository contains the Java SDK that today can be found at https://github.com/hashgraph/hedera-sdk-java
- `https://github.com/PROJECT/SUBPROJECT` - This repository contains the Go SDK that today can be found at
  https://github.com/hashgraph/hedera-sdk-go
- `https://github.com/PROJECT/SUBPROJECT` - This repository contains the C++ SDK that today can be found at https://github.com/hashgraph/hedera-sdk-cpp
- `https://github.com/PROJECT/SUBPROJECT` - This repository contains the Solo CLI that today can be found at
  https://github.com/hashgraph/solo

As shown, the Hedera ecosystem already contains several sub-projects that must be part of `PROJECT`.
All those sub-projects are necessary to deploy and run a full Hashgraph-based network and interact with that network.
All mentioned projects are currently part of the Hashgraph organization at GitHub.
Supplemental repositories include supporting tooling to deploy and validate a network built using the above codebases.
In addition to the aforementioned repositories and projects, the community and ecosystem around Hedera and its unique
hashgraph consensus algorithm is quite extensive, and we will want to transition a number of third-party projects
coming from the community as an initial step once `PROJECT` has been set up. 
An example of such a community project is https://github.com/OpenElements/hedera-enterprise.

## GitHub issues
The Hedera projects use GitHub issues today.
Together, the projects contain more than 1,000 open issues that contain information that should be preserved since they
contain great contributions from the community. Based on that, we propose to migrate the issues to the newly
created repositories.

## GitHub Actions 
Next to the issues, each of the repositories uses GitHub Actions for continuous integration.
While the GitHub Action workflow definitions are stored as part of the repository, we use custom action runners on
hardware in the Google Cloud.
The default GitHub action runners can not be used due to the complexity of `PROJECT`, especially for the services sub-project.
To continue the development of `PROJECT` based on best practices and continuous integration, we propose to set up
clones of the current hardware and action runners.
The Hedera Hashgraph projects define teams with specific authorities.
Those configurations should be migrated, and maintainers and committers for each sub-project should be defined.
The complete list of GitHub users that should be added as maintainers or committers to the
sub-projects will be submitted later.

## Documentation
The Hedera project provides a repository for the documentation of the Hedera network, including its deployment and
utilization of ever-evolving services.
That repository can be found at https://github.com/hashgraph/hedera-docs.
The content of the repository uses gitbook to create complete documentation that is currently hosted
at https://docs.hedera.com/hedera.
We propose to create a neutral hosted version of the documentation at https://docs.PROJECT.com, removing or modifying
existing content that is Hedera specific.
We will work on that directly after the setup to remove all those parts from the transited repository.

## DCO
We suggest setting up a DCO process by LFX for all `PROJECT` repositories.
The DCO documents will be based on the LF templates.
We will provide the final DCO documents separately.

## HIP
The https://github.com/hashgraph/hedera-improvement-proposal repository contains the Hedera improvement proposals (HIP)
of Hedera.
For `PROJECT` we need improvement proposals and a process for them, too.
Here, the HIP repo should be migrated to https://github.com/PROJECT/PROJECT-improvement-proposal.
Today a frontend showing all HIPs is hosted at https://hips.hedera.com/.
We propose to host a clone of that at https://NAME.PROJECT.com. 

## Build
As you can see in this chapter, `PROJECT` contains many sub-projects that need specific build steps and infrastructure.
Therefore, it is important to invest in `PROJECT`’s build, release, and deployment.
The goal must be to have a vendor-neutral build and release process led by LF.
We propose to nominate a release manager by LF who is involved in the project’s transition as soon as possible.

## Slack
With all the given sub-projects and the big community around `PROJECT`, it will be a must to have an open and easy way
to communicate with the community.
Therefore, we propose to create a `PROJECT` Slack.

## GitHub applications
We have several GitHub applications that are used in the repositories today.
We propose to migrate those applications with the repositories and check, as a step in the near future,
what can be replaced by LF best practices.

# How To
All repositories that should be transitioned to `PROJECT` have already defined an entire CI pipeline today.
As already mentioned, GitHub actions are used to run builds and tests for each pull request / commit in the projects.
Since the GitHub actions are part of the repositories the full build and test workflow of all projects is
already open today.
Since some projects have significantly more complex workflows regarding build and testing we will give some additional insights.

All projects are based on standards and best practices (Maven, Gradle, NPM, …) regarding the build process.
Based on that, each project can easily be built on a local machine.
We support Linux, macOS, and Windows as environments for most projects.
Only projects that already have a specific need based on their dependencies or programming language are more restricted.
An example is the Swift SDK, which needs macOS to be built.

The projects differ greatly in deployment and hosting, so `PROJECT` will contain libraries that are only
used as 3rd party dependencies in external projects next to full backend services and web applications.
Each project type is described in the sections below.

All projects provide GitHub actions for release automation.
That automation includes tagging the project, signing artifacts, and creating release notes.
Some of those steps need specific and secret environment variables like GitHub tokens.
All the tokens need to be created for the new repositories to support the release of the software.

## SDKs
All SDK projects and some other repositories provide workflows to deploy the build artifacts of a release to a global
registry, like Maven Central or NPM, which require accounts and tokens.
Here we propose to create new accounts and tokens in all needed registries to upload all releases done under `PROJECT`
in new namespaces of `PROJECT`.

## Consensus Node
The Consensus Node project defines the software that is running on each node of a network.
Today we do not have full open documentation about how a custom full network can be hosted and configured.
The Hedera Solo project (https://github.com/hashgraph/solo) provides a CLI based tooling to create a network with
the scope of temporal networks for testing but not with the scope of a long-running full network.
We will provide full documentation during the transition phase.

## Additional Services
A fully functional Hedera network today needs (at least) one hosted MirrorNode instance.
In addition, the JSON-RCP-Relay project and the MirrorNodeExplorer project provide artifacts that should be hosted in
combination with a running Hedera network.
Documentation for hosting and configuration of these services is part of the respective project repositories in GitHub:

### MirrorNode
- Documentation for hosting: https://github.com/hashgraph/hedera-mirror-node/blob/main/docs/installation.md 
- Documentation for configuration: https://github.com/hashgraph/hedera-mirror-node/blob/main/docs/configuration.md

### JSON-RPC-Relay
- Documentation for hosting: https://github.com/hashgraph/hedera-json-rpc-relay 
- Documentation for configuration: https://github.com/hashgraph/hedera-json-rpc-relay/blob/main/docs/configuration.md

### MirrorNodeExplorer 
- Documentation for hosting:  https://github.com/hashgraph/hedera-mirror-node-explorer?tab=readme-ov-file#run-in-kubernetes
- Documentation for configuration: https://github.com/hashgraph/hedera-mirror-node-explorer?tab=readme-ov-file#configuration

# References
- Hedera Documentation: https://docs.hedera.com/hedera (based on sources at https://github.com/hashgraph/hedera-docs).
- Description of Hedera and Hashgraph Technologies by Dr. Leemon Baird at Harvard: https://www.youtube.com/watch?v=IjQkag6VOo0
- The Hashgraph Consensus Algorithm: https://www.swirlds.com/downloads/SWIRLDS-TR-2016-01.pdf

# Closure
The successful migration of `PROJECT` to the Linux Foundation’s Decentralized Trust Foundation will be measured through
several key metrics and outcomes.

**Community Engagement and Growth**
- Increased contributions from a diverse set of developers and organizations.
- Active participation in discussions, issue reporting, and pull requests on GitHub.
- Growth in the number of maintainers and contributors over time.
- Number of new distributed applications running on the network.

**Adoption and Usage**
- The number of enterprises and projects integrating or deploying `PROJECT` technology.
- Case studies and success stories showcasing the practical applications and benefits of the technology.

**Release and Development Milestones**
- Successful completion of key development milestones and release of new versions.
- Adherence to project roadmaps and timelines, with transparent and regular updates to the community.

**Governance and Process Integration**
- Seamless integration into the Decentralized Trust Foundation governance model, including the establishment of a
  Technical Steering Committee (TSC) and adherence to its project lifecycle guidelines.
- Successful setup and use of Linux Foundation tools and processes, including CI/CD pipelines, issue tracking,
  and documentation hosting.

**Collaborative Efforts**
- Collaborative initiatives and synergy with the broader Decentralized Trust Foundation ecosystem.
- Contributions to and from other open-source projects, fostering a rich, collaborative environment.

By tracking these metrics and continuously engaging with the community, we can ensure that `PROJECT` thrives within
the Decentralized Trust Foundation, driving innovation and adoption in the distributed ledger technology space.
Any successive projects or additional initiatives stemming from this migration will be documented and tracked to ensure
ongoing success and impact.

