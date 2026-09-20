---
layout: default
title: Identity Common TypeScript
parent: Incubation
grand_parent: Project Proposals
---

# Project Identifier

Identity Common TypeScript Project Proposal

# Sponsor(s)

- Mirko Mollik, Common Codes, GitHub: [@cre8](https://github.com/cre8),
- Timo Glastra, Animo, GitHub: [@TimoGlastra](https://github.com/TimoGlastra)
- Berend Sliedrecht, Animo, GitHub: [@berends](https://github.com/berendsliedrecht)
- Henrique Dias, Animo, GitHub: [@henriquedias](https://github.com/hacdias)
- Lukas Han, Hopae Inc., GitHub: [@lukasjhan](https://github.com/lukasjhan)

The Identity Common Typescript is a monorepo for multiple reusable TypeScript libraries that merged multiple projects in the last days, so there may be more supporters.

# Abstract

Identity Common TypeScript is a vendor-neutral monorepo of reusable TypeScript libraries for digital identity. It provides tested implementations of OpenID4VC, SD-JWT, mdoc, DCQL, trust and status lists, cryptography, and EUDI-specific formats for Node.js, browsers, and React Native. The goal is to provide a solid layer of reusable TypeScript libraries for the digital identity ecosystem.

# Context

Identity Common TypeScript is an existing [OpenWallet Foundation Labs repository](https://github.com/openwallet-foundation-labs/identity-common-ts). It was created to provide shared types, utilities, and standards implementations for identity projects without forcing each project to maintain overlapping foundational code.

The monorepo consolidates packages and development history from earlier OpenWallet Foundation projects, including `sd-jwt-js`, `mdoc-ts`, `dcql-ts`, and `oid4vc-ts`, alongside newer common, cryptographic, status-list, trust-list, signature, and EUDI-specific packages. Consolidation gives these related libraries a consistent build, testing, release, dependency-management, and contribution model while retaining independently versioned package families.

The project implements specifications used in digital credentials and wallet ecosystems, including OpenID for Verifiable Credential Issuance, OpenID for Verifiable Presentations, SD-JWT and SD-JWT VC, ISO/IEC 18013-5 and 18013-7 mobile documents, Digital Credentials Query Language, CBOR Object Signing and Encryption, OAuth Token Status List, European trusted-list formats, and related ETSI and EUDI formats.

Identity Common TypeScript is a library project. It does not define a blockchain, distributed ledger, consensus mechanism, hosted identity service, or end-user wallet.

# Dependent Projects

Identity Common TypeScript has no required dependency on another LF Decentralized Trust project and does not require changes to another LFDT codebase. It uses open standards and ordinary open-source package dependencies.

Several package families originated in earlier OpenWallet Foundation repositories. Those repositories are predecessor codebases rather than runtime dependencies. Projects that consume Identity Common TypeScript packages may continue to adopt releases independently through npm.

Where compatible LFDT libraries exist, the maintainers will coordinate interfaces, share conformance findings, and prefer collaboration over unnecessary duplication.

# Motivation

Digital identity implementations repeatedly need the same low-level capabilities: standards-compliant serialization, cryptographic helpers, selective-disclosure processing, mobile-document handling, credential-status validation, authorization flows, query evaluation, trusted-list processing, and common protocol types. Reimplementing these capabilities in every issuer, verifier, and wallet increases maintenance cost, fragments interoperability behavior, and makes security fixes harder to distribute.

Identity Common TypeScript provides a shared, vendor-neutral foundation. The packages are small enough to be adopted independently while the monorepo supplies common engineering controls and makes cross-package compatibility visible. Applications can use stable library APIs instead of copying protocol code or depending on a hosted service. Platform-neutral design allows the same core behavior to be used in Node.js services, modern browsers, and React Native applications.

The project is differentiated by the combination of:

- one coherent TypeScript workspace spanning credential formats, wallet protocols, trust, status, and cryptographic building blocks;
- independently versioned package families so consumers can adopt only the capabilities they need;
- shared quality, release, documentation, and dependency-management practices;
- portability across server, browser, and mobile JavaScript environments;
- continuity for widely used OpenWallet Foundation TypeScript libraries that previously lived in separate repositories; and
- an Apache-2.0, vendor-neutral implementation intended for reuse by wallets, issuers, verifiers, middleware, test tools, and other identity infrastructure.

LFDT is an appropriate neutral home because the project provides interoperable digital trust infrastructure, benefits from multi-organization governance, and can serve several projects without being controlled by a single product vendor.

# Status

**Proposed for Incubation.**

Identity Common TypeScript is an active implementation rather than a new code proposal. The repository contains multiple published package families, tagged releases, automated checks, public documentation, a contribution guide, a security policy, Changesets-based release management, and an Apache License 2.0 license. As of September 2026, the repository publishes separate release lines for the common packages, SD-JWT, mdoc, DCQL, and OpenID4VC packages.

The repository currently assigns code ownership to the [OpenWallet Foundation Labs `identity-common-ts-maintainers` team](https://github.com/openwallet-foundation-labs/identity-common-ts/blob/main/CODEOWNERS).

The roster and affiliations will be confirmed in a public `MAINTAINERS.md` before TAC approval. This will make present responsibility auditable and demonstrate the organizational diversity required for Incubation. Historical commits or inclusion in the contributor graph will not, by themselves, confer maintainer status.

The maintainers request reuse and transfer of the existing repository and its history if it satisfies LFDT's Developer Certificate of Origin requirements. Because the monorepo incorporates history from predecessor projects, a complete DCO audit will be performed before migration. The maintainers can guarantee that the DCO requirements from the merged projects was met since this was a requirements for projects from the OWF.

# Solution

## Scope

Identity Common TypeScript provides modular TypeScript packages in several related areas:

- **Common primitives:** shared identity types, base64url handling, and JWT decoding;
- **Cryptography:** platform-neutral Web Crypto wrappers and hashing utilities;
- **Credential status:** OAuth Token Status List bitstrings and JWT/CWT transport;
- **SD-JWT:** selective-disclosure JWT processing and SD-JWT VC support;
- **Mobile documents:** ISO/IEC 18013-5 and 18013-7 mdoc issuance, presentation, and verification building blocks;
- **OpenID4VC:** OAuth 2.0, OpenID4VCI, OpenID4VP, and shared utilities;
- **Query processing:** Digital Credentials Query Language types and evaluation;
- **COSE and signatures:** CBOR Object Signing and Encryption and JAdES support;
- **Trust infrastructure:** ETSI Lists of Trusted Entities and XML trusted-list processing;
- **EUDI formats:** wallet-relying-party registration certificates, attestation schema metadata, and related European specifications; and
- **Future packages:** additional shared JOSE, X.509, certificate, and payment-related capabilities where community demand and maintainer capacity support them.

The project does not provide product-specific business workflows, hosted accounts, user interfaces, or deployment infrastructure. Consuming projects retain control of policy decisions, key custody, storage, user experience, and operational architecture.

## Architecture and Compatibility

The repository is a pnpm-managed TypeScript monorepo. Packages expose focused public APIs and can be versioned and released by package family. Shared tooling applies formatting, static type checking, unit testing, documentation checks, change tracking, and automated publication consistently across the workspace.

Consumers install only the relevant packages from npm. The libraries are designed for supported Node.js versions, modern browsers, and React Native. Breaking changes are communicated through package versions and Changesets. Standards evolution is handled through reviewed implementation changes, test vectors, compatibility notes, and coordinated releases rather than through a network upgrade or protocol fork.

## Security and Privacy

The project processes security-sensitive identity data and cryptographic structures but does not operate a hosted service or retain end-user data by itself. Applications remain responsible for secure key management, storage, authentication, authorization, and deployment.

The repository provides a private vulnerability-reporting process and a public security policy. Automated checks cover formatting, static types, tests, and dependency changes. Security-relevant fixes will be reviewed, released, and disclosed under the project's coordinated vulnerability process. The project intends to continue improving software supply-chain controls and OpenSSF Scorecard posture under LFDT governance.

## Interoperability and Testing

Each package family maintains automated tests appropriate to its specifications and public API. Imported packages retain their existing test coverage while moving toward shared conventions and cross-package integration tests. Standards examples, upstream test vectors, and external conformance tools will be used where available.

A release is considered technically healthy when the workspace installs reproducibly, static type checking succeeds, unit and integration tests pass, packages build, and the generated artifacts can be consumed from a representative Node.js application. Browser and React Native compatibility will be tested for packages that claim those environments.

## Adoption, Applications, and Use Cases

Expected consumers include:

- digital identity wallets that need OpenID4VC, SD-JWT, mdoc, DCQL, COSE, or trust-list support;
- credential issuers and verifiers that need reusable protocol and format implementations;
- middleware and gateways that expose standards-based wallet functionality to business applications;
- interoperability and conformance tools; and
- other LFDT and OpenWallet Foundation projects that need common TypeScript identity components.

The repository README identifies related projects including EUDIPLO, Credo, and OpenID Federation TypeScript. A relationship alone is not claimed as production adoption.

The libraries are used by multiple existing projects across the OpenWallet Foundation ecosystem and beyond like:
- EUDIPLO
- credo

Wallet implementations like:
- Paradym (Animo)

The analysis of monthly downloads around half a million indicates significant usage and interest in the libraries.

| Package                          |      Downloads / month |
| -------------------------------- | ---------------------: |
| **@sd-jwt/core**                 | **~94,200** ([npm][1]) |
| **@sd-jwt/sd-jwt-vc**            | **~77,300** ([npm][1]) |
| **@owf/identity-common**         |            **≈66,300** |
| **@owf/token-status-list**       |  **52,404** ([npm][2]) |
| **dcql**                         |  **37,125** ([npm][3]) |
| **@openid4vc/oauth2**            |  **25,763** ([npm][4]) |
| **@owf/mdoc**                    |            **≈25,500** |
| **@openid4vc/utils**             |  **25,241** ([npm][4]) |
| **@openid4vc/openid4vp**         |            **≈25,200** |
| **@openid4vc/openid4vci**        |  **23,562** ([npm][4]) |
| **@owf/cose**                    |            **≈21,700** |
| **@owf/eudi-lote**               |   **4,558** ([npm][5]) |
| **@owf/crypto**                  |             **≈4,100** |
| **@owf/eudi-attestation-schema** |   **3,820** ([npm][6]) |
| **@owf/eudi-wrprc**              |   **2,843** ([npm][6]) |
| **@owf/eudi-sca**                |   **2,815** ([npm][7]) |
| **@owf/eudi-tl**                 |   **2,069** ([npm][8]) |
| **@owf/eudi-jades**              |      **16** ([npm][6]) |

[1]: https://www.npmjs.com/search?q=keywords%3Asd-jwt-vc&utm_source=chatgpt.com "keywords:sd-jwt-vc - npm search"
[2]: https://www.npmjs.com/search?page=12&perPage=20&q=oauth&utm_source=chatgpt.com "oauth - npm search"
[3]: https://www.npmjs.com/search?q=keywords%3AOpenID4VC&utm_source=chatgpt.com "keywords:OpenID4VC - npm search"
[4]: https://www.npmjs.com/search?q=3c%E3%80%90PG66.CYOU%E3%80%91.vupa&time=1686132089386&utm_source=chatgpt.com "3c〖PG66.CYOU〗.vupa - npm search"
[5]: https://www.npmjs.com/search?q=keywords%3Aeudi&utm_source=chatgpt.com "keywords:eudi - npm search"
[6]: https://www.npmjs.com/search?q=keywords%3Aetsi&utm_source=chatgpt.com "keywords:etsi - npm search"
[7]: https://www.npmjs.com/search?q=keywords%3Asca&utm_source=chatgpt.com "keywords:sca - npm search"
[8]: https://www.npmjs.com/search?page=0&perPage=20&q=keywords%3Axades&utm_source=chatgpt.com "keywords:xades - npm search"

## License and Trademarks

The codebase is licensed under the [Apache License 2.0](https://github.com/openwallet-foundation-labs/identity-common-ts/blob/main/LICENSE). Third-party packages remain subject to their respective licenses and are managed through the project's package and automated dependency-review processes.

“Identity Common TypeScript,” package names in the `@owf` namespace, and associated repository branding are used as project identifiers. Their continued use or transfer will follow applicable Linux Foundation Europe, LFDT, OpenWallet Foundation, npm-namespace, and trademark review. Names of external standards and organizations are descriptive and do not imply endorsement.

# Effort and Resources

The primary sponsor and confirmed maintainers will continue technical leadership, review, releases, security response, documentation, and community support during and after transition. The public [GitHub contributors overview](https://github.com/openwallet-foundation-labs/identity-common-ts/graphs/contributors?all=1) provides transparent evidence of a broader contribution history across the consolidated codebase.

## Contributor Base and Community Growth

The repository has contributions from multiple developers, but historical contribution, current activity, governance responsibility, and organizational affiliation are different measurements. In particular, a contributor graph can be affected by imported history, author-email matching, merge strategy, automated accounts, and large mechanical changes. The project will therefore publish both the raw GitHub evidence and a clearly defined, reproducible community-health measure.

Project roles will remain distinct:

- **Sponsors** explicitly endorse this proposal and support the project during LFDT onboarding.
- **Maintainers** accept continuing responsibility for technical decisions, reviews, releases, security, and governance.
- **Active developers** perform substantive code, test, documentation, review, triage, release, security, or standards-maintenance work.
- **Adopters and community participants** provide implementation feedback, interoperability testing, use cases, and requirements.

Commit counts will not automatically confer sponsorship or maintainership. Supporting sponsors will be named only with their consent. Maintainers will be selected through a documented process based on sustained participation, technical judgment, review activity, reliability, and community trust.

Within 12 months of LFDT onboarding, the project aims to sustain at least seven active human developers from at least three independent organizations, including at least three active developers who are not initial maintainers. For this measure, an active developer is a person who, during the preceding 12 months, has completed at least one merged code, test, or documentation contribution; performed substantive review work; or taken recurring responsibility for triage, releases, security, standards tracking, or another technical project function. Automated accounts are excluded, and imported commits count only when the person also participates in the current project during the measurement period.

The project will support this objective by maintaining clear contribution guidance, labelling onboarding issues, offering timely reviews, publishing package roadmaps, discussing standards changes in public channels, recognizing non-code contributions, and documenting the path from contributor to maintainer.

The transition plan is:

1. Confirm sponsors, named maintainers, organizational affiliations, adoption references, and repository DCO status.
2. Transfer or import the repository and associated package, release, and community resources under the process agreed with LFDT.
3. Preserve package names, releases, issue history, documentation, and contributor attribution where the approved migration process permits.
4. Align governance, security, release, reporting, and namespace management with LFDT requirements.
5. Publish transparent contributor and maintainer criteria and recruit maintainers from additional organizations.
6. Continue standards maintenance, test coverage, interoperability work, and cross-project adoption.

The project has no fixed completion date. It is long-lived shared infrastructure that will track relevant standards and the needs of consuming projects.

# How To

## Build and Test from Source

With Git, a supported Node.js release, Corepack, and pnpm installed:

```shell
git clone https://github.com/openwallet-foundation-labs/identity-common-ts.git
cd identity-common-ts
corepack enable
pnpm install --frozen-lockfile
pnpm lint
pnpm types:check
pnpm test
pnpm build
```

Individual packages can then be exercised through their package tests and the repository examples. A successful checkout installs reproducibly, passes formatting and Markdown checks, completes TypeScript type checking and Vitest tests, and builds the publishable package artifacts.

Consumers install the required published package or package family from npm and import its documented public APIs. Package-specific documentation, examples, and migration notes are maintained in the repository.

# References

- [Identity Common TypeScript repository](https://github.com/openwallet-foundation-labs/identity-common-ts)
- [README and package overview](https://github.com/openwallet-foundation-labs/identity-common-ts/blob/main/README.md)
- [Packages](https://github.com/openwallet-foundation-labs/identity-common-ts/tree/main/packages)
- [Examples](https://github.com/openwallet-foundation-labs/identity-common-ts/tree/main/examples)
- [Releases](https://github.com/openwallet-foundation-labs/identity-common-ts/releases)
- [GitHub contributors overview](https://github.com/openwallet-foundation-labs/identity-common-ts/graphs/contributors?all=1)
- [Contribution guide](https://github.com/openwallet-foundation-labs/identity-common-ts/blob/main/CONTRIBUTING.md)
- [Security policy](https://github.com/openwallet-foundation-labs/identity-common-ts/blob/main/SECURITY.md)
- [Code owners](https://github.com/openwallet-foundation-labs/identity-common-ts/blob/main/CODEOWNERS)
- [Apache License 2.0](https://github.com/openwallet-foundation-labs/identity-common-ts/blob/main/LICENSE)
- [LFDT project lifecycle](https://lf-decentralized-trust.github.io/governance/governing-documents/project-lifecycle/)
- [LFDT maintainer-file requirements](https://lf-decentralized-trust.github.io/governance/governing-documents/MAINTAINERS-file/)
- [LFDT maintainer-diversity guidance](https://lf-decentralized-trust.github.io/governance/guidelines/maintainer-diversity-best-practices/)
- [LFDT project proposal process](https://lf-decentralized-trust.github.io/project-proposals/)

# Closure

Identity Common TypeScript will be considered successful within LFDT when it provides a sustainably governed, interoperable, and broadly reusable TypeScript foundation for digital identity projects. Progress will be measured by:

- continued versioned releases for actively maintained package families with automated build, type-check, test, security, and publication processes;
- maintained compatibility with the stable versions of the specifications each package claims to implement;
- at least three publicly referenceable consuming projects from at least two independent organizations;
- reproducible tests and package builds, with representative environment testing for claimed Node.js, browser, and React Native support;
- at least seven active human developers from at least three independent organizations within a rolling 12-month period, including at least three who are not initial maintainers;
- active maintainers from multiple independent organizations, with a documented path from contributor to maintainer and progress toward the diversity required for Graduation;
- current API, package, migration, contribution, and security documentation; and
- satisfaction of the applicable LFDT Incubation Exit Criteria before requesting a separate Graduation review.
