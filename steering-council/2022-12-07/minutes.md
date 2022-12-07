# Brightway Steering Council meeting minutes

## Present

### Steering Council

* Bernhard Steubing (BS)
* Chris Mutel (CM)
* Romain Sacchi (RS)
* Tomas Navarrete (TN)

### External

* Jonathan Kidner (JK)

## Discussion

Discussion was based of [input slides from CM](https://github.com/brightway-lca/enhancement-proposals/blob/main/steering-council/2022-12-07/2022-12-07%20presentation.pdf).

Initially there was not a quorum so a vote on [BEP 0001](https://github.com/brightway-lca/enhancement-proposals/blob/main/proposals/0001_bep-template.md) was delayed.

There was broad agreement that the community needs better communication on what the development process currently does, and in the future should, look like. Current information is split across too many channels and addresses.

BS proposed that the Steering Council meet more regularly, and not just discuss and vote on BEPs, but also give strategic input for future development. CM noted that this could run in conjunction with the industry stakeholder panel.

### [BEP 0002](https://github.com/brightway-lca/enhancement-proposals/blob/main/proposals/0002_merge-repositories.md)

First reactions:

BS:

Initally positive

* Seems reasonable
* Case for making changes is clearly explained

TN:

Initially negative

* Modularity: Don't want everything in one place, want to pick and choose
* User friendliness: Some users don't understand the whole ecosystem, should be able to contribute to only one library
* Development: Libraries proceed at different rates

* Users don't know where to go when they have a problem
	* `from brightway2 import *` -> They don't know where the functions come from
* Proposal doesn't seem to solve the real problems identified

CM:

Initially negative

* Modularity: Want to be able to use only some components, and for the interfaces between packages to be clearly defined so they can be used without the broader ecosystem
 and development
* Metapackage with all repositories as alternative? See example for BW documentation redo

RS:

Initially negative

* Carculator and other packages use only `bw2io`

### Expected BEPs

BS:

* Data imports are critically important, should be prioritized
	* How do we get access to other databases?

Examples databases for one-click installs:

* Agribalyse
* US LCI

## Tasks

None

## Miscelaneous 

BS: The current situation with the bw2io package is an example of data being tightly integrated to code in Brightway. ActivityBrowser user and devs would prefer to have a means to install many different biosphere databases in one same project. Another option would be to have one huge biosphere database with **all** flows (past and present).

## Next steps

* CM: Email to Ben Portner about 0001 feedback
* CM: Email to stakeholders about enhancements proposed in [happy_family](https://github.com/Depart-de-Sentier/happy_family/)
