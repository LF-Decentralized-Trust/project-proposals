---
layout: default
title: Hiero
parent: Graduated
grand_parent: Project Proposals
---

# Overview

The Hiero Project, launched in September 2024, is an open-source initiative hosted under the Linux Foundation Decentralized Trust.
It originated from a significant codebase contribution by Hedera/Hashgraph, with the initial goal of providing a modular and verifiable codebase for DLT-based networks that enables decentralized and trust-based applications.
Hiero joined the LFDT to align with the mission of fostering transparency, interoperability, vendor neutrality, and trust in digital systems through community-driven governance and open collaboration.

By donating the code to The Linux Foundation, Hiero allows diverse stakeholders to contribute, govern, and drive the project in the open.
Hiero has made meaningful progress toward delivering pluggable, auditable components and supporting verifiable data infrastructure.
The project is building the foundations for decentralized identity, trusted transactions, and composable governance mechanisms,
which are essential to powering the next generation of decentralized applications.

As the project matures, Hiero is working toward establishing itself as a central component of the LFDT ecosystem.
The project's vision includes expanding its contributor and maintainer base, increasing interoperability with other decentralized technologies,
and promoting widespread adoption through real-world use cases.
Hiero seeks to enable a broader community of developers, enterprises, and public sector organizations to build systems of trust securely, transparently, and openly.

# Incubation Exit Criteria

The Hiero community has been working on the project’s incubation exit criteria as follows:

## Minimum Requirements

### Legal Obligations and Licensing

- All code is licensed under Apache 2, with the exception of “hiero-website”, whose code is developed under the MIT License. 
- Every repo created under hiero-ledger has a license badge displayed in its README.md file. This is a requirement for new repos to comply with the best practices requirements.
- GitHub community standards (within GitHub Insights) also add an additional layer of verification for the presence of the license in the code.

### Community Support

- The Hiero project's maintainer team has seen significant updates, including new members, restructurings, and role assignments.
  Several contributors have been granted both maintainer and committer roles in various repositories, demonstrating their active engagement and contributions. 
- The maintainers in the Hiero Ledger organization are primarily represented by contributors from Hashgraph, LimeChain, and others.
  Given that the majority of the project was originally donated by Hashgraph/Hedera, this distribution is to be expected at the moment, but the project is forecasting the adoption of new community-driven ecosystem repositories that leverage Hiero to drive their development which will attract new contributors and bring in new ideas. 
- The acquisition of new community-driven repositories enables us to host a range of community calls, office hours events, and taskforce sessions, all of which are updated publicly to attract new talent.
- The TSC members have also acquired three new members from different organizations to represent the project. Empowering additional organizations with governance opportunities helps to decentralize the project's direction and allows for a diverse range of perspectives to influence Hiero's trajectory.
  Over 50 companies were added to our list of [adopters](https://github.com/hiero-ledger/hiero/blob/main/ADOPTERS.md), and more than 100 active contributors participated in the voting for the Contributor Seat elections. 
- Hiero’s activities in GitHub (PRs, Issues, Reviews, Discussions, etc) are represented by 81 organizations and close to 800 contributors across all repositories. 

These updates reflect the growing adoption and participation in the project, as well as the ongoing efforts to expand and strengthen the project's contributor base.

### Test Coverage and Q/A

Hiero’s components form a modular architecture where consensus ensures trust, mirror nodes provide transparency, and local/solo nodes support flexible deployment and development.

The quality and reliability of these components are actively maintained by the core maintainers team, who ensure that all code changes adhere to established unit and integration testing standards.
These tests are integrated into GitHub Actions workflows, which automatically run on every new pull request.
This continuous integration setup helps safeguard against regressions, enforce consistent coding practices, and maintain overall system stability.
Additionally, the README.md files of the core repositories display the CI status badges, providing real-time insights into test coverage, code quality, and the health of the build pipeline.
This transparent approach reinforces confidence in the development process and highlights the team’s commitment to maintaining high engineering standards.

### User Documentation

Each repository within hiero-ledger includes a README.md file, providing essential information to facilitate contributor collaboration.
The community ensures these files are readily accessible and contain details pertaining to licensing, security status, environment setup instructions (if applicable), collaboration guidelines, and CI/CD pointers.

The community maintains the leading documentation site under the hiero-docs repo.
This documentation site collects information and tutorials that help new developers set up a Hiero-based network locally.
It also provides pointers to each of the SDKs and main components of the project, like Block Node, Consensus Node, JSON RCP Relay, Local Node, Node Explorer, and others. 

Additionally, the team maintains hiero.org, located in the hiero-website repository, where the community can find general information about the Hiero project and publish new content under the project’s blog site.
This platform is becoming a great tool for bringing in new developers and sharing technical information about the project.

### Alignment

The Hiero project demonstrates a strong commitment to its mission by building an open, decentralized, and verifiable credentialing infrastructure that empowers trust across institutions. 

Its governance ensures transparency, community-empowered development, and alignment with open source principles and best practices.
The project promotes collaboration and diverse participation through its open Technical Steering Committee (TSC), public working group meetings, and a growing ecosystem of contributors.

Hiero invests in real-world adoption by offering tools like custom GitHub Actions for integration tests, maintaining public documentation and tutorials at hiero.org and docs.hiero.org, and actively engaging with the community in public events.
This commitment to openness, interoperability, and usability reflects Hiero’s long-term vision to become a game changer of decentralized digital trust.

Hiero strives to promote and operate under the project’s open source best practices for collaboration.
These guidelines are public and available to the community to easily guide the collaboration between all parties involved. 

Periodic project updates and being publicised under the LFDT’s and Hiero blogs.
Additionally, the TSC meeting is undergoing a plan to offer project updates on a regular basis, which has already started with the first Solo Action project update.

New releases for each of the components are being produced on a weekly or regular basis, offering consumers detailed insights into the latest features and code fixes presented via their release notes.
The release news were also made public in the project’s community calls.

### Infrastructure

Hiero is hosted under the GitHub organization hiero-ledger.
The project consists of 28 code, administrative, and documentation repositories.
Each repository follows the guidelines for open source best practices as well as the GitHub guidelines for community standards. 

The hiero-ledger repositories contain accessible information for the community contributors, including license, contribution guidelines, security guidelines, readme, and collaboration instructions, reports of CI badges, reports of OpenSSF, and scoring details, as well as technical documentation. 

Hiero utilizes GitHub Actions for its CI, with workflows open for community contributions and enhancements.
Releases are publicly distributed: most components via GitHub artifacts, while always targeting a deployment at public repositories. 
For example, JAR artifacts through Maven Central, Python packages on pypi.org, and Rust-based artifacts on crates.io.

The Hiero project consistently publishes updates in both the LFDT blog and the hiero.org blog sites.
Additionally, new releases and project updates are made public in the project’s Discord announcements channel.
The project also runs topic-specific channels where contributors, collaborators, and maintainers can interact with each other.

The project’s open calendar offers audiences access to the TSC, community call, and project-specific weekly and bi-weekly meetings.
These meetings are open to everyone and recorded for audiences to access at their own time. 


### Security

The security vulnerability reporting guidelines are in place under the SECURITY.md in the root of the project.
Each individual hiero-ledger repository displays this information in its own README.md file alongside the project's best practices for collaboration.

The information for the project’s security team is also available in the same documentation.
Additionally, we have included instructions to help the community report security vulnerabilities safely.
Each repository in hiero-ledger has its security reporting channel enabled to allow contributors to report security vulnerabilities privately to the maintainers of the project.

For the CI/CD processes, the maintainers are also integrating tools such as Snyk and StepSecurity, which assist the project in reporting vulnerabilities through scheduled and triggered GitHub Actions workflows.


### OpenSSF Best Practices Badge

We have obtained the OpenSSF Best Practices Badge, which is available in the README.md file of each repo.
This project submission is continually updated as the project progresses.

We also follow all the recommendations in the LFDT TAC for Project Best Practices guidelines and structure. 

Hiero-ledger is also compliant with GitHub’s Insights Community Guidelines, which together complement the repo’s best practices for collaboration in open source. 

Overview of OpenSSF Scores for hiero-ledger repos:

| Project | Badge |
|--------|--------|
| hiero | [![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/hiero-ledger/hiero/badge)](https://scorecard.dev/viewer/?uri=github.com/hiero-ledger/hiero) |
| hiero-block-node | [![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/hiero-ledger/hiero-block-node/badge)](https://scorecard.dev/viewer/?uri=github.com/hiero-ledger/hiero-block-node) |
| hiero-consensus-node | [![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/hiero-ledger/hiero-consensus-node/badge)](https://scorecard.dev/viewer/?uri=github.com/hiero-ledger/hiero-consensus-node) |
| hiero-did-sdk-python | [![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/hiero-ledger/hiero-did-sdk-python/badge)](https://scorecard.dev/viewer/?uri=github.com/hiero-ledger/hiero-did-sdk-python) |
| hiero-docs | [![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/hiero-ledger/hiero-docs/badge)](https://scorecard.dev/viewer/?uri=github.com/hiero-ledger/hiero-docs) |
| hiero-gradle-conventions | [![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/hiero-ledger/hiero-gradle-conventions/badge)](https://scorecard.dev/viewer/?uri=github.com/hiero-ledger/hiero-gradle-conventions) |
| hiero-improvement-proposals | [![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/hiero-ledger/hiero-improvement-proposals/badge)](https://scorecard.dev/viewer/?uri=github.com/hiero-ledger/hiero-improvement-proposals) |
| hiero-json-rpc-relay | [![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/hiero-ledger/hiero-json-rpc-relay/badge)](https://scorecard.dev/viewer/?uri=github.com/hiero-ledger/hiero-json-rpc-relay) |
| hiero-local-node | [![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/hiero-ledger/hiero-local-node/badge)](https://scorecard.dev/viewer/?uri=github.com/hiero-ledger/hiero-local-node) |
| hiero-mirror-node | [![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/hiero-ledger/hiero-mirror-node/badge)](https://scorecard.dev/viewer/?uri=github.com/hiero-ledger/hiero-mirror-node) |
| hiero-mirror-node-explorer | [![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/hiero-ledger/hiero-mirror-node-explorer/badge)](https://scorecard.dev/viewer/?uri=github.com/hiero-ledger/hiero-mirror-node-explorer) |
| hiero-sdk-cpp | [![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/hiero-ledger/hiero-sdk-cpp/badge)](https://scorecard.dev/viewer/?uri=github.com/hiero-ledger/hiero-sdk-cpp) |
| hiero-sdk-go | [![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/hiero-ledger/hiero-sdk-go/badge)](https://scorecard.dev/viewer/?uri=github.com/hiero-ledger/hiero-sdk-go) |
| hiero-sdk-java | [![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/hiero-ledger/hiero-sdk-java/badge)](https://scorecard.dev/viewer/?uri=github.com/hiero-ledger/hiero-sdk-java) |
| hiero-sdk-js | [![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/hiero-ledger/hiero-sdk-js/badge)](https://scorecard.dev/viewer/?uri=github.com/hiero-ledger/hiero-sdk-js) |
| hiero-sdk-python | [![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/hiero-ledger/hiero-sdk-python/badge)](https://scorecard.dev/viewer/?uri=github.com/hiero-ledger/hiero-sdk-python) |
| hiero-sdk-rust | [![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/hiero-ledger/hiero-sdk-rust/badge)](https://scorecard.dev/viewer/?uri=github.com/hiero-ledger/hiero-sdk-rust) |
| hiero-sdk-swift | [![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/hiero-ledger/hiero-sdk-swift/badge)](https://scorecard.dev/viewer/?uri=github.com/hiero-ledger/hiero-sdk-swift) |
| hiero-sdk-tck | [![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/hiero-ledger/hiero-sdk-tck/badge)](https://scorecard.dev/viewer/?uri=github.com/hiero-ledger/hiero-sdk-tck) |
| hiero-solo-action | [![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/hiero-ledger/hiero-solo-action/badge)](https://scorecard.dev/viewer/?uri=github.com/hiero-ledger/hiero-solo-action) |
| hiero-website | [![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/hiero-ledger/hiero-website/badge)](https://scorecard.dev/viewer/?uri=github.com/hiero-ledger/hiero-website) |
| sdk-collaboration-hub | [![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/hiero-ledger/sdk-collaboration-hub/badge)](https://scorecard.dev/viewer/?uri=github.com/hiero-ledger/sdk-collaboration-hub) |
| solo | [![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/hiero-ledger/solo/badge)](https://scorecard.dev/viewer/?uri=github.com/hiero-ledger/solo) |

## Additional Considerations

### Real World Use

While the Hiero Project is still in the early stages of development and brand neutralization, it has already gained attention through several real-world pilot applications and early adoption scenarios.
Some examples include:

- **Hedera:** The [Hedera network](https://hedera.com/) is one of the most prominent public ledgers.
  Since February 2025, all instances of Hedera are 100% based on Hiero.
  With that, all projects in the Hiero ecosystem are compatible with Hedera.
  Libraries and applications created for Hedera can often be easily modified to be product agnostic and work with any Hiero-based network.
  In the last month, we onboarded such projects to Hiero [with more to be onboarded in the near future](https://github.com/hiero-ledger/tsc/issues?q=is%3Aissue%20state%3Aopen%20label%3A%22project%20proposal%22).
- **HashSphere:** The [HashSphere](https://www.hashgraph.com/hashsphere/) product of Hashgraph allows everybody to host a private, permissioned network built using the Hiero open-source codebase.
  It’s designed for enterprises and institutions that need localized control, tailored governance, and the ability to run a Hedera-compatible distributed network in private or sovereign environments.
  HashSphere maintains compatibility with Hiero - and therefore with Hedera’s mainnet - for hybrid use cases, allowing organizations to deploy trusted infrastructure without relying exclusively on a public ledger.

Next to full networks, a diverse set of libraries, tools, and applications already depend on Hiero. The given sample stands for a huge list of products that are compatible with any Hiero-based network. While many projects initially focused on Hedera as a primary use case, Hiero is gaining adoption as a standard within these products. We anticipate that a broader range of future projects will offer general support for Hiero.

- **Hgraph:** With Enterprise grad APIs and Mirror Node hosting Hgraph, provide support for any Hiero-based network.
  The company recognized the benefits of Hiero from the project's inception and facilitated our progress.
  Today, Hgraph is an active participant on the Hiero TSC.
- **Hashgraph Online:** The tooling of Hashgraph Online is based on the consensus service of Hiero.
  It provides On-chain file storage and a content-addressed retrieval system, next to other functionality on top of every Hiero-based network.
  Like Hgraph, Hashgraph Online is present and active on the Hiero TSC.
- **HashPack:** As one of the main wallets of the Hedera ecosystem, HashPack is not only a gateway to the Hedera network but to any Hiero-based network.
  HashPack is investing in Hiero and is interested in supporting any network based on our standards.

### Ease of Use and Consumption

Hiero is designed with ease of use and seamless integration in mind, making it highly accessible for developers and organizations alike.
The project’s intuitive APIs and streamlined data model simplify the process of recording and verifying trust-related events, and at the same time reduce the overhead typically associated with distributed ledger technologies.
Hiero enables systems to interact with decentralized trust data without needing to manage a complex blockchain infrastructure.
This approach makes it ideal for projects seeking transparency, auditability, and interoperability without compromising performance or usability.

To support adoption and rapid education, Hiero offers comprehensive online tutorials and technical documentation at docs.hiero.org, helping new users and contributors to get started.
In addition, the project actively engages with the community through recent and upcoming seminars presented at LDFT conferences, offering hands-on demonstrations, real-world use cases, and opportunities to connect with the developers and contributors behind the technology.

### Standardization

Hiero-ledger repositories conform to the LFDT’s TAC guidelines for best practices.
The team continues to work on improving the quality of the code and security guidelines. 

LFX Insights offers a new Quality and Best Practices Meter that enhances code quality and security scans by incorporating best practices compliance checks and security checks, helping maintainers identify potential vulnerabilities.

The Hiero-ledger repositories adhere to GitHub’s guidelines for community standards, which the TAC recently adopted as a tool to verify code quality and structure.

Additionally, the project continues to work on its continuous efforts to seek vendor neutrality in the codebase. This initiative will be reflected in the project through:

- Improved community trust and broader participation.
  By moving away from the Hedera namespace, we will encourage more community and contributor participation in the project and promote adoption.
- Governance aligned with Open Source best practices.
  The project is governed by a neutral community-driven model that is responsible for making decisions in the direction of the project and influencing its overall development.
  This will also reflect in added transparency in decision-making and roadmap direction.
- Interoperability and participation with other projects in the ecosystem.
  Vendor neutrality will contribute to better integration across multiple platforms and technologies.
  This will reflect in adoption across industries, collaboration with other projects in the ecosystem, and overall project trust. 

### Graduation Benefits for Community

Hiero consistently delivers new releases and publications suitable for production environments.
As the project progresses towards complete vendor neutrality, achieving graduation status will enhance its reliability for consumers and boost confidence in contributions toward this objective. 

Over the past year, Hiero has gained significant exposure through various global events.
We remain committed to delivering in-person presentations and updates at key LFDT events.

The project’s mature status will enable us to attract new and diverse talents, as well as new adopters, with the goal of developing leaders and core maintainers across each component.
