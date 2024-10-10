---
layout: default
title: Xkey
parent: Incubation
grand_parent: Project Proposals
---

# HIP Identifier
Xkey HIP v0.1

# Sponsor(s)
* Dfns (research@dfns.co)

# Abstract
This initiative aims to establish an ecosystem for threshold signing schemes (TSS) 
and multi-party computations (MPC) in general.

# Context
Signing schemes are a crucial part of our daily technology. They power systems like 
TLS, code signing, wallets, blockchains and others.

In basic cryptography, signing schemes use a pair of keys: a private key and a public key. 
The private key signs messages, and the public key verifies the signature.

Keeping the private key secret is essential. If it's leaked, it can lead to serious 
problems, like someone stealing all the funds in a crypto wallet. Losing the private key 
is also a big issue, as it can result in permanent loss of access to funds.

To manage these risks, we can use Threshold Signing Schemes (TSS). TSS is an advanced 
method that uses multiple private key shares among multiple participants. In a t-out-of-n 
scheme, `n` signers share the key, and any `t` of them can work together to sign a message. 
This setup offers unique security benefits: an attacker can compromise up to `t-1` signers 
without learning anything about the private key. Also, up to `n-t` signers can fail without 
affecting service availability.

However, TSS protocols are complex. The cryptographic principles behind them are hard to 
understand, and their implementation adds more layers of complexity. TSS protocols are 
usually multi-round and require synchronous communication with authenticated and encrypted 
channels. Their state progresses gradually as they receive messages. Therefore, implementing 
TSS involves intricate boilerplate code, making it difficult to audit.

# Dependent Projects
None

# Motivation
When we implemented a TSS ECDSA protocol, we noticed a lack of tools and frameworks available 
in the community. Most TSS implementations either rewrite a state machine from scratch to 
drive protocol execution or offer low-level functions, requiring manual protocol handling. 
This results in boilerplate code that is difficult to read and maintain.

Our goal is to build an ecosystem with:
* A framework for writing MPC protocols, reducing boilerplate and making the code easy to
  write and read.
* A library for generic elliptic curve cryptography, enabling seamless curve switching and
  secure arithmetic operations, while managing small subgroups and memory security.
* Common primitives and ZK proofs like Schnorr Proof of Knowledge, unambiguous hashing,
  secret sharing, and more.
* Applied libraries like fast Paillier encryption, using CRT to speed up (de)encryption
  and homomorphic operations, among others.

The ultimate goal of this proposal is to make developing and maintaining TSS/MPC protocols 
easier. We want to improve their reliability, readability, and security because we believe 
these are the safest and most feature-rich ways to protect and move digital assets.

# Status
Proposed for Incubation

# Solution
We developed following crates in Rust:

* A framework called [`round-based`] that allows implementing MPC as a single function.
  It abstracts away communication layer, and provides reusable tools for dealing with
  MPC-specific types of communications.
* Library for generic elliptic curve cryptography [`generic-ec`]. It allows writing code
  generic over choice of curve, provides advanced tools like multiscalar multiplication.
  It was designed with security in mind: it's resistent to small-group attacks, and it
  provides things like `SecretScalar` which stores secrets on heap and zeroizes it when
  it's not used anymore.
  * [`generic-ec-zkp`] provides ZK proofs and tools based on `generic-ec` crate
  * [`stark-curve`] exposes a pure Rust implementation of stark curve
* [`slip-10`] is a crate for HD-wallet derivation that follows [slip10][slip10-spec]
  standard (which is compatible with [bip32][bip32-spec])
* [`udigest`] is a library for unambiguous hashing of structured data
* [`fast-paillier`] contains fast implementation of paillier encryption that contains
  optimizations such as using Chinese Remainder Theorem (CRT) when private key is known
* And, finally, [`cggmp21`], an audited implementation of threshold ECDSA protocol based
  on [CGGMP21 paper][cggmp21-paper].

Currently in development:
* An implementation of threshold Schnorr/EdDSA protocol following the
  [FROST IETF draft][frost-draft].
* Tools for running TSS in enclaves

[`round-based`]: https://github.com/dfns/round-based
[`generic-ec`]: https://github.com/dfns/generic-ec
[`generic-ec-zkp`]: https://docs.rs/generic-ec-zkp
[`stark-curve`]: https://github.com/dfns/stark-curve
[`slip-10`]: https://github.com/dfns/slip-10
[`udigest`]: https://github.com/dfns/udigest
[`fast-paillier`]: https://github.com/dfns/fast-paillier
[`cggmp21`]: https://github.com/dfns/cggmp21

[cggmp21-paper]: https://eprint.iacr.org/2021/060 
[frost-draft]: https://datatracker.ietf.org/doc/html/draft-irtf-cfrg-frost-15

[slip10-spec]: https://github.com/satoshilabs/slips/blob/master/slip-0010.md
[bip32-spec]: https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki

All our work listed above is currently licensed under dual MIT or Apache-2.0 licenses. 
We're planning on relicensing the code to Apache-2.0 only.

# Effort and Resources
All crates above were reviewed, developed and are maintained by Dfns' research team, 
which currently includes two full-time engineers and one part-time cryptographer:

* Denis Varlakov (denis@dfns.co)
* Nikita Sorokovikov (nikita@dfns.co)
* Dr. Jonathan Katz (jkatz@dfns.co)

# How To
All crates are available on crates.io. Each library is extensively documented, 
rendered documentation is available on docs.rs.

# References
* Ran Canetti, Rosario Gennaro, Steven Goldfeder, Nikolaos Makriyannis, and Udi Peled. UC
  Non-Interactive, Proactive, Threshold ECDSA with Identifiable Aborts. Cryptology ePrint
  Archive, Paper 2021/060, 2021. Available at https://eprint.iacr.org/2021/060.
* Deirdre Connolly, Chelsea Komlo, Ian Goldberg, and Christopher A. Wood. Two-Round Threshold
  Schnorr Signatures with FROST. Internet Engineering Task Force, draft-irtf-cfrg-frost-15.
  Available at https://datatracker.ietf.org/doc/html/draft-irtf-cfrg-frost-15.
* Jochen Hoenicke and Pavol Rusnak. Universal private key derivation from master private key.
  Available at https://github.com/satoshilabs/slips/blob/master/slip-0010.md.
* Pieter Wuille. Hierarchical Deterministic Wallets. Available at 
  https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki

# Closure
Project success can be measured by how many other libraries use the developed ecosystem.
