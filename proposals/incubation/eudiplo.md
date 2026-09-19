---
layout: default
title: EUDIPLO
parent: Incubation
grand_parent: Project Proposals
---

# Project Identifier

EUDIPLO Project Proposal v0.1

# Sponsor(s)

- **Primary Sponsor:** Mirko Mollik, Lead Maintainer — [mirkomollik@gmail.com](mailto:mirkomollik@gmail.com), GitHub: [@cre8](https://github.com/cre8)
- **Supporting Sponsor:** Lukas J. Han, Maintainer — [lukas.j.han@gmail.com](mailto:lukas.j.han@gmail.com), GitHub: [@lukasjhan](https://github.com/lukasjhan)

Mirko Mollik is the project's primary sponsor and principal active maintainer. The public [GitHub contributors overview](https://github.com/openwallet-foundation/eudiplo/graphs/contributors?all=1) shows both this central maintenance role and meaningful contributions by other developers. But it also shows the increased participation of other developers, fixing bugs or adding more features. The goal is to increase the number of active developers from different companies that are using EUDIPLO by themselves.

# Abstract

EUDIPLO is an open-source, self-hosted middleware that lets organizations issue and verify electronic attestations with EUDI Wallets through configuration-driven APIs. It abstracts the underlying wallet protocols and keeping deployment, data, and cryptographic keys under operator control.

# Context

EUDIPLO is an existing OpenWallet Foundation Growth project with an established codebase, public documentation, tagged releases, automated tests, and an active community. It is currently developed in the [openwallet-foundation/eudiplo](https://github.com/openwallet-foundation/eudiplo) repository and is proposed for transfer as part of the OpenWallet Foundation transition to LF Decentralized Trust.

The project addresses the European Digital Identity Wallet ecosystem established under the revised eIDAS framework. It implements open protocols and credential formats used between wallets, credential issuers, and relying parties, including OpenID for Verifiable Credential Issuance (OpenID4VCI), OpenID for Verifiable Presentations (OpenID4VP), Digital Credentials Query Language (DCQL), SD-JWT VC, ISO/IEC 18013-5 mdoc, and OAuth Token Status List.

EUDIPLO is not a wallet, identity provider, or business application. It is a protocol adapter that allows an existing backend to expose standards-based issuance and presentation flows without embedding the complete wallet protocol stack into that backend.

# Dependent Projects

EUDIPLO has no required dependency on another existing LF Decentralized Trust project and does not require changes to another LFDT codebase. Once the [identity common ts project](https://github.com/openwallet-foundation-labs/identity-common-ts) is also migrated to LFDT, it relies on it.

Where compatible LFDT components or libraries exist, the project will seek collaboration and reuse rather than duplicate lower-level implementations.

# Motivation

Organizations entering the EUDI Wallet ecosystem must implement a rapidly evolving set of protocols, credential formats, trust mechanisms, cryptographic operations, and security requirements. Implementing those capabilities separately in every public- or private-sector backend is costly, makes interoperability harder, and ties protocol support to the application technology stack. Proprietary wallet connectors can reduce that complexity but may introduce vendor lock-in, mandatory external services, or limited control over sensitive data and keys.

EUDIPLO provides a vendor-neutral alternative. An organization can run it on its own infrastructure and integrate through HTTP APIs, webhooks, and declarative JSON configuration. Credential definitions and presentation requests remain configuration rather than application-specific protocol code. This separation lets domain systems retain their business logic while EUDIPLO handles wallet-facing protocol behavior.

The project is differentiated by the combination of:

- configuration-driven issuance and verification;
- support for both issuer and verifier roles in one deployable middleware;
- self-hosting without a mandatory external SaaS dependency;
- protocol- and wallet-agnostic HTTP integration;
- modular database, storage, and key-management backends;
- multi-tenant administration and access control;
- automated tests and OpenID Foundation conformance testing; and
- practical tooling, including Docker deployment, a web client, a CLI, and generated API artifacts.

LFDT is an appropriate neutral home because EUDIPLO implements interoperable digital trust infrastructure, benefits from cross-organization governance, and complements LFDT's broader identity and trust ecosystem without being tied to a single vendor or national deployment.

# Status

**Proposed for Incubation.**

EUDIPLO is a mature, actively developed project rather than a new code proposal. Its current repository contains a substantial development history, regular tagged releases, public documentation, a contribution guide, a security policy, a technical charter, and an Apache License 2.0 license.

The initial maintainers are:

| Name | GitHub | Organization | Role |
| --- | --- | --- | --- |
| Mirko Mollik | [@cre8](https://github.com/cre8) | Common Codes GmbH | Lead Maintainer |
| Lukas J. Han | [@lukasjhan](https://github.com/lukasjhan) | Hopae S.A. | Maintainer |

The maintainers request reuse and transfer of the existing GitHub repository if the repository history satisfies LFDT's Developer Certificate of Origin requirements. A full DCO audit will be completed before migration. If reuse is not possible, the code will be imported using the repository process agreed with LFDT.

# Solution

## Scope

EUDIPLO provides middleware capabilities for organizations acting as credential issuers and relying parties. Its scope includes:

- creating and managing credential issuance configurations;
- executing authorization-code and pre-authorized-code issuance flows;
- issuing supported credential formats to compatible wallets;
- defining presentation requests using DCQL;
- creating same-device and cross-device presentation flows;
- validating wallet responses and presented credentials;
- notifying business backends through APIs and webhooks;
- managing tenants, service clients, roles, sessions, and operational configuration;
- integrating external attribute providers, authorization systems, storage, and key-management services; and
- providing administration, diagnostics, migration, and local demonstration tooling.

Application-specific eligibility decisions, source-of-truth data, user interfaces, and business workflows remain outside EUDIPLO and stay in the integrating system.

## Architecture

EUDIPLO is deployed as a standalone service between an organization's backend and EUDI Wallets:

1. The business backend requests an issuance or presentation operation through a simple API.
2. EUDIPLO creates and manages the corresponding standards-based wallet flow.
3. The wallet communicates with EUDIPLO using the supported OpenID protocols and credential formats.
4. EUDIPLO returns the result to the business backend through an API response, session status, or webhook.

The project is organized as a TypeScript monorepo and provides a backend service, web administration client, CLI, SDK/API artifacts, documentation, and deployment assets. Modules abstract database, file storage, and cryptographic key management so that operators can use lightweight local backends for development and production-oriented backends for deployment.

EUDIPLO does not create a blockchain or distributed ledger and does not define a consensus or network-participation protocol. Its interoperability boundary is the standardized HTTP exchange between issuers, relying parties, authorization systems, and wallets.

## Security and Privacy

EUDIPLO is designed for self-hosted deployment. Operators control where application data and cryptographic keys are processed and stored. Authentication and authorization protect administrative APIs, and the project supports tenant isolation and role-based access control. Pluggable key management allows development keys to be replaced by production key-management systems without changing the business integration.

The repository includes a public security policy and automated dependency and code-quality checks. Security-sensitive changes are covered by unit, integration, and end-to-end tests. The project intends to continue improving its OpenSSF Scorecard posture and software supply-chain controls under LFDT governance.

## Interoperability and Testing

The project maintains automated tests across issuance, presentation, credential formats, tenancy, persistence, and security-related flows. It has also been tested with OpenID Foundation conformance suites for OpenID4VCI and OpenID4VP. Wallet compatibility is documented and expanded through interoperability testing with independent wallet implementations.

Existing integrations use versioned configuration and API contracts. Breaking changes are documented in release and migration notes. The project uses semantic versioning and automated release processes to make upgrades predictable for operators.

## Adoption, Applications, and Use Cases

Publicly demonstrated application scenarios include:

- issuing electronic attestations from an existing citizen portal, education system, company registry, or other domain backend;
- requesting and validating wallet credentials as a relying party without implementing OpenID4VP in the business application;
- requesting an existing credential during issuance to support subject binding or attribute verification;
- operating a local interoperability sandbox for wallet, issuer, and verifier testing; and
- deploying the same middleware behind different application stacks through its HTTP interface.

EUDIPLO is discussed and demonstrated through OpenWallet Foundation community channels, including the Wallet Interoperability SIG, and the project operates a recurring public community call.

**TODO before submission:** Add publicly referenceable adopters, pilots, or evaluations that have agreed to be named. For each entry, identify the organization or project, whether the use is production, pilot, evaluation, or interoperability testing, and provide a public reference or contact that the TAC may verify.

| Organization or project | Type of use | Public evidence or contact |
| --- | --- | --- |
| German EUDI Wallet Playground | Demo showcasing, E2E Wallet testing | http://playground.eudi-wallet.org/ |
| [Raiffeisen Bank International](https://www.rbinternational.com/) | internal testing | approval to reach OWF grow stage |
| Intesi Group](https://www.intesigroup.com/) | customer projects | approval to reach OWF grow stage |
| espuni | Age Verification | https://app.espuni.com/en |

> Multiple companies in the German EUDI Wallet Sandbox where I do not have confirmation to name them

## License and Trademarks

The EUDIPLO codebase is licensed under the [Apache License 2.0](https://github.com/openwallet-foundation/eudiplo/blob/main/LICENSE). Documentation content identifies its applicable license separately. Third-party dependencies are managed through the project's package-management and automated dependency-review processes.

The EUDIPLO name and visual identity are used as project identifiers. Their continued use or transfer will follow applicable Linux Foundation Europe and LFDT trademark review. References to the “EUDI Wallet” describe the ecosystem and supported standards and do not imply endorsement by the European Union.

# Effort and Resources

The primary sponsor and current maintainers have committed to continuing technical leadership, review, releases, documentation, and community support during and after the transition. Additional developers already contribute through issues and pull requests, as reflected in the public [GitHub contributors overview](https://github.com/openwallet-foundation/eudiplo/graphs/contributors?all=1).

## Contributor Base and Community Growth

The project is currently maintained by a small core, with additional contributions from independent developers. A principal objective of joining LFDT is to turn this wider participation into a larger, sustainable, and organizationally diverse developer community.

Project roles will remain transparent and distinct:

- **Sponsors** explicitly endorse the proposal and support the project during the LFDT onboarding process.
- **Maintainers** accept ongoing responsibility for technical decisions, reviews, releases, security, and community governance.
- **Active developers** contribute code, tests, documentation, reviews, issue triage, release work, or other substantive technical work.
- **Adopters and community participants** provide implementation feedback, interoperability testing, use cases, and requirements.

Commit counts will not automatically confer sponsorship or maintainership. New sponsors will be named only with their consent. New maintainers will be selected based on sustained participation, technical judgment, review activity, reliability, and community trust, following documented project governance.

Within 12 months of LFDT onboarding, EUDIPLO aims to have at least five active human developers from at least three organizations, including at least two active developers who are not initial maintainers. For this measure, an active developer is a person who, during the preceding 12 months, has completed at least one merged code, test, or documentation contribution; performed substantive review work; or taken recurring responsibility for triage, releases, security, or another technical project function. Automated accounts are excluded.

The project will work toward this objective by maintaining approachable contribution documentation, labelling suitable onboarding issues, providing timely reviews, discussing roadmap items in public community calls, recognizing non-code contributions, and offering a documented path from contributor to maintainer.

The transition plan is:

1. Complete proposal review, organizational-affiliation confirmation, adoption references, and repository DCO audit.
2. Transfer or import the repository and associated project resources under the process agreed with LFDT.
3. Preserve release continuity, documentation, issue history, community channels, and contributor attribution during migration.
4. Align governance, security, release, and reporting practices with LFDT requirements.
5. Publish transparent contributor and maintainer criteria and actively onboard developers from additional organizations.
6. Continue protocol maintenance, interoperability testing, production-hardening, and community growth as ongoing work.

The project has no fixed completion date; it is maintained as long-lived infrastructure that tracks relevant standards and ecosystem requirements.

# How To

## Run a Local Demonstration

On Linux or macOS, the standalone CLI can install and start a local demonstration:

```shell
curl -fsSL https://eudiplo.dev/install.sh | bash
eudiplo demo
```

Alternatively, with Node.js 22.12 or newer:

```shell
npx @eudiplo/cli demo
```

The command creates editable demonstration configuration and starts the backend and web client with Docker Compose. The demonstration credentials are intended only for local evaluation.

## Build and Test from Source

```shell
git clone https://github.com/openwallet-foundation/eudiplo.git
cd eudiplo
corepack enable
pnpm install --frozen-lockfile
pnpm build
pnpm lint
pnpm test
```

Deployment instructions, API documentation, configuration examples, and architecture documentation are available at [docs.eudiplo.dev](https://docs.eudiplo.dev/). A working deployment exposes the configured administrative API and wallet protocol endpoints and completes the documented issuance and presentation test flows with a compatible wallet.

# References

- [EUDIPLO source repository](https://github.com/openwallet-foundation/eudiplo)
- [EUDIPLO documentation](https://docs.eudiplo.dev/)
- [EUDIPLO architecture](https://docs.eudiplo.dev/architecture/)
- [EUDIPLO supported protocols](https://docs.eudiplo.dev/reference/protocols/)
- [EUDIPLO wallet compatibility](https://docs.eudiplo.dev/getting-started/wallet-compatibility/)
- [EUDIPLO releases](https://github.com/openwallet-foundation/eudiplo/releases)
- [EUDIPLO security policy](https://github.com/openwallet-foundation/eudiplo/blob/main/SECURITY.md)
- [EUDIPLO contribution guide](https://github.com/openwallet-foundation/eudiplo/blob/main/CONTRIBUTING.MD)
- [OpenWallet Foundation project listing](https://tac.openwallet.foundation/projects/)
- [LFDT project lifecycle](https://lf-decentralized-trust.github.io/governance/governing-documents/project-lifecycle/)
- [LFDT project proposal process](https://lf-decentralized-trust.github.io/project-proposals/)

# Closure

EUDIPLO will be considered successful within LFDT when it provides a sustainably governed, interoperable, and production-capable integration layer for EUDI Wallet issuers and relying parties. Progress will be measured by:

- continued versioned releases with automated build, test, security, and release processes;
- maintained compatibility with the stable versions of the supported protocols and credential formats;
- repeatable interoperability with at least three independent wallet implementations;
- at least two publicly referenceable production or pilot deployments;
- at least five active human developers from at least three organizations within a rolling 12-month period, including at least two who are not initial maintainers;
- active maintainers drawn from multiple independent organizations, with a documented and evidence-based path from contributor to maintainer and toward the diversity required for Graduation;
- current deployment, API, security, and migration documentation; and
- satisfaction of the applicable LFDT Incubation Exit Criteria before requesting a separate Graduation review.
