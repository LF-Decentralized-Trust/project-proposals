---
layout: default
title: CLPR
parent: Incubation
grand_parent: Project Proposals
---

# Sponsor(s)
<!-- TODO: confirm full sponsor list (name, affiliation, email) -->
- Richard Bair (Hashgraph) [<richard@hashgraph.com>](mailto:richard@hashgraph.com)
- Leemon Baird (Hashgraph) [<leemon@hashgraph.com>](mailto:leemon@hashgraph.com)
- Hendrik Ebbers (Hashgraph) [<hendrik.ebbers@hashgraph.com>](mailto:hendrik.ebbers@hashgraph.com)
- Edward Wertz (Hashgraph) [<edward@hashgraph.com>](mailto:edward@hashgraph.com)
- Joseph Sinclair (Hashgraph) [<joseph.sinclair@hashgraph.com>](mailto:joseph.sinclair@hashgraph.com)
- Diane Mueller (Hedera Hashgraph LLC) [<diane@hedera.com>](mailto:diane@hedera.com)

# Abstract
CLPR ("Clipper") is an extensible **C**ross **L**edger **PR**otocol that enables
reliable, asynchronous, in-order message passing between independent ledger
networks without bridges, pooled liquidity, or intermediary validator networks.


# Context
The ideas behind CLPR stem from the proposals and approaches to cross-ledger 
communication advocated by Dr. Leemon Baird, co-founder of Hedera, and designer
of the Hashgraph consensus algorithm.

CLPR initially grew out of the need and desire to facilitate fast asynchronous 
Byzantine Fault Tolerant (aBFT) interledger communication between Hiero based 
networks such as Hedera Mainnet and private HashSpheres. By introducing Verifier
Contracts as the anchors of trust on communication Channels, we were able to 
create an extensible pattern that can support arbitrary trust paradigms and 
ledger data formats.

Pursuant to its agreement with the Hedera Governing Council, Hashgraph has 
created the initial CLPR Specification and developed an initial implementation
of the CLPR specification, integrated as a native service within the Hiero
consensus node. We have also implemented CLPR Service smart contracts which
can be deployed to any EVM network along with prototype CLPR Endpoints which
can build state-proven bundles for Besu networks. The code and documents for
these elements have been open sourced. (See References)

The Hedera Governing Council wants to donate CLPR to be incubated as an LFDT Lab
project, stewarded and developed further by Hashgraph and the community of CLPR 
adopters. The Hedera Governing Council will donate the brand and trademark to 
the LFDT if the Lab proposal is accepted.

# Dependencies and Related Projects

With the donation of CLPR to the LFDT, there becomes clear relationships between
the following things:

1. The normative CLPR Specification details the protocols, software APIs, and
   expected behavior of the defined CLPR components.
2. The LFDT hosted reference implementations that exemplify expected behavior
   and illustrate possible implementation and deployment approaches.
3. External native or custom implementations of CLPR  that are maintained by 
   other projects or organizations

The CLPR specification has no intrinsic software dependencies. It can be
implemented in any programming language and be integrated with any chain. 
Interoperability is determined by conformance to the APIs and protocols. A copy 
of the CLPR Specification has been published to the
[hiero-hackers/CLPR-Spec](%20https://github.com/hiero-hackers/CLPR-spec)
repository hosted by the LFDT.

An initial reference implementation for Besu networks has been published to the
[hiero-hackers/clpr-smart-contracts](https://github.com/hiero-hackers/clpr-smart-contracts)
and [hiero-hackers/clpr-evm-endpoint](%20https://github.com/hiero-hackers/clpr-evm-endpoint)
repositories. The smart contract repo contains Solidity implementations of the
CLPR Service and various Verifier Contracts, while the EVM endpoint repository
contains a java implementation of a CLPR Endpoint able to read Besu chain state
and submit bundles to the Besu network for a deployed CLPR Service smart
contract.

The Hiero Improvement Proposal (HIP-1535) has been presented to the Hiero TSC.
The Hedera Governing Council has approved adoption of CLPR for the Hedera
network. With TSC approval, a 
[Hiero native implementation of the CLPR specification](https://github.com/hiero-ledger/hiero-consensus-node/pull/27029) 
will be merged into the Hiero consensus node. Hiero will be the first project to
adopt CLPR and create a native implementation conformant to the CLPR
Specification.

These donated codebases are the first instances in an extensible pattern. Under
the stewardship of the LFDT, we hope to see the development of additional
reference implementations for different types of ledgers and adoption by 
different chains to incorporate native implementations.

Hashgraph is developing its own CLPR applications and will continue to develop
CLPR Endpoint relays and smart contract based CLPR implementations deployable
to different types of ledgers. We hope to do this in open collaboration with 
other interested parties under the governance of the LFDT. We hope this 
inspires various chains to adopt CLPR and integrate their own native 
implementations to simplify interledger communication and trust.

The CLPR specification and deployable references implementations of the CLPR
Service, CLPR Endpoints, and Verifier Contracts would greatly benefit from
neutral, vendor-independent open-source governance within the LFDT.

# Motivation

Today, the most common solutions for cross-ledger communication involve 
additional trust, either in the form of trusting oracles, or by adding an
intermediate ledger to custody the assets being transferred. Exploits of bridges
and 3rd party trust mechanisms have been on the rise. Interledger trust models
are simpler and more secure if chains can communicate with and trust each other
leveraging their native security models.

There are two deployment methodologies for CLPR. The first is for a chain to
implement the CLPR specification natively. The CLPR Service smart contract
would be a native implementation and its operation managed by the governing
body of the chain. Some or all validators or consensus nodes would operate as
CLPR Endpoints, relaying bundles of CLPR data from the local chain to peer
CLPR Endpoints and submitting remote bundles to the local chain.

The second deployment approach is non-native. The CLPR Service is deployed as
a smart contract and is administered by the deployer. The CLPR Endpoints would
be independently operated from the related ledger, responsible for monitoring
the CLPR Service chain state, creating outgoing bundles and submitting incoming
bundles as transactions to the CLPR Service smart contract. While formal
adoption of CLPR and native implementation of its contracts is not necessary
for communication with a ledger, adoption and implementation by the governing
body of a ledger and native implementation is a superior state of trust.

While there are many competing approaches and standards for interledger
communication, there are only a few that minimize the number of fundamentally
trusted parties to just the ledgers themselves (when deployed as native
services of the participating ledgers).

# Status

Proposal to become an LFDT Lab project.

CLPR is under active development by Hashgraph on behalf of the Hedera Governing
Council. The Hedera Governing Council has adopted CLPR, and it will be used as
one of the core communication pathways between private HashSpheres and the 
public Hedera Mainnet. The CLPR intellectual property, including the trademark
and existing code is owned by Hedera Hashgraph, LLC (the Hedera Governing
Council) and will be donated to the LFDT subject to an Apache 2.0 License
upon acceptance of the proposal. The Hedera Governing Council has published a
version of the CLPR code repositories and will transition to public development
of CLPR under LFDT governance upon acceptance of the proposal.

Working deployments in the published repositories:

1. Hiero ⇔ Hiero
2. Besu ⇔ Hiero
3. Besu ⇔ Besu

# Solution

The detailed specification is provided in the CLPR-spec repository in the Hiero
Hackers GitHub organization. The core ontology and explanation of extensibility
of the solution is provided here.

## Terminology

- **Peer Ledger** — the other ledger that a network communicates with over CLPR.
- **State Proof** — a cryptographic proof that a specific piece of data exists
  in a ledger's committed state and/or history. State proofs are CLPR's sole
  mechanism of cross-ledger trust.
- **CLPR Endpoint** — a node responsible for periodically exchanging
  configuration and messages with peer Endpoints.
- **CLPR Service** — Responsible for curating CLPR state per ledger, managing
  communication Channel state to remote ledgers, routing messages to 
  applications, and coordinating economic transactions between Connectors,
  applications, and Endpoints.
- **Channel** — an on-ledger entity representing a communication path to a
  specific peer CLPR Service instance, bound to one Verifier Contract for its
  lifetime. Multiple Channels may exist between the same two ledgers.
- **Connector** — an economic entity that authorizes messages on the source
  ledger and pays for their execution on the destination ledger.
- **Message** — an arbitrary byte payload plus routing metadata representing 
  one unit of cross-ledger communication.
- **Bundle** — an ordered batch of messages transmitted together between two
  ledgers, accompanied by a state proof.
- **Data Message** — a message carrying application content. Every Data Message
  produces exactly one Response Message.
- **Response Message** — generated on the destination ledger after processing 
  a Data Message; carries a status and reply bytes back to the source.
- **Control Message** — a protocol message that manages Channel state (e.g., 
  configuration updates) rather than carrying application data.
- **Configuration** — a ledger's `ChainID`, protocol version, and throttle 
  parameters, as published to peers.
- **Verifier Contract** — An immutable smart contract responsible for verifying
  state proofs from remote ledgers and decoding the bundle content from the 
  remote ledger's data format to the local ledger's in-memory data format.
- **Trust Anchor** — the opaque, verifier-defined representation of a peer
  ledger's current signing authority, stored per Channel and updated only 
  via verified proofs.

CLPR organizes into four layers:

- **Network layer** — Channel establishment between two ledgers (permissionless,
  commit-reveal registration to prevent Channel ID squatting), the protocol for 
  syncing bundles between CLPR Endpoints of different ledgers, and the pluggable
  Verifier Contract interface that validates a peer ledger's state proofs and 
  decodes the bundled data for consumption by the CLPR Service.
- **Messaging layer** — an ordered, state-proven message queue per Channel. 
  Messages are arbitrary byte payloads batched into bundles and delivered with a
  cryptographic running-hash chain, so a bundle's proof extends trust across 
  every message it carries without individually proving each one.
- **Payment & routing layer** — Connectors: economic actors that provide payment
  for message execution on the destination ledger and are subject to slashing 
  for misbehavior. Connectors let applications choose their own economic backers
  for cross-chain delivery. The CLPR Service routes messages in bundles to the 
  appropriate destination applications.
- **Application layer** — The CLPR Application API is a minimal interface for 
  sending and receiving message payloads from remote applications. CLPR moves 
  data between applications on different ledgers, and it is up to the 
  applications to interpret and coordinate on the meaning of the messages. 
  All interledger asset transfers and smart contract calls are application 
  layer logic.

## Extensibility

When a new ledger type is added into the CLPR library of support, the following
elements must be developed:

1. A CLPR Service implementation that is either native or deployed as a smart 
   contract to the ledger. This CLPR Service implementation must conform to the 
   CLPR Service behavior outlined in the CLPR Specification.
2. CLPR Endpoints that read the local CLPR Service ledger state and construct 
   state-proven bundles in the data format of the source ledger. These CLPR 
   Endpoints must implement the common bundle sync protocol to exchange bundles 
   with the CLPR Endpoints of other ledgers. These Endpoints are also 
   responsible for rotating the trust anchor of the ledger in remote 
   Verifier Contracts.
3. Multiple Verifier Contract implementations, one for each target ledger type 
   supported. The Verifier Contracts are seeded with an updateable trust anchor
   that stores the source ledger's signing material used in verification of 
   state proofs coming from the source ledger. The Verifier Contracts are also 
   responsible for translating the data format of bundles from the source ledger
   to the destination ledger data format expected by the receiving CLPR Service.

The alignment between the source CLPR Endpoint bundle construction and the 
destination Verifier Contract translating the data format from the source 
ledger to the destination ledger format is the magic that allows interoperable 
extension to new ledger types without needing to modify the implementation of 
the destination CLPR Service. In creating a new Channel, the address of a new 
ledger's Verifier Contract is provided for use along with the remote ledger's 
CLPR Service configuration.

### Example Extension Process

Steps to add a new ledger type (Solana, Polygon, ICP, etc.) to communicate with 
Hiero.

1. Implement CLPR Service and CLPR Endpoints for the new ledger type.
2. Implement a Hiero Verifier Contract deployable to the new ledger type.
3. Implement a Verifier Contract for the new ledger type, deployable to Hiero.
4. Deploy the respective Verifier Contracts to the opposing networks.
5. Setup a new Channel between the CLPR Services of the two networks.
6. Share the CLPR Endpoints of the opposing network with each other.
7. Setup a common Connector to bond to the Channel.
8. Deploy CLPR applications configured to use the Connector and Channel to the 
   respective networks.

## Initial Contribution

All donated code is under the Apache 2.0 license.

The following codebases are provided as the initial OSS for CLPR:

- [https://github.com/hiero-hackers/CLPR-spec](https://github.com/hiero-hackers/CLPR-spec)
    - This repository contains the core CLPR specification detailing the 
      behavior of all components and the common data structures and formats.
    - This repository has a subdirectory called `ADR` which contains documented 
      proposals for how the spec has evolved prior to donation to the LFDT.
    - The CLPR specification will likely go through a couple more changes to 
      polish out some rough edges.
- [https://github.com/hiero-hackers/clpr-smart-contracts](https://github.com/hiero-hackers/clpr-smart-contracts)
    - This repository contains both the CLPR Service smart contracts and the 
      Verifier smart contracts written in Solidity and are deployable to Besu.
    - If this repository remains as the location where both the CLPR Service 
      and Verifier smart contracts live for all chains, it will likely need to 
      be reorganized by chain type.
- [https://github.com/hiero-hackers/clpr-evm-endpoint](https://github.com/hiero-hackers/clpr-evm-endpoint)
    - This repository contains a Java implementation of the CLPR Endpoint that 
      is able to read EVM chain state and submit EVM transactions to Besu 
      networks. It is implemented to manage the trust anchor updates for Besu 
      QBFT consensus in remote Verifier Contracts.
    - If CLPR Endpoints are implemented natively into the validators of a chain,
      then the code for the CLPR Endpoint would live in that ledger's 
      repository.
    - If a ledger is not implementing a native CLPR Service, then it doesn't
      matter what language the CLPR Endpoint supporting it is written in. This 
      Java based implementation can be refactored and organized to support 
      multiple ledger types.
- [https://github.com/hiero-ledger/hiero-consensus-node/pull/27029](https://github.com/hiero-ledger/hiero-consensus-node/pull/27029)
    - Approved by the Hedera Governing Council and pending approval by the 
      Hiero TSC, the Hiero native implementation of the CLPR Specification is 
      provided in the `clpr-feature` branch in the 
      `hiero-ledger/hiero-consensus-node` repository.
    - This branch will not be merged until all requirements and standards for 
      code hygiene, organization, testing, and documentation have been met.

# Effort and Resources

Hashgraph will continue to develop its own CLPR applications and continue to 
implement smart contract based CLPR implementations to deploy to target networks
according to its own business interests.

If the LFDT accepts CLPR as a Lab project, the Hedera Governing Council 
(via Hashgraph) will move its CLPR development into the public OSS repositories 
and collaborate with any and all community developers that want to join the CLPR
LFDT project.

CLPR will operate as a vendor-neutral LFDT project. Participation in 
specification development, implementation, governance, and maintenance will be
open to contributors regardless of organizational affiliation. No contributor 
or donating organization will hold exclusive authority over the specification 
or project roadmap by virtue of its initial contribution.

The LFDT will need to provide dedicated repositories with resources for building
and testing heterogeneous CLPR deployments. Hashgraph currently has arrangements
to coordinate on build and test resources for the Hiero Consensus Node and 
related Hiero repositories. Similar logistics and arrangements on resources are 
available for CLPR with Hashgraph.

Hashgraph and Hedera are initial maintainers, but we are eager to collaborate 
and share maintenance responsibilities with other contributing parties.

Hashgraph currently has allocated 4-5 developers per code repository it is 
donating. These numbers will likely sustain as the CLPR project matures and new 
implementations are developed and deployed to various ledgers.

Hashgraph and Hedera expect to participate actively in the initial governance 
and maintenance of the CLPR project through their contributing developers and 
maintainers. As the contributor community grows, project governance and 
maintainer participation will evolve in accordance with LFDT policies and the 
project's community governance processes.

It is hard to estimate the expected rate of growth for this project, but we 
believe the extensible architecture makes a lot of sense and will facilitate 
fast adoption.

At Hashgraph, there are minor in-flight changes to the CLPR Specification and 
pending software updates to the CLPR implementations. If the LFDT accepts CLPR
as a Lab project, a short grace period to finish polishing the CLPR 
Specification would be appreciated, but is not critical or necessary. We can 
propose changes under the desired governance structures established by the LFDT.

# How To

Each repository documents its own build, test, and deployment process in its 
README and `docs/` directory:

- `clpr-spec` — the specification and ADRs are plain Markdown; no build step.
- `clpr-smart-contracts` — Foundry-based; `forge build` / `forge test`, with a 
  vitest end-to-end harness against Anvil, Besu, and Hiero Solo backends.
- `clpr-evm-endpoint` — Gradle-based Java relay service, with unit, integration,
  and end-to-end test suites, plus a Helm chart for Kubernetes deployment.

More detailed tutorials and walkthroughs can be developed once the project 
proposal is accepted and the code reaches its new homes.

# References

1. `clpr-spec`: [https://github.com/hiero-hackers/CLPR-spec](https://github.com/hiero-hackers/CLPR-spec)
2. `clpr-smart-contracts`: [https://github.com/hiero-hackers/clpr-smart-contracts](https://github.com/hiero-hackers/clpr-smart-contracts)
3. `clpr-evm-endpoint`: [https://github.com/hiero-hackers/clpr-evm-endpoint](https://github.com/hiero-hackers/clpr-evm-endpoint)
4. `hiero native implementation`: [https://github.com/hiero-ledger/hiero-consensus-node/pull/27029](https://github.com/hiero-ledger/hiero-consensus-node/pull/27029)
5. `HIP-1535`: [https://github.com/hiero-ledger/hiero-improvement-proposals/pull/1535](https://github.com/hiero-ledger/hiero-improvement-proposals/pull/1535)

# Closure

Success for the LFDT CLPR Lab will be measurable across a variety of dimensions:

- Additional interested parties join the CLPR LFDT project to help curate the 
  CLPR Specification and develop reference implementations.
- A scalable repository structure is implemented to handle the variety of 
  implementations for different ledger types.
- Educational literature and orienting tutorials are developed to help ramp 
  up new community participants.
- A cooperative ethos is anchored in the CLPR Development community, measurable 
  by feedback from new participants and visitors.
- CLPR Application Libraries are developed to provide the boilerplate code 
  needed by all CLPR applications.
- New ventures form to create CLPR Applications and operate CLPR Endpoints
  and Connectors to facilitate messaging across Channels.