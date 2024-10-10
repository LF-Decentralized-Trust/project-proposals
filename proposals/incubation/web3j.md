---
layout: default
title: Web3j
parent: Incubation
grand_parent: Project Proposals
---

# HIP Identifier

Hyperledger Web3j v1.0

# Sponsor(s)

- Conor Svensson [<conor@web3labs.com>](mailto:conor@web3labs.com)
- Christian Felde [<christian@web3labs.com>](mailto:christian@web3labs.com)
- George Ţebrean [<george@web3labs.com>](mailto:george@web3labs.com)
- Nischal Sharma [<nischal@web3labs.com>](mailto:nischal@web3labs.com)

# Abstract

Web3j is the Ethereum integration library for the Java and Android platforms.

# Context

Web3j was first created back in 2016 out of the need to simplify working with Ethereum networks using the Java and Android platforms (collectively referred to as the JVM from herein).

![Web3j provides the plumbing for developing on Ethereum](https://github.com/web3j/web3j-docs/blob/main/docs/img/web3j_network.png?raw=true)

Web3j's original author had spent more then a decade of their career working on large institutional financial systems on the JVM, which made them appreciated how much of our modern enterprise infrastructure was built on this platform. 

With all of the interest in blockchain technology in enterprise, it seemed like a natural area to focus on — making it as simple as possible for enterprise developers to integrate with the leading blockchain network Ethereum.

In the 7 years since Web3j's initial creation a vibrant community has been built. Key project metrics include:

- 4.8k GitHub stars
- 192 contributors
- 106 releases
- 1.7k forks
- Over 1000 resolved issues
- Over 2 million downloads

Web3j is a successful open source project and a key piece of open source infrastructure for the Ethereum ecosystem. However, the projects original creator wants to ensure that Web3j ultimately  resides within a foundation that can ensure that Web3j thrives for the long term without being directly tied to Web3 Labs.

With the Hyperledger Foundation's role as the leading ecosystem for enterprise-grade blockchain technology, there is no better place for Web3j to reside long term.

# Dependent Projects

Web3j requires an Ethereum compatible network to run. It works natively with any Ethereum node software that implements the execution client [JSON-RPC specification](https://ethereum.github.io/execution-apis/api-documentation/). 

This includes Ethereum clients such as Hyperledger Besu, Quorum, and Geth, as well as appchain and layer two clients such as the OP Stack, Linea and Polygon ZK-EVM.

As both Web3j and Hyperledger Besu run on the JVM, there are a number of existing dependencies between the two projects.

Hyperledger Besu makes use of Web3j in a [number of areas](https://github.com/search?q=repo%3Ahyperledger%2Fbesu%20web3j&type=code), including using its Ethereum ABI type implementations and in its acceptance tests. Web3j makes use of Hyperledger Besu's EVM implementation within its unit testing framework Web3j Unit. This facilitates unit testing of Solidity smart contracts within Web3j projects.

# Motivation

When developers wish to integrate with Ethereum based infrastructure, they are typically trying to accomplish one of the following:

1. Query a blockchain node to obtain information about on-chain activities
2. Deploy smart contracts
3. Transact with or query data from deployed smart contracts
4. Create wallets
5. Send Ether from one wallet to another

Prior to the creation of Web3j, there was no straightforward way to accomplish any of the above on the JVM. Developers would need to develop their own code to provide the following functionality:

- Implement the JSON-RPC protocol for communicating with Ethereum nodes
- Perform type conversion for deploying, transacting with and reading data from smart contracts
- Working with Ethereum's Secp256k1 elliptic curve for signing transactions

Web3j was created originally with the goal of addressing these needs for users. However, over time its scope grew to address some of the challenges with the overall development workflow when working with smart contracts on the JVM:

- Scaffolding Solidity projects
- Providing an integrated developer experience
- A lack of unit and integration testing capabilities

The specific components of Web3j and how it addresses these items are addressed in subsequent sections below.

For further historical context on Web3j, you can read the [following post I wrote](https://web3perspectives.com/p/building-open-source-software-web3j) on the creation of the project earlier the year.

# Status

Proposal

# Solution

Web3j is made up of a number of components. It was designed to be as accessible as possible to developers, and the design of these components reflects this.

In order to bring the greatest benefit to its users, the expectation is these components collectively would make up the Hyperledger Web3j project.

These components are as follows:

- The core Web3j library provides the Ethereum integration capabilities to support use cases that utilise the JSON-RPC protocol and smart contracts
- Smart contract testing components that allow users to develop and test Solidity smart contracts within their JVM project workflow
- Build plugins that integrate the Solidity compiler and Solidity library dependencies within the JVM project
- A command line interface (CLI) to simplify working with Web3j

These are discussed in further detail below.

## Core Web3j library

The [core Web3j library](https://github.com/web3j/web3j) was designed to be highly modular, so that users could easily incorporate the minimal parts of the library for their projects. This consideration was especially important in servicing the Android community.

The notable modules include:

- **rlp:** [Recursive Length Prefix (RLP)](https://ethereum.org/en/developers/docs/data-structures-and-encoding/rlp/) serialisation
- **crypto:** cryptographic operations and key management 
- **abi:** [Contract Application Binary Interface (ABI)](https://docs.soliditylang.org/en/latest/abi-spec.html) encoding and decoding
- core: core Web3j components including the JSON-RPC implementation and abstractions for wallets
- utils: utility functions including type conversions
- **besu, geth, eea: Ethereum** client specific functionality
- codegen: code generators for creating Java type wrappers for Solidity smart contracts
- contracts: smart contract specific types

## Smart Contract Testing

The Web3j core library is complemented by the following projects that facilitate unit and integration testing of Solidity smart contracts.

The [Web3j EVM](https://github.com/web3j/web3j-evm) project provides an embedded EVM that allows developers to write applications that simulate transactions taking place on the EVM. 

The EVM contained within the project is the Hyperledger Besu EVM. This ensures that the EVM can be run within the local JVM without the need to orchestrate a full Ethereum node via Docker or similar tools.

One of the significant advantages of using the Hyperledger Besu EVM is that developers work with a production-grade EVM during the development process. In other non-JVM development environments, it's unlikely that developers will have at their disposal an embedded EVM that uses the same code as a widely used Ethereum client.

The Web3j EVM project is complemented by the [Web3j Unit](https://github.com/web3j/web3j-unit) project. This project is used to inject different EVM environments into unit and integration tests.

This allows developers to transact with real Ethereum execution environments from their unit tests. The most common use cases are smart contract deployments and interacting with them, but any type of EVM transaction can be performed.

By default the Web3j unit project uses the embedded Hyperledger Besu EVM for this purpose to ensure fast execution time. However, it is also possible to use containerised instances of Ethereum execution clients such as Hyperledger Besu and Geth for this purpose. This is especially useful for integration testing purposes to simulate production environments.

## Build Plugins

The JVM platform utilised two major build systems — Gradle and Maven. The [Web3j Gradle](https://github.com/web3j/web3j-gradle-plugin) and [Web3j Maven](https://github.com/web3j/web3j-maven-plugin) projects implement support for these build systems.

One of the complexities that developers face when working with smart contract development is the need for a separate Solidity compilation environment. 

When working with these plugins they install the the most recent version of the Solidity compiler that is appropriate for your project, enabling the compilation of any Solidity source files at build time.

Following the Solidity build process, these build plugins generate Java wrappers for integrating with these smart contracts using Web3j.

This enables the development process to remain within the developers JVM environment, resulting in no additional installations apart from the Java Development Kit (JDK) or Android equivalent.

In addition, there may be opportunities to integrate the build plugins with Hyperledger Solang which could be explored.

## CLI

Web3j also comes with a [CLI](https://github.com/web3j/web3j-cli) providing a number of different functions including:

- Scaffolding new Web3j projects
- Generating wallets
- Generating smart contract wrappers

The intent behind the CLI is that it enables users to get up and running with Web3j using the smallest number of possible steps. Creating a new Java project using the build plugins is straight forward for experienced Java developers, but we want to minimise barriers to entry for the project.

# Effort and Resources

It is our hope that in becoming a Hyperledger project, Web3j will gain additional maintainers beyond just the core Web3 Labs team, which includes the following individuals:

- Christian Felde
- George Ţebrean
- Nischal Sharma

This team is adequate to continue to maintain and support the project, but in growing the contributor and maintainer base we expect the growth of the project to accelerate further.

We've already started to talk to Hyperledger staff about how to work with them to support our goals of bringing in new contributors and maintainers.

A number of organisations have contributed to the project in the past. It's not clear from GitHub profiles alone which have. However, pull requests have been submitted by numerous staff at ConsenSys over the years.

# How To

The simplest way to work with Web3j is to create a new project. We provide this functionality using the Web3j CLI. This latter can be installed as follows:

For Unix:

```
curl -L get.web3j.io | sh && source ~/.web3j/source.sh
```

For Windows, in Powershell:

```
Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://raw.githubusercontent.com/web3j/web3j-installer/master/installer.ps1'))
```

Create a new project by running:

```
$ web3j new 
```

For building and development on the Web3j codebase, there are [build instructions](https://github.com/web3j/web3j#build-instructions) on the project home page.

# References

https://github.com/web3j/web3j/
https://github.com/web3j/web3j-evm
https://github.com/web3j/web3j-unit
https://github.com/web3j/web3j-gradle-plugin
https://github.com/web3j/web3j-maven-plugin
https://github.com/web3j/web3j-cli
https://docs.web3j.io/

# Closure

For enterprise developers wishing to develop native Ethereum applications on the JVM Web3j is an essential piece of plumbing. 

Within the Hyperledger Foundation, given the close synergies with Hyperledger Besu, we hope to grow Web3j's adoption further within the enterprise landscape and see many more projects reach production being built on it.
