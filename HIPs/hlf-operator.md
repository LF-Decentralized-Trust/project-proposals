---
layout: default
title: Hyperledger Fabric Operator Proposal
parent: Hyperledger Improvement Proposals
---

# HIP Identifier
[HIPs/hlf-operator.md](./hlf-operator.md)

# Sponsor(s)

- David Viejo [<dviejo@kfs.es>](mailto:dviejo@kfs.es)
- Carlo Innocenti [carlo.innocenti@oracle.com](mailto:carlo.innocenti@oracle.com)

# Abstract
HLF Operator is a Kubernetes operator that helps simplify the deployments of Hyperledger Fabric in Kubernetes. It is based on the Hyperledger Fabric Helm charts and provides a Kubernetes native way to deploy and manage Hyperledger Fabric networks.

# Context

There are many ways to deploy Hyperledger Fabric, but most of the alternatives focus on Docker and manually performed deployments, not to mention there's no support to perform operations like:

- Renewal of the certificates
- Upgrades
- Channel management

HLF-operator solves this by 

<mark>_**Context** if any, what is this project derived from? What if any
is it related to?_
</mark>

# Dependent Projects

Hyperledger Fabric Operator only requires **Hyperledger Fabric** to run.

# Motivation

When building Hyperledger Fabric networks, there are a number of barries to start using and deploying Hyperledger Fabric:
- How do I deploy a network in Kubernetes?
- How do I manage the certificate authorities/peers/orderers in a production environment?
- How do I renew the certificates?


# Status
Proposal

# Solution
<mark>_**Solution** to the problem addressed in the motivation section. Try
to make this as detailed as possible. The topics given below are
just suggestions, address only if they are relevant to your problem:_

-   _Transactions- including types, confidentiality, signing,
    traceability, identity of participants, contracts (scripts)_

-   _Effects on User facing Clients that help with transaction
    formation (similar to Wallets in BTC)_

-   _Effects on the network, throughput, visibility to other
    participants, change in protocol if any, criteria for network
    participation_

-   _Block formation and ledger formation: Consensus algorithm, size
    overhead, effects on the throughput and rate_

-   _Backward compatibility (hard fork or updates by all network
    participants needed?)_

-   _Rough design and scenarios on the probable effects, if any_

-   _The use of diagrams is encouraged to elucidate concepts_

-   _Address any possible objections and also support that came up
    during seed proposal from technical community on the lists._

-   _Traceability, testing criteria to gauge effects on installed
    base._

-   _License of codebase (including dependencies)_

-   _Any trademarks used in the project name or codebase?_
</mark>

# Effort and Resources
<mark>_**Effort and resources** committed (coders and any other resources
that are needed) and timeline._
</mark>

# How To

There's a guide in the documentation of the project that shows how to deploy a sample network in a KinD cluster:

[https://labs.hyperledger.org/hlf-operator/docs/getting-started](https://labs.hyperledger.org/hlf-operator/docs/getting-started)


# References
N/A

# Closure

The goal of Hyperledger Fabric Operator is to speed up the adoption of Hyperledger Fabric and ease the management of HLF networks at scale. The success of the project can be measured by the community on Discord, companies using it and meetups/videos on youtube about this project.
