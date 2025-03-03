---
layout: default
title: 2024 Annual Review Hyperledger Indy
parent: 2024
grand_parent: Project Updates
---

# 2024 Annual Review Hyperledger Indy

## Project Health

Hyperledger Indy LFX Insights Page for [Calendar Year 2023](https://insights.lfx.linuxfoundation.org/foundation/hyp/overview?project=indy&repository=all&dateFilters=2023-01-01%20to%202023-12-31&dateRange=2023-01-01%20to%202023-12-31&compare=PP&granularity=month&hideBots=true) (v. [2022](https://insights.lfx.linuxfoundation.org/foundation/hyp/overview?project=indy&repository=all&dateFilters=2022-01-01%20to%202022-12-31&dateRange=2022-01-01%20to%202022-12-31&compare=PP&granularity=month&hideBots=true))  and for [Q1 2024 Oct-Dec.](https://insights.lfx.linuxfoundation.org/foundation/hyp/overview?project=indy&repository=all&dateFilters=2023-10-01%20to%202023-12-31&dateRange=2023-10-01%20to%202023-12-31&compare=PP&granularity=month&hideBots=true) (v. [Q4 2023](https://insights.lfx.linuxfoundation.org/foundation/hyp/overview?project=indy&repository=all&dateFilters=2023-07-01%20to%202023-09-30&dateRange=2023-07-01%20to%202023-09-30&compare=PP&granularity=month&hideBots=true)).

Compared to 2022, the Pull Request count was down by about 25% to 189 for the year, while the number of contributors was slightly higher, up about 20% to 46. Compared to Q4 2023, the Q1 2024 report changes had the same ratios — down about 25% (to 24) in Pull Requests, up about 20% in contributors (to 13).

While the existing implementation of Indy is extremely stable, and robust — for example, the Sovrin Foundation has been running its networks for 6 years, with 100% uptime since Feb. 2020 — there has been relatively little substantially new functionality added in some time. That may be changing as, in the latter half of 2023, the idea of “Indy Besu” was raised and a successful PoC developed, demonstrating implementing Indy’s public-permissioned network model on top of a Besu network. Progress has already been good in 2024 with the Indy community agreeing on the creation of the [Indy Besu repository](https://github.com/hyperledger/indy-besu) that further moves the implementation forward.

Indy Besu is a set of independent smart contracts. The main idea here is a modular system (modules list below) that allows deploying smart contracts at any time for:

- permissioned Indy network (new or migration of existing ones)
- existing Besu networks
- existing or new Ethereum permissionless networks

Modules:

- Network Permissions:
  - [Auth](https://github.com/hyperledger/indy-besu/blob/main/docs/design/auth.md) - control user permissions
    - role control - manage roles assigned to accounts  
    - access control - first level validation about whether to accept write transactions (execute target contract method) from a given account
  - [Upgrading contracts](https://github.com/hyperledger/indy-besu/blob/main/docs/design/upgradability.md) - control versions of deployed contracts (proposing and approving new versions).
  - [Validators node management](design/network.md) - control the list of network validator nodes
- Identity:
  - [DID Method](https://github.com/hyperledger/indy-besu/blob/main/docs/design/did-method.md) - Supported DID method
  - [CL Registry](https://github.com/hyperledger/indy-besu/blob/main/docs/design/cl-registry.md)
- [Client](https://github.com/hyperledger/indy-besu/blob/main/docs/design/vdr.md) - design of VDR library

More links and docs here https://github.com/hyperledger/indy-besu/blob/main/docs/README.md

The Hyperledger Indy ecosystem community came together at a series of Hyperledger Indy Ecosystem Summits (organized by the Sovrin Foundation), bringing together network operators, node operators, project maintainers, network users, vendors to discuss the state of Indy and proposals for moving the project forward. The summits were well-attended (up to 90 participants), a better understanding of the community of interest was gained, and next steps were proposed, with some (mostly notably, the Indy Besu initiative) acted upon.

## Maintainer Diversity

There are 35 individuals on 22 Indy GitHub Teams representing at least 16 organizations. We continue to have participation from (more or less) the same organizations as in 2022 — which is both good (still participating) and bad (few newcomers).

From the last Quarterly Report: _Still needed -- a cleanup of the teams are needed as some of the individuals are no longer active in the community. No progress was made on that cleanup this quarter. We have the team lists, but have not queried those on the list to see if they are still interested in being maintainers._

Typical Indy [Maintainers File](https://github.com/hyperledger/indy-plenum/blob/main/MAINTAINERS.md).

## Project Adoption

Insights from the Hyperledger Indy Ecosystem Summit showed that project adoption is “stable”. It seems those that have adopted Indy continue to stay with it and while there is evidence of new private deployments, we’re not aware of new public ones. There remains little competition for what Indy is today — an easy to deploy, stable, token-less, public, permissioned blockchain that is purpose-built for privacy-preserving verifiable credentials. The best alternative to Indy, and one being investigated as a potential Indy replacement, is Besu, with features that align with the existing Indy concepts.

It should be noted that we continue to see a steady stream of people deploying Indy through questions asked on Discord and in GitHub issues, but we do not have visibility into why they are deploying Indy and if they are continuing to use it.

## Goals

### Performance Against Prior Goals

As this is the first Hyperledger Indy Annual Report, there is not a 2022 Annual Report to look back on. However, in March 2023, the Indy Contributors group developed this [Indy Roadmap](https://hackmd.io/GeRP00i0Sj-7z4zXn2MB5g?view), an (non-timelined) wish list of technical capabilities we’d like to see in Indy. That roadmap was part of the agenda of the Hyperledger Indy Ecosystem summit, where it was highlighted that in addition to the technical capabilities, a focus was needed on marketing and on influencing regulatory guidance on decentralized identity infrastructure.

Of those items, progress was made on the following items:

* Ubuntu 20.04 development, deployment, upgrade documentation, and release.
* Clean up of issues in the various Indy repositories.
* Indy node monitoring capabilities.

That is less progress than we would have liked to see. A positive spin on that lack of progress is that Indy continues to be stable and adequately scalable such that there have been no hard complaints on the lack of additional features.

There were several events around which Hyperledger Indy code development efforts were focused over the year:

* Completion of the Ubuntu 20.04 version of Indy Node. Deployers of Indy networks have reported success in deploying the new version.
* The archiving of Ursa, triggering the move of the BLS Signatures library from Ursa to being maintained in the Indy Project.
* The movement of Aries projects to use the “shared components” in place of the Indy SDK. The “shared components” consist of [Aries Askar](https://github.com/hyperledger/aries-askar) (secure storage), [Indy VDR](https://github.com/hyperledger/indy-vdr) (client interface to Indy networks) and [Hyperledger AnonCreds](https://www.hyperledger.org/projects/anoncreds) (AnonCreds implementation).
* Deprecation of the Indy SDK by the end of Q1 2024. Progress has been made on things like closing all open pull requests and closing all issues. We've also removed the Indy SDK from the public (Read the Docs) documentation.

In addition, as mentioned earlier in the report, significant progress was made in creating the Indy Besu proof of concept and repository. Its code was added to the experimental feature branch of Indy Node repository. The development of the project is planned in a new [Hyperledger Indy Besu repository](https://github.com/hyperledger/indy-besu/tree/main).

### Next Year’s Goals

The goals for 2024 derive from both 2023 Indy Roadmap document, and the outcome of the Indy Ecosystems Summits held in 2023. The bullet point versions of these goals include the following. The Indy maintainers and contributors have a deeper understanding of what is behind these bullet points:

* Increased awareness of Indy, its usefulness, and a corresponding increase in contributors to enable it to continue to evolve.
* Formally release the Ubuntu 20.04 release of Indy Node.
    * Look into updating the solution to later releases.
* Tools and guidance in updating existing networks to the 20.04 release.
* Continue to support the migration of Indy clients away from the Indy SDK.
    * Update the Indy documentation to point people to current “best practices”.
    * Update and release the Indy VDR component as needed.
* Address the “Corporate Firewall” issue, where users behind a corporate firewall cannot access an Indy network because of the ZMQ ports being used.
* Evolve Indy so as to be ready for when the current implementation will need more functionality, such via the Indy Besu approach.
* Desired functionality:
    * Ledger Redactibility (aka "tombstoning" transactions)
    * Simplify the process for adding more types of transactions so that new object types can be published on the ledger with some verification. Currently, that requires more work than we would like, so it does not happen as often as we would need.
        * Simplify, but ideally without increasing the risk of "bad data" going on the ledger and requiring use of the "Ledger Redactibility" feature (e.g. permissioned writing, and at least some structural verification of the data)
        * With more types of transactions we can more easily transition to new of kinds of verifiable credentials, such as AnonCreds v2.
        * With transitions to new VC formats, we get better functionality, such as much better revocation — which will reduce the number of transactions on the ledger — reducing the pressure on scalability.
            * Scalability is not an issue today, but will be some day.
    * Additional DIDDoc support, such support for additional key types
    * Read replicas for performance
    * Storing other document types on an Indy ledger, such as OCA Bundles
* Progress on the Indy Besu concept:
  * Transitioning from the existing PoC and design to a concrete implementation.
      * Improvement of existing modules
      * Integration with Aries Frameworks
      * Implementation of migration tools
    * Some of the general desired functionality above might be done in the Indy Besu implementation.

### Help Required

No specific requests at this time. There is a lot that the Hyperledger Foundation provides that we need to be making use of, particularly in the area of marketing / getting the word out about the capabilities of Hyperledger Indy. Our challenge is that the project is driven largely by technical types, not marketers.

## Project Lifecycle Stage Recommendation

Indy is a Graduated project and should remain so. Its code is rock solid, and a relatively large ecosystem of network operators, maintainers, contributors, and users.

## Indy Annual Review 2024 Notes from the TOC

[TOC Meeting Recording 2024.02.15](https://zoom.us/rec/play/9R-g9dDkev58KyjPT7XkYJ6fltM879Tba6rdC-Loz_6pjyCjMabH5KwO8vcC-kvs_WoKp8ksD6Y8O1qG.FcT2qG1CM2RydRmp?canPlayFromShare=true&from=share_recording_detail&continueMode=true&componentName=rec-play&originRequestUrl=https%3A%2F%2Fzoom.us%2Frec%2Fshare%2FSEWW2lMg14g4kV7hsjvXFr-i5hVtJDPlUb9_BmFb2S8cA-YyP-jw3EfEx4qbk4sA.AmQb1tXouL7kdu6A) -- Indy Annual report discussion starts at the 29:37 mark.

### Project Health

* Overall, the project is in good health as indicated in the review and by looking at the insights
* There's a lot of community interest and participation, as indicated by the Discord activity
* Production usage is significant (e.g., govt. of BC, govt. agency in India)
* The community of contributors and orgs is active and diverse, but there is still significant skew (almost 50% activity from a single maintainer, almost 60% from a single org). Maintainers should strive to distribute workload more, and ensure that there are no "critical" contributors, whose absence could derail maintenance of key features.

### Recent Maintenance Activity and Progress
  
* As the review indicates, PRs are fewer. This is understandable when the product is mature and is largely in maintenance mode rather than in feature development mode. (Could this also be because there is more "code" per PR?)
* Tasks listed in the roadmap are being fulfilled over time.
* Question about roadmap: why is this hosted on an external site and also not linked from any of the project repos' READMEs?

### Compliance with Hyperledger Project Lifecycle Criteria

* All the criteria are fulfilled with no red flags
* Should remain in Graduated status

### Suggestions for Improvement

* Manage churn from massive refactoring in a better way, ensuring stability and usability
* Strive to keep documentation and upgrade guidelines for both users and contributors as fresh as possible, and display prominently to avoid basic inquiries on communication channels
* There doesn't seem to be a well-advertized process for new feature proposal and brainstorming, say using RFCs. For a project of this stature, brainstorming only during the maintainers' calls (including having to listen to past recordings) seems to be inadequate in my opinion.
* Maintain a roadmap file in at least one of the main repos rather than hosting it externally.

### General Recommendations

* Continue to pursue synergies with other projects, like Aries and Besu. Avoid reinventing the wheel and leverage dependencies instead, keeping the code as modular as possible. (The project has done a good job of this so far!)
* Create an Indy ecosystem page similar to the Fabric ecosystem page (https://wiki.hyperledger.org/display/fabric/Ecosystem). This would be helpful to the community, as currently it is hard for newbies to understand how all the Indy repos (let alone Aries, or Besu) complement each other.
* Write blog articles and run workshops periodically with Hyperledger staff's help
* Keep connections with the W3C standardization community and strive for compliance with those standards
* Figure out an ideal longer-term vision and roadmap, focusing on what is valuable about Indy. Also factor in the number of knowledgeable maintainers available and interests of the community (more around decentralized identity and credentials rather than distributed ledger architecture).
* Identify real priorities that can be fulfilled along with ensuring maintainer diversity. Peg supporting features that are somewhat dormant (i.e., the Indy ledger) to other active projects (e.g., the current Indy-Besu effort to use a Besu ledger for purposes that Indy was originally intended for.)