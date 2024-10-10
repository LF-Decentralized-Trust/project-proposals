---
layout: default
title: Mechanical Process
parent: Project Proposal Process
---

# Mechanical Process

The Project Proposal process is intended to provide a consistent and controlled 
path for new projects to join LF Decentralized Trust.

## Process to propose a project

1. Fork [this repository](https://github.com/lf-decentralized-trust/project-proposals/).

2. Fill out the [Proposal Template](https://github.com/lf-decentralized-trust/project-proposals/blob/gh-pages/proposals/0000-template.md) 
and save it into the `proposals` subdirectory under the name of your project,
such as `mynewproject.md`.

4. Commit your changes with proper sign-off. This means that your commit
log message must contain a line that looks like the following one,
with your actual name and email address:

        Signed-off-by: John Doe <john.doe@example.com>

   Adding the `-s` flag to your `git commit` command will add that line
automatically. You can also add it manually as part of your commit
log message or add it afterwards with `git commit --amend -s`.

5. Submit a Pull Request.

## Bringing in an existing repository


By default LF Decentralized Trust will create a new respository for you to
start from but if you have an existing GitHub repo you would like to
bring to your proposed project you have the option to request for that
repo to be reused instead. This is however only possible if every
commit in your existing repo is signed-off so there is no 
[DCO](https://developercertificate.org/) related issues. If that is 
not the case, you will need to bring your code by squashing all of 
your commits into a single first commit made against your new lab 
repo with your sign-off.
