Contributing to U°OS
====================

Table of Contents
-----------------

* [Introduction](#introduction)
* [Project Repositories](#repos)
* [Working with Issues](#issues)
* [Working with UIPs](#uips)
* [Documentation](#docs)
* [Developer Environment](#environment)
* [Testing](#testing)
* [Submitting Changes](#commits)
* [Coding Conventions](#codestyle)
* [Code of Conduct](#conduct)
* [List of Releases](#releases)
* [Running up a Block Producer Node](#bpnode)
* [Running a Calculator Node](#calcnode)
* [Licensing](#license)
* [Communication](#communication)

Introduction <a name="introduction"></a>
----------------------------------------

### Intended audience

* Project contributors
* App developers
* Dapp developers
* Issue reporters
* Improvement reporters

### Core components:

* Block Producer Node
* Calculator Node

U°Community is deployed as a dapp and has a fronted and a backend for interface.

Project Repositories <a name="repos"></a>
-----------------------------------------

* [ucom.frontend](https://github.com/UOSnetwork/ucom.frontend) — U°Community frontend
* [singularity](https://github.com/UOSnetwork/singularity) — DPOI
* [ucom.backend](https://github.com/UOSnetwork/ucom.backend) — U°Community backend
* [ucom.libs.social.transactions](https://github.com/UOSnetwork/ucom.libs.social.transactions) — U°Community user transactions on U°OS
* [ucom.libs.wallet](https://github.com/UOSnetwork/ucom.libs.wallet) — U°Community wallet for U°OS
* [uos.plugins](https://github.com/UOSnetwork/uos.plugins) — Rate of entities on U°OS. Entities: posts, articles, comments, users, organizations, communities. Also displayed on U°Community.
* [uos](https://github.com/UOSnetwork/uos) — U°OS blockchain software
* [uos.docs](https://github.com/UOSnetwork/uos.docs) — U°OS Framework documentation repository
* [uos.uip](https://github.com/UOSnetwork/uos.uip) — U°OS Network improvement proposals
* [ucom.uip](https://github.com/UOSnetwork/ucom.uip) — U°Community improvement proposals
* [mongo-c-driver](https://github.com/UOSnetwork/mongo-c-driver) — A cross-platform MongoDB client library for C. Used as part of the U°OS project to provide library compatibility to cache account names.
* [uos.contracts](https://github.com/UOSnetwork/uos.contracts) — U°OS Network contracts for entity rates
* [tribute](https://github.com/UOSnetwork/tribute) — User mentions for U°Community
* [ucom.libs.graphql-schemas](https://github.com/UOSnetwork/ucom.libs.graphql-schemas) — GraphQL schemas library to reuse between different services
* [UOSTracker](https://github.com/UOSnetwork/UOSTracker) — U°OS block explorer
* [UOS-Web-Wallet](https://github.com/UOSnetwork/UOS-Web-Wallet) — U°OS web wallet
* [uos.landing](https://github.com/UOSnetwork/uos.landing) — U°OS landing page at https://uos.network/
* [uos.libs](https://github.com/UOSnetwork/uos.libs) — DEPRECATED

Working with Issues <a name="issues"></a>
-----------------------------------------

### Issue tracker

Click ``Issues`` in the repository to see the reported issues.

### Submitting an Issue

See [Issue Template](issue_template.md).

Working with UIPs <a name="uips"></a>
-------------------------------------

UIP is short for U°OS Improvement Proposal.

A UIP is what you submit to improve the U°OS protocol. A UIP is always a community decision and must go through a detailed discussion with the community members.

### UIP tracker

UIPs are tracked in the [uos.uip](https://github.com/UOSnetwork/uos.uip) repository.

### Submitting a UIP

Submit a UIP as a pull request to the UIP repository: github/UOSnetwork/repo/

See [UIP Template](../../../uos.uip/blob/master/uip_template.md).

Documentation <a name="docs"></a>
---------------------------------

[U°OS and U°Community documentation hub](https://uos.readme.io).

Developer Environment <a name="environment"></a>
------------------------------------------------

Check README.md of each repository.

Testing <a name="testing"></a>
------------------------------

Check README.md of each repository.

Submitting Changes <a name="commits"></a>
-----------------------------------------

### Intent

The goals of contributing to U°OS:

* Maintain the quality of code, developer experience, user experience
* Fix issues
* Engage the community to make the best possible U°OS

### Instructions

#### Commit messages

See [Commit Message Style Guide](commit_message.md).

#### Fixing a bug

1. Check the [Issue Tracker](#issues) first to see if the bug's been reported and/or fixed.
2. If the bug hasn't been submitted yet, submit it first.
3. Write a comment in the issue tracker that you are working on the bug.
4. Submit your fix in accordance with the regular [GitHub flow](https://help.github.com/articles/github-flow/).

Coding Conventions <a name="codestyle"></a>
-------------------------------------------

* [EOSIO Coding Standards](https://developers.eos.io/eosio-home/docs/coding-standards)
* [JavaScript](https://standardjs.com/)
* [React](https://github.com/airbnb/javascript/tree/master/react)

Code of Conduct <a name="conduct"></a>
--------------------------------------

See [Code of Conduct](code_of_conduct.md).

List of Releases <a name="releases"></a>
----------------------------------------

See [Releases and Release Notes](releases.md).

Running a Block Producer Node <a name="bpnode"></a>
---------------------------------------------------

For a detailed walkthrough see [Spinning up a Block Producer Node on Ubuntu](uosBPubuntu.md).

Running a Calculator Node <a name="bpnode"></a>
-----------------------------------------------

For a detailed walkthrough see [Starting a U°OS Calculator Node](https://u.community/posts/5658).

Licensing <a name="license"></a>
--------------------------------
Both U°OS and U°Community are open source and under public licensing. For details, check the LICENSE.md file in each repository.

Communication <a name="communication"></a>
------------------------------------------

* Gitter: [UOS-Dev](https://gitter.im/UOS-Dev/)
* Telegram: [UOS Network Chat](https://t.me/uos_network_en)
* Discord: [UOS Network Chat](https://discord.gg/Bcq2Q5C)
