---
layout: default
title: Project Proposal Process
nav_order: 1
has_children: true
---

# Project Proposal Process

A **Project** at LF Decentralized Trust is a collection of specific Maintainers,
users and other developers, code, releases, issues, and other activity
oriented around a common software-implemented mission.

This project proposal template ushers originators, designers,
implementers, and testers of a project through community and TAC approval.
The proposal should evolve organically as it moves through the
stages of conception, design, approval, implementation and deployment.
The project and hence the proposal may also need several iterations. In
its terminal forms it can also serve as a short manual to the features
of the project for users.

This proposal template is descriptive and not normative, a guide rather
than the law. Prior templates like the internet RFC process, Bitcoin
Improvement Proposal, Python Improvement Proposal etc. were used as
guidelines to develop this template.

The seed of a new project has to be vetted in a public forum like
the [TAC mailing list](https://lists.lfdecentralizedtrust.org/g/tac/topics)
before creating a project proposal. It is best if the project has
technical champions who believe in the project and are
the maintainers of the project. The technical champions can change in
the middle of the project.

If this project proposal is for a feature that is unique to an existing
LF Decentralized Trust project, please reach out to that project's TSC
to see about joining that project instead of creating a new project proposal.
If discussion with the existing project community leads to not joining,
then the proposal will be reviewed on its own merits as an independent
project. Please note in the proposal the conversations with that project
and the reason for not joining their efforts.

Please note that readability is very important. The language of the
proposal should be English if possible as that is the lingua franca of
the community. The Chicago Manual Of Style should be followed for
explanation of abbreviations, references etc. This is extremely
important as a clear statement of the problem and its technical details
are helpful to coalesce the community around a solution and prompt
volunteers. The outline of a project is given below with comments on the
sections.

-   **Identifier** a short description plus a serial number with a
    version (for example this document is Template for a Project 0.3)

-   **Sponsor(s)** name and contact details including email address

-   **Abstract** (less than 50 word) description of the project.

-   **Context** if any, what is this project derived from? What if any
    is it related to?

-   **Dependent Projects** if any, must be listed, and each dependent
    project\'s maintainers must sign off on the proposal before it is
    considered by the TAC. **NOTE: If this project proposal is unique
    to an existing project, please discuss including this
    feature with that project's TSC.**

-   **Motivation** for this project; a longer justification of the
    project. This may be a couple of hundred words. Why is this
    project better at solving a problem compared to parallel proposals
    or implemented projects?

-   **Status** of the project: See [lifecycle documentation].

[lifecycle documentation]: https://lf-decentralized-trust.github.io/governance/governing-documents/project-lifecycle.html

-   **Solution** to the problem addressed in the motivation section. Try
    to make this as detailed as possible. The topics given below are
    just suggestions, address only if they are relevant to your problem:

    -   Transactions - including types, confidentiality, signing,
        traceability, identity of participants, contracts (scripts)

    -   Effects on User facing Clients that help with transaction
        formation (similar to Wallets in BTC)

    -   Effects on the network, throughput, visibility to other
        participants, change in protocol if any, criteria for network
        participation

    -   Block formation and ledger formation: Consensus algorithm, size
        overhead, effects on the throughput and rate

    -   Backward compatibility (hard fork or updates by all network
        participants needed?)

    -   Rough design and scenarios on the probable effects, if any

    -   The use of diagrams is encouraged to elucidate concepts

    -   Address any possible objections and also support that came up
        during seed proposal from technical community on the lists.

    -   Traceability, testing criteria to gauge effects on installed
        base.

    -   License of code base (including dependencies)

    -   Any trademarks used in the project name or codebase

-   **Effort and resources** committed (coders and any other resources
    that are needed) and timeline.

-   **How to**: How to host and test the project. How to deploy and use.
    How does one know that it works.

-   **References**. See [citation guide](http://www.chicagomanualofstyle.org/tools_citationguide.html)

-   **Closure** how do we know that the project succeeded. This has to
    be measurable if possible. Make references to successor projects if
    any.
