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

## LFDT Criteria for Project State Transition to Graduated

This section gives an overview to the topics that is defined by LFDT as [criteria for the project transition to Graduated state](https://lf-decentralized-trust.github.io/governance/governing-documents/project-incubation-exit/#introduction).

### Legal

All hiero-ledger repos score a **10/10** in License for OpenSSF scores.

Hiero adheres to the TAC’s repository structure guidelines by accurately displaying its license file, which is readily presented in each repository’s `README.md` file and easily linked when inspecting the GitHub Community Standards on GitHub’s Insights tab. Each repository is also displaying the Licence badge in the repo’s homepage to allow the community to visually find that information faster.

### Diversity

Hiero’s activities in GitHub (PRs, Issues, Reviews, Discussions, etc) are represented by 81 organizations and close to [800 contributors](https://insights.linuxfoundation.org/project/hiero/contributors?timeRange=custom&start=2024-09-01&end=2025-07-21&widget=organization-dependency) across all repositories. 
The following diagram shows the diversity of organisations contributing to Hiero:

<img width="580" height="547" alt="1" src="https://github.com/user-attachments/assets/ace75d29-9a9d-4212-99b9-b0ba0f00a3f1" />

The maintainer diversity keeps growing as we continue to promote the project and promote more adoption and participation.
The following diagram shows the diversity of maintainers contributing to Hiero:

<img width="589" height="364" alt="2" src="https://github.com/user-attachments/assets/0e9df6bb-937a-41ae-8b48-a8e4bdb4b604" />

These metrics were compiled utilizing [Bitergia](https://hashgraph.biterg.io) in conjunction with our `MAINTAINERS.md` information.
Currently, LFX Insights can identify contributors with a Maintainer role but cannot isolate metrics based solely on Maintainers.
It is presently capable of measuring only all participants (Contributors + Maintainers).
Our OpenSSF scores do not provide a score for Contributors, but we use other tools including Bitergia, `MAINTAINERS.md` and GitHub metrics to track participation.

A [support request](https://jira.linuxfoundation.org/plugins/servlet/desk/portal/4/SUPPORT-37059) has been initiated to facilitate the tracking of this information via LFX Insights.
As of today, the team reported that they will include this capability in the roadmap.

### Releases

The repositories `hiero-improvement-proposals`, `hiero-sdk-cpp`, `hiero-sdk-go`, `hiero-sdk-js`, `hiero-sdk-swift`, `hiero-sdk-tck` and `hiero-solo-action` have a “?” for packaging in OpenSSF score.
With the exception of `hiero-improvement-proposals` (which is a purely documentation based repo), our sdk repositories are producing consistent releases which are published as part of GitHub artifacts and even published to external artifact repositories like Maven Central or NPM.

Rest of the repos, score a **10/10** for packaging in OpenSSF score.

### Testing and Q/A

Hiero repositories have their CI running in GitHub Actions.
OpenSSF scores can track CI but at the moment, the cron is not displaying that particular score.
LFX Insights is able to track the quality of the releases and ensuring that the repos are able to release in a consisten maner and under a controlled process and tools under their [Build and Release tab](https://insights.linuxfoundation.org/project/hiero/security?timeRange=past365days&start=2024-08-19&end=2025-08-19).
At the moment, most scores are at **100%** in LFX insights with the exception of the `governance` and `hiero-improvement-proposals` which score 50% given that these repos are purely documentation or management.

The performance of the CI is monitored using the [GitHub Insights tool](https://github.com/orgs/hiero-ledger/actions/metrics/usage?dateRangeType=DATE_RANGE_TYPE_LAST_YEAR&tab=repositories), which provides data on usage metrics, performance metrics, and dependencies.
This tool also facilitates the tracking of open security advisories within these dependencies. 

As anticipated, the hiero-ledger core repositories exhibit the highest statistics in terms of workflows and run time since the project's transfer.
These repositories include: `hiero-consensus-node`, `solo`, `hiero-mirror-node`, `hiero-block-node`, `hiero-json-rpc-relay`, `hiero-local-node` and hiero sdk repositories.

In terms of performance, since the project and workflows were transferred, we have detected the following failure rate across our most active (core) repositories:

<img width="1419" height="899" alt="3" src="https://github.com/user-attachments/assets/19f5e731-482e-4c44-b064-2ffdd893c875" />

### Security

All repositories in hiero-ledger contain a visible and easily accessible link to `SECURITY.md` which can be found in the home page of the repo as well as the `README.md` file. This security file, adheres to the LFDT guidelines as it provides comprehensive information about the security team responsible for the project’s performance, instructions on how to file security issues privately and securely and guidelines for maintaining security standards.

Breakdown of OpenSSF scores for hiero-ledger code repositories:

| Repo                       | Dangerous Workflow | Token Permissions | Branch-Protection | Dependency-Update-tools | Fuzzing | Pinned-Dependencies | SAST | Security Policy | Signed-Releases | Vulnerabilities |
|----------------------------|--------------------|-------------------|-------------------|-------------------------|---------|---------------------|------|-----------------|-----------------|-----------------|
| `hiero-gradle-conventions`   | 10                 | 0                 | 4                 | -                       | 0       | 10                  | 10   | 10              | ?               | 10              |
| `hiero-json-rpc-relay`       | 10                 | 0                 | 4                 | -                       | 0       | 7                   | 3    | 10              | ?               | 0               |
| `hiero-local-node`           | 10                 | 9                 | 4                 | -                       | 0       | 10                  | 9    | 10              | ?               | 4               |
| `hiero-mirror-node`          | 10                 | 0                 | 5                 | -                       | 0       | 7                   | 8    | 10              | ?               | 8               |
| `hiero-mirror-node-explorer` | 10                 | 0                 | 4                 | -                       | 0       | 8                   | 10   | 10              | ?               | 9               |
| `hiero-sdk-cpp`              | 10                 | 10                | 4                 | -                       | 0       | 10                  | 9    | 10              | ?               | 10              |
| `hiero-sdk-go`               | 10                 | 10                | 4                 | -                       | 0       | 8                   | 9    | 10              | ?               | 10              |
| `hiero-sdk-java`             | 10                 | 0                 | 4                 | -                       | 0       | 9                   | 9    | 10              | ?               | 10              |
| `hiero-sdk-js`               | 10                 | 0                 | 4                 | -                       | 0       | 8                   | 9    | 10              | ?               | 0               |
| `hiero-sdk-python`           | 10                 | 0                 | 4                 | -                       | 0       | 6                   | 1    | 10              | ?               | 10              |
| `hiero-sdk-rust`             | 10                 | 0                 | 4                 | -                       | 0       | 6                   | 6    | 10              | ?               | 8               |
| `hiero-sdk-swift`            | 10                 | 10                | 4                 | -                       | 0       | 10                  | 6    | 10              | ?               | 10              |
| `hiero-sdk-tck`              | 10                 | 10                | 4                 | -                       | 0       | 7                   | 7    | 10              | ?               | 9               |
| `hiero-solo-action`          | 10                 | 0                 | 4                 | -                       | 0       | 5                   | 6    | 10              | ?               | 10              |

### Structure

All repositories in hiero-ledger comply with the TAC’s Common Repository Structure guidelines. This means that the repos have all the required information (license, openssf badge, community guidelines badge), recommended information (readme, contribution, changelog, notice, releases), and does not contain any prohibited executable files. 

Recently, we [submitted a request](https://github.com/LF-Decentralized-Trust/governance/pull/153) for the TAC to adopt the Github Community Standards as part of the tooling for verifying the repository structure.
This request was accepted and, at the same time, our hiero-ledger organization is verified to comply with these standards.

All our repos score a passing score **above 50%** in LFX Insights with the exception of `sdk-collaboration-hub` which scores 40% (inaccurate score).
While LFX is currently undergoing a testing process to ensure data accuracy, it also supports our structure compliance in the [Security and Best Practices Guidelines](https://insights.linuxfoundation.org/project/hiero/security?timeRange=past365days&start=2024-08-19&end=2025-08-19).
Please note that our `sdk-collaboration-hub` repository is flagged in LFX as containing executable files.
However, after diving into this information, we concluded that the repository does not contain any prohibited files or files with extended permissions.
A [ticket](https://jira.linuxfoundation.org/plugins/servlet/desk/portal/4/SUPPORT-37136) has been filed for the LFX team to verify the accuracy of the tool.

### Maintenance

All hiero-ledger repos score a **10/10** in Code Review for OpenSSF Standards.
`hiero-improvement-proposals` at the moment scores a 5/10 given the early stages of the project.
The project reflects PRs getting updated as frequently as hours ago and few times a week. 

The community driven bi-weekly calls are also growing in size.
At the moment, hiero is hosting community meetings every Monday through Thursday for every week:

| Community Meeting | Meeting occurrance link |
|-------------------|-------------------------|
| TSC meeting       | [LFX Calendar Link](https://zoom-lfx.platform.linuxfoundation.org/meetings/hiero?view=week)     |
| Community Call    | [LFX Calendar Link](https://zoom-lfx.platform.linuxfoundation.org/meetings/hiero?view=week)     |
| Python SDK        | [LFX Calendar Link](https://zoom-lfx.platform.linuxfoundation.org/meetings/hiero?view=week)     |
| Docs              | [LFX Calendar Link](https://zoom-lfx.platform.linuxfoundation.org/meetings/hiero?view=week)     |
| Solo              | [LFX Calendar Link](https://zoom-lfx.platform.linuxfoundation.org/meetings/hiero?view=week)     |
| Solo Action       | [LFX Calendar Link](https://zoom-lfx.platform.linuxfoundation.org/meetings/hiero?view=week)     |
| SDK               | [LFX Calendar Link](https://zoom-lfx.platform.linuxfoundation.org/meetings/hiero?view=week)     |

The goal is to be able to host a meeting per related component of the project to give the community the opportunity to participate. 

### Production

End-user organizations play a critical role in shaping the future of Hiero by providing real-world insights into how the technology is applied in practice.
Our June 2025 TSC elections attracted 50+ companies that [adopted the Hiero project](https://github.com/hiero-ledger/hiero/blob/main/ADOPTERS.md) and continue to participate in it.

### Documentation

Each repo in the `hiero-ledger` org contains a proper and complete `README.md` file with the badges and pointers of the information about the contents of the repo and with a section to provide guidance for new collaborators to get started into the project.
The documentation includes guidelines for collaboration and security protocols for private and secure report filing.

For every technical repository, we have also included additional information on how to install dependencies and/or prepare your workspace to be able to do internal testing. 

Our `hiero-docs` repo contains a link to each of our core repositories and SDK’s documentation which is hosted under [docs.hiero.org](https://docs.hiero.org).
This makes it easier for collaborators to find all the information they need in one single place. 

Additionally, we have our `hiero-website` repository which contains all the project information hosted in [hiero.org](https://hiero.org).
This site contains core information which is useful to attract first time collaborators, adopters and new users of the project.
We also have a blog section which gets updated with technical project updates and announcements. 

The community is invited to participate in two bi-weekly and monthly calls to contribute to and work on updates for each of these sites:
the Hiero Docs community call and the Hiero Website community call (see calendar).

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
