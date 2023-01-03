---
leap: 43
title: Kwenta Hosting Pilot
status: Draft
author: Leifu Chen (@LeifuChen), Burt Rock (@BurtRock)
created: 2022-12-30
---

<!--You can leave these HTML comments in your merged LEAP and delete the visible duplicate text guides, they will not appear and may be helpful to refer to if you edit it again. This is the suggested template for new LEAPs. Note that a LEAP number will be assigned by an editor. When opening a pull request to submit your LEAP, please use an abbreviated title in the filename, `leap-draft_title_abbrev.md`. The title should be 44 characters or less.-->

## Simple Summary
<!--"If you can't explain it simply, you don't understand it well enough." Simply describe the outcome the proposed changes intends to achieve. This should be non-technical and accessible to a casual community member.-->
This proposal allows KwentaDAO to host a front end for Lyra’s options as part of the Kwenta exchange for a period of 6 months. 400,000 LYRA will be provided to the Kwenta DAO to incentivize hosting and align the DAOs.

Prior to the end of the 6 month pilot, the terms of the partnership between Kwenta and Lyra should be evaluated and continued or amended in a subsequent LEAP.

## Abstract
<!--A short (~200 word) description of the proposed change, the abstract should clearly describe the proposed change. This is what *will* be done if the LEAP is implemented, not *why* it should be done or *how* it will be done. If the LEAP proposes deploying a new contract, write, "we propose to deploy a new contract that will do x".-->
As the first interface deployer, Kwenta will receive priority support to host a Lyra interface. The Lyra team will continue to assist in updates for the duration of the 6 month period. The user interface will be rebranded as `Kwenta` instead of `Lyra` with an additional label `powered by Lyra`. The interface will retain all existing functionality under this rebranding.

## Motivation
<!--This is the problem statement. This is the *why* of the LEAP. It should clearly explain *why* the current state of the protocol is inadequate.  It is critical that you explain *why* the change is needed, if the LEAP proposes changing how something is calculated, you must address *why* the current calculation is innaccurate or wrong. This is not the place to describe how the LEAP will address the issue!-->
As Lyra’s protocol grows more complex and the number of integrations expands, the Lyra team should be able to focus on back end development and support for integrators to maximize use cases for Lyra options.

Since options exchanges in traditional finance are typically part of a suite of spot and derivatives trading tools, moving Lyra’s options trading experience out of isolation would expand the reach and appeal of Lyra’s product. Kwenta is a project focused on providing a UI and tooling for a variety of spot and derivatives offerings on Optimism, and is an ideal context in which to place Lyra’s offerings.

For the duration of the agreement, Kwenta DAO's responsibilities will include, and be limited to, the operation of the interface as outlined in this proposal. Kwenta DAO will not charge any additional fees for users accessing the Lyra interface unless specified as part of a future integration or partnership agreement.

## Specification
<!--The specification should describe the syntax and semantics of any new feature, there are five sections
1. Overview
2. Rationale
3. Technical Specification
4. Test Cases
5. Configurable Values
-->

### Overview
<!--This is a high level overview of *how* the LEAP will solve the problem. The overview should clearly describe how the new feature will be implemented.-->
A collaboration between Lyra DAO and Kwenta DAO to execute the pilot hosting will help Lyra establish a viable long term approach to the hosting of an options trading front end. By providing an incentive in the form of Lyra tokens and a period of priority support, Lyra can ensure a smooth transition to independent 3rd party hosting.

### Technical Specification
<!--The technical specification should outline the public API of the changes proposed. That is, changes to any of the interfaces Lyra currently exposes or the creations of new ones.-->
- The Lyra user interface will be rebranded as `Kwenta` instead of `Lyra`. 
- The label `powered by Lyra` will be presented on the UI to clarify the distinction.
- The Lyra team will provide update support for 6 months.

### Configurable Values
<!--Please list all values configurable under this implementation.-->
```
Length of the hosting period = 6 months
Incentive for the hosting = 400,000 LYRA
```
## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
