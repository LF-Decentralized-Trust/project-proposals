---
layout: default
title: Multipaz
parent: Incubation
grand_parent: Project Proposals
---

# Project Identifier

Multipaz Project Proposal v0.1

# Sponsor(s)

- **Primary Sponsor:** David Zeuthen, Lead Maintainer (Google LLC) — [zeuthen@google.com](mailto:zeuthen@google.com), GitHub: [@davidz25](https://github.com/davidz25)
- **Supporting Sponsors:**
  - Akash Shah, Maintainer (Google LLC) — [dyiop@google.com](mailto:dyiop@google.com), GitHub: [@dyiop](https://github.com/dyiop)
  - Gareth Oliver, Maintainer (Google LLC) — [gco@google.com](mailto:gco@google.com), GitHub: [@GarethCOliver](https://github.com/GarethCOliver)
  - Ever Morales, Maintainer (Open Mobile Hub) — [ever.morales@koombea.com](mailto:ever.morales@koombea.com), GitHub: [@TheBlackBit](https://github.com/TheBlackBit)
  - Hanlu Feng, Maintainer (Open Mobile Hub) — [hanlu.feng25@gmail.com](mailto:hanlu.feng25@gmail.com), GitHub: [@hanluOMH](https://github.com/hanluOMH)
  - Vishnu Sanal T, Maintainer (Open Mobile Hub) — [t.v.s10123@gmail.com](mailto:t.v.s10123@gmail.com), GitHub: [@VishnuSanal](https://github.com/VishnuSanal)
  - Saurabh Goyal, Maintainer (Open Mobile Hub) — [saurabh@openapplab.org](mailto:saurabh@openapplab.org), GitHub: [@saurabhgoyal7872](https://github.com/saurabhgoyal7872)
  - Diego Zuluaga, Maintainer (Open Mobile Hub) — [diegofossdev@gmail.com](mailto:diegofossdev@gmail.com), GitHub: [@dzuluaga](https://github.com/dzuluaga)
  
# Abstract

Multipaz is a multiplatform open-source SDK, UI toolkit, and server framework for real-world digital credentials across the three-party trust model (Issuer, Holder, and Verifier), supporting ISO/IEC 18013-5 mdoc/mDL, IETF SD-JWT VC, OpenID4VCI, OpenID4VP, W3C Digital Credentials API, Face Matching, and Zero-Knowledge Proofs across Android, iOS, Web, and JVM servers.

# Context

Multipaz originated at Google as the Android `identity-credential` reference library for mobile driving licenses (mDL) and ISO/IEC 18013-5 credentials. To foster vendor-neutral, cross-platform collaboration across the entire digital identity ecosystem, Google donated the project to the OpenWallet Foundation (OWF), where it was rebranded to **Multipaz**, expanded into a full Kotlin Multiplatform (KMP) framework targeting Android, iOS, Web (JS/Wasm), and JVM servers, and advanced to an **OpenWallet Foundation Growth** project. With the OpenWallet Foundation shutting down, the maintainers propose transitioning Multipaz to LF Decentralized Trust (LFDT) as an Incubating project.

Multipaz addresses the complete lifecycle of real-world digital credentials across all three roles of the classic three-party identity model:
1. **Holder (Wallet):** Provisioning, hardware-backed key management (`SecureArea`), secure storage, consent UI, and credential presentment both in person (over NFC and Bluetooth Low Energy) and online/in-app (via the W3C Digital Credentials API and custom URI schemes).
2. **Verifier (Relying Party / Reader):** Proximity mdoc readers (via NFC engagement, NFC Concurrent Channel Engagement / NFCv2, BLE, and USB CCID NFC readers) and online/native verifiers supporting ISO/IEC 18013-7 and OpenID4VP 1.0 with Digital Credentials Query Language (DCQL).
3. **Issuer:** Standards-based credential issuance servers and client flows supporting OpenID for Verifiable Credential Issuance (OpenID4VCI), Cloud Secure Area (CSA) remote key attestation and signing, and credential status/revocation management.

The Multipaz project comprises five repositories in the `openwallet-foundation` GitHub organization proposed for transfer to LFDT:

| Repository | Description |
| --- | --- |
| [`openwallet-foundation/multipaz`](https://github.com/openwallet-foundation/multipaz) | Core Kotlin Multiplatform SDK, Compose Multiplatform and SwiftUI UI toolkits, Longfellow ZKP and FaceNet biometric modules, `multipazctl` CLI, in-browser developer tools, server modules, and test applications. |
| [`openwallet-foundation/multipaz-wallet`](https://github.com/openwallet-foundation/multipaz-wallet) | Full-featured multiplatform digital credential wallet application for Android (Jetpack Compose), iOS (SwiftUI), and Web (Kotlin/JS & React), along with its wallet backend server. |
| [`openwallet-foundation/multipaz-samples`](https://github.com/openwallet-foundation/multipaz-samples) | Standalone sample applications demonstrating Multipaz integration across Compose Multiplatform, Swift/iOS, `SecureArea`, and standalone verifiers. |
| [`openwallet-foundation/multipaz-developer-website`](https://github.com/openwallet-foundation/multipaz-developer-website) | Open-source Docusaurus developer portal ([developer.multipaz.org](https://developer.multipaz.org)) hosting documentation, guides, codelabs, blog posts, and generated KDoc API references. |
| [`openwallet-foundation/multipaz-utopia`](https://github.com/openwallet-foundation/multipaz-utopia) | Multi-organization reference playground of issuers, registries, payment providers, and relying parties in the fictional "Utopia" ecosystem. |

# Dependent Projects

Multipaz has no mandatory code dependencies on existing LF Decentralized Trust projects and requires no modifications to other LFDT codebases.

Within the broader LFDT and transitioning OpenWallet Foundation ecosystem, Multipaz complements projects such as **Hyperledger Aries**, **Identus**, **Credo**, and **EUDIPLO**:
- Whereas server-focused middleware (such as EUDIPLO) or DIDComm/agent frameworks (such as Aries and Identus) focus on backend protocol adaptation or agent-to-agent messaging, Multipaz provides a **Kotlin Multiplatform SDK and native UI toolkit** engineered from the ground up for mobile, web, and server environments with deep hardware-backed security (`SecureArea` for Android Keystore/StrongBox, Apple Secure Enclave, and Cloud Secure Area) and physical proximity transports (NFC APDU, NFC Forum Connection Handover, NFC CCE / NFCv2, and BLE GATT/L2CAP).
- Because Multipaz implements open international standards—including ISO/IEC 18013-5, ISO/IEC 18013-7, IETF SD-JWT VC, OpenID4VCI, OpenID4VP, DCQL, and OAuth Token Status List—it naturally interoperates with other LFDT issuer, verifier, and wallet projects and creates strong opportunities for cross-project conformance and interoperability testing within LFDT.

# Motivation

Implementing real-world digital identity solutions—such as Mobile Driving Licenses (mDLs), EU Digital Identity (EUDI) Personal Identification Data (PID) and attestations, Photo IDs, National IDs, and Digital Payment Credentials—requires navigating a complex, rapidly evolving matrix of specifications, cryptographic schemes, hardware security APIs, and transport protocols:

- **Cross-Platform Fragmentation:** Wallet and reader developers typically maintain separate native implementations for Android, iOS, Web, and backend servers. Duplicating intricate CBOR/COSE (RFC 8949 / RFC 9052), JOSE/SD-JWT (RFC 9901), X.509 PKI, VICAL/RICAL trust list validation, and state-machine logic across platforms is expensive and error-prone.
- **Hardware Security and Anti-Cloning:** High-assurance credentials require binding device keys to dedicated secure hardware (Android Keystore/StrongBox, iOS Secure Enclave) or Cloud Secure Areas (HSM-backed remote key management) with rigorous attestation verification and biometric/PIN user authentication.
- **Proximity and Online Convergence:** Users expect a seamless, unified experience whether tapping their phone against an NFC terminal at a transit gate or retail point-of-sale, presenting an mDL via BLE at an airport checkpoint, or sharing a credential with a website or native app via the W3C Digital Credentials API.
- **Privacy and Selective Disclosure:** Protecting user privacy requires not only selective disclosure in mdoc and SD-JWT VC formats, but also emerging privacy-preserving techniques such as rotating single-use credentials, unlinked presentations, and Zero-Knowledge Proofs (ZKP) per ISO/IEC 18013-5 Second Edition.

Multipaz addresses these challenges by providing a single, cohesive, permissively licensed (Apache 2.0) Kotlin Multiplatform framework:
- **Write Once, Run Natively Everywhere:** Core cryptographic, data-encoding, credential-storage, and protocol logic is written once in common Kotlin and compiled natively to JVM bytecode (Android and backend servers), native ARM64/x64 binaries via Kotlin/Native (iOS), and JavaScript/WebAssembly (Web browsers).
- **Production-Grade Native UI Components:** `multipaz-compose` (Compose Multiplatform) and `multipaz-swiftui` (native SwiftUI) provide ready-to-use, customizable consent prompts, credential carousels, QR scanners, and NFC/BLE presentment flows localized into more than 20 languages.
- **Active Standards Leadership & Battle-Tested Interoperability:** Multipaz maintainers actively contribute to ISO/IEC JTC1 SC17 WG10, OpenID Foundation (DCP and DCHP working groups), W3C, and IETF. Multipaz serves as a proving ground for new standards—such as ISO/IEC 18013-5 Second Edition, NFC Concurrent Channel Engagement (NFCv2) with sub-500ms and double-tap presentment, Zero-Knowledge Proofs via Google Longfellow-ZK, transaction data binding, and Post-Quantum Cryptography (ML-DSA, ML-KEM)—and is regularly validated at international interoperability events (including the France, Bangkok, and Geneva ISO interop events).

Transitioning Multipaz from the OpenWallet Foundation to LF Decentralized Trust ensures long-term, vendor-neutral governance, preserves continuity for downstream adopters, and anchors a flagship mobile and multiplatform credential SDK within the LFDT community.

# Status

**Proposed for Incubation.**

Multipaz is an established **OpenWallet Foundation Growth** project with a multi-year development history, over a dozen pre-1.0 releases, a steady 4-to-8 week release cadence on [Maven Central](https://central.sonatype.com/artifact/org.multipaz/multipaz), automated snapshot publishing on every merge to `main`, enforced 100% public KDoc documentation coverage via Detekt, and an active contributor community spanning multiple organizations.

The initial maintainers for the LFDT project are:

| Name | GitHub                                   | Email                                                           | Organization | Role |
| --- |------------------------------------------|-----------------------------------------------------------------| --- | --- |
| David Zeuthen | [@davidz25](https://github.com/davidz25) | [zeuthen@google.com](mailto:zeuthen@google.com)                 | Google LLC | Lead Maintainer |
| Akash Shah | [@dyiop](https://github.com/dyiop)       | [dyiop@google.com](mailto:dyiop@google.com)                     | Google LLC | Maintainer |
| Gareth Oliver | [@GarethCOliver](https://github.com/GarethCOliver) | [gco@google.com](mailto:gco@google.com)                         | Google LLC | Maintainer |
| Ever Morales | [@TheBlackBit](https://github.com/TheBlackBit) | [ever.morales@koombea.com](mailto:ever.morales@koombea.com)     | Open Mobile Hub | Maintainer |
| Hanlu Feng | [@hanluOMH](https://github.com/hanluOMH) | [hanlu.feng25@gmail.com](mailto:hanlu.feng25@gmail.com)       | Open Mobile Hub | Maintainer |
| Vishnu Sanal T | [@VishnuSanal](https://github.com/VishnuSanal) | [t.v.s10123@gmail.com](mailto:t.v.s10123@gmail.com)       | Open Mobile Hub | Maintainer |
| Saurabh Goyal | [@saurabhgoyal7872](https://github.com/saurabhgoyal7872) | [saurabh@openapplab.org](mailto:saurabh@openapplab.org)   | Open Mobile Hub | Maintainer |
| Diego Zuluaga | [@dzuluaga](https://github.com/dzuluaga) | [diegofossdev@gmail.com](mailto:diegofossdev@gmail.com)       | Open Mobile Hub | Maintainer |

The maintainers request direct transfer of the five existing GitHub repositories from `openwallet-foundation` to a new `multipaz` organization, preserving commit history, issues, pull requests, and releases. The repositories already enforce `Signed-off-by` (DCO) on commits and follow Linux Foundation governance practices from their tenure in the OpenWallet Foundation.

# Solution

## Architecture Overview

Multipaz is structured with strict boundaries between UI-agnostic core libraries, platform-native UI toolkits, protocol and server modules, developer tooling, and reference applications:

```text
┌────────────────────────────────────────────────────────────────────────────┐
│                   Applications & Reference Deployments                     │
│  ┌───────────────────────────────────┐  ┌───────────────────────────────┐  │
│  │ Multipaz Wallet                   │  │ Samples & TestApp             │  │
│  │ (Android, iOS, Web)               │  │ (Compose & SwiftUI)           │  │
│  └───────────────────────────────────┘  └───────────────────────────────┘  │
│  ┌───────────────────────────────────┐  ┌───────────────────────────────┐  │
│  │ Multipaz Web Tools                │  │ Reference Issuers, Verifiers  │  │
│  │ (tools.multipaz.org)              │  │ & Utopia Backends             │  │
│  └───────────────────────────────────┘  └───────────────────────────────┘  │
└─────────────────────────────────────┬──────────────────────────────────────┘
                                      │
                                      ▼
┌────────────────────────────────────────────────────────────────────────────┐
│                   Native UI & Platform Integration Layer                   │
│  • multipaz-compose (Compose Multiplatform UI components)                  │
│  • multipaz-swiftui (Native SwiftUI components)                            │
│  • multipaz-dcapi-credman (Android) & multipaz-dcapi-ios (iOS)             │
│  • multipaz-facenet (Biometric Face Matching & Active Liveness)            │
└─────────────────────────────────────┬──────────────────────────────────────┘
                                      │
                                      ▼
┌────────────────────────────────────────────────────────────────────────────┐
│                   Protocols, Document Types & ZKP Layer                    │
│  • multipaz-openid4vci & multipaz-openid4vci-server                        │
│  • multipaz-verifier & multipaz-verifier-server                            │
│  • multipaz-csa & multipaz-csa-server (Cloud Secure Area)                  │
│  • multipaz-doctypes (mDL, EU PID, Photo ID, Aadhaar, Payment) & utopia    │
│  • multipaz-longfellow (Google Longfellow-ZK Zero-Knowledge Proofs)        │
│  • multipaz-cbor-rpc (Multiplatform CBOR-RPC)                              │
└─────────────────────────────────────┬──────────────────────────────────────┘
                                      │
                                      ▼
┌────────────────────────────────────────────────────────────────────────────┐
│                      Core Multiplatform SDK (multipaz)                     │
│  • Multiplatform Crypto, CBOR, COSE, JOSE, X.509, PKCS#12, VICAL/RICAL     │
│  • Credential Store & Formats (ISO/IEC 18013-5 mdoc, IETF SD-JWT VC)       │
│  • SecureArea (Android Keystore/StrongBox, iOS Secure Enclave, Cloud, SW)  │
│  • Transports & Presentment (NFC, NFCv2 CCE, BLE, USB, W3C DC API, OID4VP) │
└────────────────────────────────────────────────────────────────────────────┘
```

## Key Components and Modules

### 1. Core SDK (`multipaz`)
Written in Kotlin Multiplatform targeting Android, iOS, JVM (server/desktop), and Web (Kotlin/JS and Wasm):
- **Data Encoding & Cryptography:** Strongly typed CBOR (RFC 8949) parser/encoder with Concise Diagnostic Notation (CDN) support, COSE (RFC 9052), JOSE/JWT, X.509 certificate chain generation and validation, PKCS#12 (RFC 7292) container support, and VICAL/RICAL trust list processing.
- **`SecureArea` Key Management:** Pluggable hardware-backed and software cryptographic key storage supporting key attestation, biometric/passcode user authentication, pre-unlocked key providers for double-tap NFC flows, and key agreement/signing:
  - `AndroidKeystoreSecureArea` (TEE and StrongBox hardware security modules on Android)
  - `SecureEnclaveSecureArea` (Apple Secure Enclave on iOS)
  - `CloudSecureArea` (remote HSM/server-backed key management with anti-cloning guarantees)
  - `SoftwareSecureArea` (cross-platform in-memory/persistent passphrase-protected keys)
- **Credential Formats & Document Store:** Complete lifecycle management for ISO/IEC 18013-5:2021 (and Second Edition draft) `mdoc` credentials and IETF `SD-JWT VC` (RFC 9901) credentials, including credential rotation, status list revocation checking (`RevocationChecker`), and local privacy-preserving event logging (`EventLogger`).
- **Face matching extension points:** Abstract interfaces for face matching implementations to plug in. These interfaces are optionally used for credential matching.
- **Proximity & Online Presentment:**
  - **In-Person (ISO/IEC 18013-5):** QR and NFC engagement (static, negotiated, and ISO/IEC 18013-5 Second Edition **NFC Concurrent Channel Engagement / NFCv2**), single-tap and double-tap NFC APDU presentment, BLE peripheral/central GATT and L2CAP data transfer, and external USB-connected NFC readers.
  - **Online & In-App:** W3C Digital Credentials API and custom URI scheme integrations supporting ISO/IEC 18013-7:2025 (Annex A and Annex C) and OpenID4VP 1.0 (including HAIP profiles, DCQL queries, and cryptographic transaction data binding).

### 2. UI Toolkits & OS Integrations
- **`multipaz-compose` & `multipaz-swiftui`:** Rich, platform-authentic UI components for Jetpack Compose / Compose Multiplatform and native iOS SwiftUI, including unified proximity/online consent prompts, transaction confirmation sheets, document carousels and vertical lists, QR code generators/scanners, and selfie/liveness capture. Localized into 21+ languages via the repository's custom `lokalize` build plugin.
- **`multipaz-dcapi-credman` & `multipaz-dcapi-ios`:** Deep OS integrations enabling wallet apps to register credentials with Android's Credential Manager (`DigitalCredentials`) and Apple's iOS `IdentityDocumentProviderExtension` for seamless W3C Digital Credentials API presentment in browsers and native apps.
- **`multipaz-facenet`:** On-device and server-side biometric face matching and active liveness verification using MediaPipe BlazeFace and MobileFaceNet (for testing and development and only).

### 3. Document Types, ZKP, and Protocol Modules
- **`multipaz-doctypes` & `multipaz-utopia`:** Pre-built schemas, claim metadata, localized labels, and sample data for standardized document types including ISO/IEC 18013-5 mDL, EU PID (mdoc and SD-JWT VC), ISO/IEC 23220 Photo ID, Aadhaar, Digital Payment Credentials, and Utopia reference credentials.
- **`multipaz-longfellow`:** Integration of the [Google Longfellow-ZK](https://github.com/google/longfellow-zk) library into Multipaz, enabling Zero-Knowledge Proof generation and verification for ISO/IEC 18013-5 Second Edition credentials so holders can prove attributes without revealing linkable signatures or raw claims.
- **`multipaz-openid4vci` & `multipaz-verifier`:** Client and high-level `VerificationSession` libraries for OpenID4VCI issuance and multi-protocol credential verification.
- **`multipaz-server` Suite (`multipaz-backend-server`, `multipaz-openid4vci-server`, `multipaz-verifier-server`, `multipaz-csa-server`, `multipaz-records-server`, `multipaz-server-frontend`, `multipaz-server-deployment`):** Ktor-based JVM backend services and container deployment configurations for running standalone or integrated issuers, verifiers, Cloud Secure Areas, and authoritative registries.

### 4. Developer Tools & Companion Repositories
- **`multipazctl`:** JVM command-line utility for generating IACA root certificates, Document Signer (DS) certificates, reader root/leaf certificates, and inspecting credential structures.
- **Multipaz Web Tools (`multipaz-tools` / [tools.multipaz.org](https://tools.multipaz.org)):** A 100% client-side, in-browser developer suite compiled to Kotlin/JS for inspecting ISO mdoc MSOs, CBOR/COSE payloads, Concise Diagnostic Notation (CDN), SD-JWT VCs, PKCS#12 files, `.mpzpass` containers, and testing W3C Digital Credentials API verifier requests without any PII leaving the developer's browser.
- **Multipaz Wallet (`multipaz-wallet`):** End-to-end reference wallet application for Android, iOS, and Web, backed by a wallet server that enforces hardware verified-boot/attestation checks in production ([wallet.multipaz.org](https://wallet.multipaz.org)) while offering a developer-friendly instance ([dev.wallet.multipaz.org](https://dev.wallet.multipaz.org)).

## Security and Privacy

Security and user privacy are foundational to Multipaz:
- **Hardware-Backed Keys & Memory Hygiene:** Private keys are generated and used inside hardware-isolated environments (`SecureArea`) whenever supported by the platform. For software keys and shared secrets, Multipaz implements explicit memory zeroing and lifecycle disposal.
- **Anti-Cloning & Device Attestation:** Through `CloudSecureArea` and platform attestation verification (Android Key Attestation with Verified Boot `GREEN` enforcement, Apple App Attest), issuers and wallet backends can cryptographically verify device integrity and prevent credential cloning.
- **Privacy by Design:** Multipaz supports selective disclosure, element-level device key authorization, unlinkable single-use credentials, Zero-Knowledge Proofs (`multipaz-longfellow`), and PII-free default logging.
- **Strict Input Validation:** All external CBOR, COSE, JOSE, X.509, and network payloads undergo strict schema and cryptographic validation prior to use.

## Interoperability and Testing

- **Automated Testing & Static Analysis:** Every pull request is gated by GitHub Actions running host unit tests across KMP targets (`./gradlew check`), server tests, and Detekt static analysis enforcing coding standards and 100% public API KDoc documentation coverage. Android instrumented device tests (`./gradlew connectedCheck`) and iOS simulator builds validate platform-specific hardware and UI paths.
- **International Interoperability Events:** Multipaz is continuously tested against dozens of independent wallet, reader, and issuer implementations at major international test events, including the **ISO/IEC SC17 WG10 Interop in La Ciotat, France (2026)**, the **Global Digital ID & Verifiable Credential Summit in Bangkok (August 2026)**, and the **IATA / Aptitude ISO Photo ID and mdoc Interoperability Event in Geneva (August 2026)**.
- **Public Reference Endpoints:** To help the broader ecosystem test interoperability 24/7, the project operates live, publicly accessible reference services:
  - **Developer Portal & Docs:** [developer.multipaz.org](https://developer.multipaz.org)
  - **Online Verifier (OpenID4VP & ISO 18013-7):** [verifier.multipaz.org](https://verifier.multipaz.org)
  - **OpenID4VCI Issuer Portal:** [issuer.multipaz.org](https://issuer.multipaz.org)
  - **In-Browser Developer Tools:** [tools.multipaz.org](https://tools.multipaz.org)
  - **Prebuilt Android APKs (Wallet, TestApp):** [apps.multipaz.org](https://apps.multipaz.org)
  - **Multipaz Wallet Backends:** [wallet.multipaz.org](https://wallet.multipaz.org) and [dev.wallet.multipaz.org](https://dev.wallet.multipaz.org)

## Adoption, Applications, and Use Cases

Multipaz is used in production applications, national/regional digital identity ecosystems, and cross-vendor interoperability testbeds:

| Organization or Project | Type of Use                                                                                                                                                            | Public Evidence or Reference |
| --- |------------------------------------------------------------------------------------------------------------------------------------------------------------------------| --- |
| **Google Wallet** | Production Android digital wallet platform using Multipaz for secure credential management and presentation. Also used for ID Pass issuance.                           | [Showcase](https://developer.multipaz.org/showcase) / [Google Play](https://play.google.com/store/apps/details?id=com.google.android.apps.walletnfcrel) |
| **Scytáles AB** | Uses Multipaz to power secure credential verification for the official EU Digital Identity (EUDI) Wallet reference implementation.                                     | [Showcase](https://developer.multipaz.org/showcase) / [GitHub Reference](https://github.com/search?q=org%3Aniscy-eudiw+multipaz&type=code) |
| **Khaklin Technologies** | Uses Multipaz (JVM target) as the holder library in a test wallet presenting SD-JWT VC credentials over OpenID4VP to `polaris-oid4vp` (OpenID4VP 1.0 + HAIP verifier). | [ADOPTERS.md](https://github.com/openwallet-foundation/multipaz/blob/main/ADOPTERS.md) / [`polaris-id`](https://github.com/EgorKhaklin/polaris-id/tree/main/lab/interop/multipaz) |

## License and Trademarks

All Multipaz repositories are licensed under the [Apache License 2.0](https://github.com/openwallet-foundation/multipaz/blob/main/LICENSE). Third-party dependencies are permissively licensed and tracked via Gradle version catalogs (`gradle/libs.versions.toml`) and pinned Yarn lockfiles (`kotlin-js-store/`), with automated Dependabot security monitoring.

The "Multipaz" name, logos, and `multipaz.org` domain are used to identify the open-source project and its public developer resources. Their continued use and stewardship will follow applicable Linux Foundation and LFDT trademark and domain guidelines.

# Effort and Resources

Multipaz is actively developed and maintained by engineers from **Google LLC** and **Open Mobile Hub**, alongside community contributors from wallet providers, relying parties, and standards organizations (see the [GitHub contributors graph](https://github.com/openwallet-foundation/multipaz/graphs/contributors)).

## Roadmap to 1.0 and Community Growth

- **Multipaz 1.0.0 Milestone:** The project publishes releases every 4–8 weeks to Maven Central (currently at `0.101.0` / `0.102.0-SNAPSHOT`) and is on track to reach **Multipaz 1.0.0** in late 2026 or early 2027, establishing long-term API and on-disk data stability guarantees.
- **Upcoming Technical Priorities:**
  - Finalizing ISO/IEC 18013-5 Second Edition support (including multiple matching document sets, extended consent prompt customization, and ZKP profiles).
  - Prototyping Post-Quantum Cryptography (ML-DSA and ML-KEM) for ISO/IEC 18013 and 23220 series credentials.
  - Expanding OpenID4VCI conformance and server-to-server issuance flows, as well as Digital Credentials Harmonized Presentation (DCHP) profiles.
  - Exploring agentic identity workflows where digital credential wallets interact safely with AI agents.
- **Governance and Organizational Diversity:** The project holds weekly public community meetings every Tuesday and maintains comprehensive contributor guides (`CONTRIBUTING.md`, `CODING-STYLE.md`, `DEVELOPER-ENVIRONMENT.md`, `TESTING.md`). During LFDT Incubation, the maintainers aim to continue expanding active contributor and maintainer participation across additional independent organizations consuming Multipaz in wallets, issuers, and verifiers.

## Transition Plan

1. Complete LFDT TAC proposal review and confirm repository transfer checklist.
2. Transfer the five repositories (`multipaz`, `multipaz-wallet`, `multipaz-samples`, `multipaz-developer-website`, `multipaz-utopia`) from `openwallet-foundation` to new `multipaz` organization.
3. Update repository links, CI/CD workflows, security reporting (`SECURITY.md`), and community meeting/Discord channels to LFDT infrastructure while preserving uninterrupted Maven Central publishing (`org.multipaz`) and `multipaz.org` developer services.
4. Continue regular 4–8 week releases toward the 1.0.0 milestone and work toward LFDT Graduation criteria.

# How To

## Consuming Multipaz Libraries

Released artifacts are available on [Maven Central](https://central.sonatype.com/artifact/org.multipaz/multipaz):

```kotlin
dependencies {
    implementation("org.multipaz:multipaz:0.101.0")
    implementation("org.multipaz:multipaz-doctypes:0.101.0")
    implementation("org.multipaz:multipaz-compose:0.101.0")
}
```

For iOS applications, consumers can integrate Multipaz via Gradle and [SKIE](https://skie.touchlab.co/) to build an umbrella `XCFramework` (as demonstrated in `multipaz-wallet/shared`) and link `multipaz-swiftui`.

## Building and Testing from Source

```shell
git clone https://github.com/openwallet-foundation/multipaz.git
cd multipaz

# Compile and run all host unit tests and Detekt documentation/lint checks
./gradlew check

# Build the multipazctl CLI fat JAR
./gradlew :multipazctl:buildFatJar

# Assemble the Android test application
./gradlew :samples:testapp:assembleDebug
```

## Trying Live Demonstrations

Without building from source, evaluators can immediately test Multipaz:
1. Download prebuilt Android APKs for **Multipaz Wallet** or **Multipaz TestApp** from [apps.multipaz.org](https://apps.multipaz.org).
2. Provision test mDL, EU PID, or Photo ID credentials from the live OpenID4VCI issuer at [issuer.multipaz.org](https://issuer.multipaz.org).
3. Present credentials online using OpenID4VP 1.0 or ISO/IEC 18013-7 over the W3C Digital Credentials API at [verifier.multipaz.org](https://verifier.multipaz.org).
4. Inspect and debug CBOR, COSE, mdoc MSO, and SD-JWT VC payloads locally in the browser at [tools.multipaz.org](https://tools.multipaz.org).

# References

- [Multipaz Core Repository](https://github.com/openwallet-foundation/multipaz)
- [Multipaz Wallet Repository](https://github.com/openwallet-foundation/multipaz-wallet)
- [Multipaz Samples Repository](https://github.com/openwallet-foundation/multipaz-samples)
- [Multipaz Developer Website Repository](https://github.com/openwallet-foundation/multipaz-developer-website)
- [Multipaz Utopia Repository](https://github.com/openwallet-foundation/multipaz-utopia)
- [Multipaz Developer Portal & Documentation](https://developer.multipaz.org/)
- [Multipaz API Reference (KDocs)](https://developer.multipaz.org/kdocs/index.html)
- [Multipaz Maven Central Artifacts](https://central.sonatype.com/artifact/org.multipaz/multipaz)
- [Multipaz Web Developer Tools](https://tools.multipaz.org/)
- [Multipaz Online Verifier](https://verifier.multipaz.org/) and [Issuer Portal](https://issuer.multipaz.org/)
- [ISO/IEC 18013-5:2021 — Personal identification — ISO-compliant driving licence — Part 5: Mobile driving licence (mDL) application](https://www.iso.org/standard/69084.html)
- [ISO/IEC TS 18013-7:2025 — Mobile driving licence (mDL) add-on functions](https://www.iso.org/standard/82772.html)
- [IETF RFC 9901 — Selective Disclosure for JSON Web Tokens (SD-JWT)](https://datatracker.ietf.org/doc/rfc9901/)
- [IETF SD-JWT-based Verifiable Credentials (SD-JWT VC)](https://datatracker.ietf.org/doc/draft-ietf-oauth-sd-jwt-vc/)
- [OpenID for Verifiable Credential Issuance (OpenID4VCI)](https://openid.net/sg/openid4vc/) and [OpenID for Verifiable Presentations (OpenID4VP)](https://openid.net/sg/openid4vc/)
- [W3C Digital Credentials API](https://w3c-fedid.github.io/digital-credentials/)
- [Google Longfellow-ZK Library](https://github.com/google/longfellow-zk)
- [LFDT Project Lifecycle](https://lf-decentralized-trust.github.io/governance/governing-documents/project-lifecycle/)

# Closure

Multipaz will be considered successful in LFDT Incubation when it achieves a smooth transition from the OpenWallet Foundation and satisfies the LFDT Incubation Exit Criteria toward Graduation, measured by:
- **1.0 Release & Release Cadence:** Reaching the stable `1.0.0` release milestone with documented API/storage stability guarantees and maintaining a predictable 4-to-8 week release cadence on Maven Central.
- **Standards & Interoperability Leadership:** Continued conformance and verified interoperability with independent wallet, reader, and issuer implementations across ISO/IEC 18013-5 (First and Second Editions), ISO/IEC 18013-7, OpenID4VCI, OpenID4VP, W3C Digital Credentials API, and SD-JWT VC.
- **Community & Maintainer Diversity:** Sustained active contributions and maintainership across multiple independent organizations (building on the current Google LLC and Open Mobile Hub maintainer base), with transparent governance and regular public community calls.
- **Production & Ecosystem Adoption:** Continued growth in production wallets, relying party verifiers, and issuer deployments documented in `ADOPTERS.md` and the Multipaz Showcase.
- **Security & Best Practices:** Meeting LFDT security, OpenSSF Best Practices / Scorecard, DCO, and CI/CD standards across all transferred repositories.
