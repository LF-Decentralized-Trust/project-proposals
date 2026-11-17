---
layout: default
title: tsp reference implementation migrating from OpenWallet to LFDT
parent: Incubation
grand_parent: Project Proposals
---

# Sponsor(s)

Wenjing Chu, Lead Maintainer (Futurewei Technologies, Inc.), [wchu@futurewei.com](wchu@futurewei.com), GitHub: [@wenjing](https://github.com/wenjing) 
Additional sponsors:
Carly Huitema, Drummond Reed, Glenn Gore of the Trust over IP community

# Abstract

TSP project is a reference implementation and SDK for the Trust Spanning Protocol (TSP) as specified by the Trust over IP project of the LF Decentralized Trust Foundation, and its related developer testbed, tools, CLI, testing infrastructure and application examples and/or extensions.

TSP is the core spanning layer of the Trust over IP stack - it provides authenticity, confidentiality and metadata privacy for any party to any other addressed by Verifiable Identifiers.

It is developed in Rust, and supported through additional language bindings including Python and Javascript. It may add additional language bindings as needs arise. It is transport agnostic in terms of how it carries its messages. Current implementation supports HTTP(s), TCP, QUIC, and additional AI agent protocols like MCP.

It can support diverse verifiable identifiers, e.g. DIDs (like did:webvh, did:peer), but can also support other identifiers and URN in general. Additional IDs like AID/did:webs and did:scid are in the roadmap.

It has built in post-quantum cryptography support, by adopting TSP, you are PQ-ready and can turn it on without changing protocol.

For more detailed introduction of Why TSP Matters and its status, this new LFDT blog post is a great resource for a compact introduction. [TSP 1.0 LFDT Blog](https://www.lfdecentralizedtrust.org/blog/tsp-1.0-a-trust-layer-for-the-age-of-ai-agents). 

**TSP in brief**
TSP is the spanning layer of the Trust Over IP stack: a minimal protocol that every higher-level trust application can share.
  - Verifiable identifiers (VIDs) at both ends. Each party is addressed by an identifier it controls, such as did:webvh, rather than by an account on someone else's platform.
  - Authenticity, confidentiality and metadata privacy in one compact envelope. Messages are signed and encrypted, and routed or nested modes protect metadata from unwanted snooping.
  - Relationship forming built in. Parties establish and manage long-term trust relationships through standard control messages.
  - Post-quantum ready. Hybrid post-quantum encryption and post-quantum signatures are part of TSP 1.0, available whenever a relationship needs them.
  - Efficient encoding at scale. TSP is based on CESR encoding, which unifies text and binary encodings and keeps messages compact and fast to process.
  - Transport independent. TSP runs over HTTP, TCP, QUIC or any other transports that applications/agents may already be using (e.g. MCP and A2A), and carries any payload, text or binary, including JSON, CBOR, MessagePack or CESR messages.

# Context

The TSP has just been approved by the Trust over IP WG as 1.0 specification and is in the process of approval by ToIP steering committee. For information about the specification and its development history, please check out the spec repo: [https://github.com/trustoverip/tswg-tsp-specification](https://github.com/trustoverip/tswg-tsp-specification).

The open source reference implementation has been hosted and actively developed in the OpenWallet Foundation as a lab project. This proposal is to migrate that to LFDT as an incubation project.

# Dependent Projects

TSP does not have any mandatory dependencies that would be impacted by this migration. For example, TSP SDK currently depends on DID:WEBVH and Askar secure store, such dependencies are not impacted by this move. (Askar may itself be moving to LFDT.)

# Motivation

Why TSP Matters Now:
The internet was built to move data, not to establish trust. For decades we patched that gap with passwords, certificates tied to domains, and platform accounts. In 2026 those patches are failing on four fronts at once.
 - AI agents now operate on web infrastructure that has no identity and trust layer. They browse, sign in, send email, call APIs, move money and change code through the same accounts and channels people use. When an agent shows up, there is no reliable way to know what it is, who stands behind it, or whether it should be trusted. It may be posing as a person, acting openly for one, acting for no one at all, or quietly hijacked by an attacker, and from the other side these all look the same. That uncertainty now runs through everything an agent touches. TSP addresses this at the root. It gives every party a strongly authenticated identity and makes their relationship authentic, establishing who said what to whom. Each party can verify this before acting, and each can be held accountable afterwards.
 - Generative AI has made impersonation cheap. Voices, faces and writing styles can be faked at scale, and detection will not keep up. The real defense is verifiable relationships: knowing who you are dealing with, through a durable identifier that party controls, and being assured that you are communicating with the real party.
 - Trust ecosystems are naturally diverse. Identifier methods, credential formats and wallet ecosystems differ for good reasons, serving different jurisdictions and industries. That diversity is healthy, but without a common layer, every pair of ecosystems needs its own bridge. TSP is designed to fill that role: a compact interworking layer that spans identifier types and trust boundaries, the way IP spans networks.
 - Trust also has to hold up over time. Data captured today could be decrypted once quantum computers become capable, which may not be far off. Accountability records, such as signed logs and audit trails, may need to remain verifiable for years. And trust relationships themselves are meant to last. In some areas, protecting all three calls for post-quantum cryptography now rather than later.

The common question behind all four is the one TSP was designed to answer: who said what to whom.

TSP is a minimalistic interworking (or spanning) protocol that (a) assures authenticity as first priority and confidentiality and metadata privacy, (b) maximizes interoperability, (c) maximizes cryptographic agility. So above all, it solves an authenticity problem - without which we can't have a stable foundation to build applications, esp. agentic ones. Its flexibility in adapting to different identifiers/trust boundaries and transport and cryptos gives it edge as a long term interworking protocol. Its speed and scalability allows it be adopted in both high and lower layers of technology stacks.

# Status

The project has been in development in the OpenWallet community, concurrently along with the TSP specification work in Trust over IP (LFDT community), for the last 2+ years with 15 code contributors around the world on its core repo and numerous contributors on the Specification side that directly influenced code development. Significant contributions have already been made to build up a convenient testbed, benchmarking, CI/CD, extensions, application examples and tooling.

# Solution

Authenticity:
TSP solves it with (a) a uniquely strong combination of public key authenticated encryption (PKAE) and signature, (b) verifiable identifier that a verifier can appraise its continuous key state. Conventional schemes (encrypt then sign or vice versa) leave unacceptable weakness in that combination. TSP assures the we know who is the sender, who is the intended receiver, and the message is not tempered. 

Interworking:
Several key design choices: the minimalist approach, the CESR binary/text encoding, the self-framing, crypto agility that comes with it, and most importantly by designating not one identifier format by only verifiability/appraisability criteria. It is efficient, disciplined and adaptive.

Metadata privacy:
It has built in intermediary design that can use routed and nested messages efficiently to support metadata privacy.

Post-quantum:
TSP supports crypto agility which includes supporting PQ algorithms as they mature without changing the protocol. The SDK has built in PQ support.

Trust enabled AI agents:
TSP provides a solid foundation to solve the challenges AI agent deployment is facing. In addition to the work in TSP, the Trust over IP's AI and Human Trust Working Group is also working on the Trust Enabled AI Agents (TEA) specification that will further develop how to integrate TSP and other Trust over IP solutions to help the agentic applications.

# Effort and Resources

The TSP repo is sufficiently complete and stable (together with the TSP 1.0) spec. Current TSP SDK crate is in version 0.16. The new developments are expected in compliance, interoperability, extensions, use cases and benchmarking or porting and language supports etc. We expect the required efforts and resources for the SDK itself to be consistent with existing and new contributors.

# How To

It comes with a full fledged testbed, including CLI for local endpoints and online DID server and intermediaries on the cloud (the testbed).
The "Try it" section here describes how to test it on a local host and the using the SDK library section describes how to code your own application/test: https://github.com/openwallet-foundation-labs/tsp.

# References

The TSP 1.0 specification: https://trustoverip.github.io/tswg-tsp-specification/
The code repo: https://github.com/openwallet-foundation-labs/tsp
The Rust crate: https://docs.rs/tsp_sdk/latest/tsp_sdk/index.html
The LFDT blog post: https://www.lfdecentralizedtrust.org/blog/tsp-1.0-a-trust-layer-for-the-age-of-ai-agents

# Closure

I think ultimately a reference implementation of TSP is successful when TSP is successfully adopted. In the blog post I cited above, we can point to openVTC, First Person project, Linux kernel group's developer trust use case, more recent libp2p development and experimental integrations with MCP/A2A that are being developed for agentic systems. One of the work I like to propose for the project is actually a list of such use cases on the project README.

The second way to measuring success is to see interoperability and compliance test suites and results. This is already on roadmap as one of the things to do.

Adoption also happens because a protocol is being designed into other protocols/applications. TSP is esp. designed to be built on - the upper protocols are called trust tasks, and the number of trust tasks that are built on TSP is rapidly increasing. One such example is happening in the DTG Working Group in the Trust over IP community. This community web site lists 800+ such trust tasks - a vibrate community of creative excitements.

Finally, more supported languages, bindings, transports, identifiers, use cases, and higher performances, ... can also be measured.
