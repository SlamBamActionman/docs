# PR Freeze And Restrictions Policy
This document lists the policy and procedure for how to handle PR freezes and restrictions for the Space Station 14 repository.

A Freeze is a hard blocker on merging PRs related to areas defined by the Freeze description. This means any PR that would fall within any such area should *not* be merged into Staging/Master, unless given an exception as defined by the Freeze.

A Restriction is an indicator to show that any PR in related areas will be heavily scrutinized before merging. This means that *all* such PRs require more thorough examination and discussion among maintainers, but may still be merged should it pass approval.

**Freezes are listed in the following SS14 Github Repository Issue: [Current Freezes and Restrictions](https://github.com/space-wizards/space-station-14/issues/8524).**

## Applying a Freeze

A Freeze is meant to indicate to contributors that any PR that falls within a frozen area is going to be denied, and that their effort is best spent elsewhere. As such, freezes should only be implemented where there is very good reason to restrict the addition of new PRs. Reasons should fall within one of the following (exceptions may apply):

- A technical feature is required, as additional PRs in the area would have technical impact.
- Content within the area is satiated and more would not be desirable.
- A design document is required for futher development, to ensure a cohesive direction when adding features.

The process of initiating a Freeze is the following:

1. Any Maintainer or above may initiate a Freeze.
2. The initiator creates a thread within an internal staff chat on Discord, tagging the Maintainer role and any other relevant roles. The start of the thread should explain the issue the Freeze would address, what area the Freeze touches, what would allow the Freeze to end and if there are any exceptions to the Freeze.
3. The thread should ideally be up for 24 hours to allow for comments before the freeze is instantiated. Staff should discuss and attempt to reach a resolution within this timeframe. This step may be waived at a Project Manager's discretion.
4. The initiator should add the freeze to the list of [Current Freezes and Restrictions](https://github.com/space-wizards/space-station-14/issues/8524) following the template below.

**Note: A Project Manager (or above) may, with written approval, allow a PR to bypass a Freeze. This should be done via a comment on the bypassing PR, with a motivating reason given for why it bypasses the Freeze.**

### Freeze Template

```
**Freeze area**
*Reason:*
*End condition:*
*Exceptions:*
```

Examples:
```
**New lobby art**
*Reason:* We got enough at the moment and don't require more.
*End condition:* None.
*Exceptions:* An Art Director may be contacted for an exception.
```
```
**Clothing variants for mobs**
*Reason:* Inconsistently maintaining a lot of clothing sprite variants for species/mobs is not feasible and could have big long-term consequences. Variants will not be accepted until we support displacement masks (unless the variants have a good reason to be or a maintainer approved them). 
*End condition:* Displacement map support and implementation for mobs.
*Exceptions:* This freeze wont apply for maintaining current variants (like monkey suits); Certain species-specific sprites are fine if they can't be displacement mapped; It is fine for existing round-start species.
```
```
**Wizard & Related content**
*Reason:* Needs a design document, and content is being refactored/added by @keronshb.
*End condition:* A design document is required for free development of Wizard content.
*Exceptions:* Keron may approve individual PRs; please contact them before starting a Wizard-related PR. 
```

## Applying a Restriction

A Restriction is meant to indicate to contributors that a PR submitted within a restricted area will need to be high-effort and go through heavy scrutiny to be accepted. The requirements to apply a Restriction is not as heavy as a Freeze, and one may be added via simple consensus among *three* Maintainers (or approval from a single Project Manager). Once there is consensus, add the Restriction to the list of [Current Freezes and Restrictions](https://github.com/space-wizards/space-station-14/issues/8524) following the template below.

**Note: A Project Manager (or above) may, with written approval, allow a PR to bypass a Restriction. This should be done via a comment on the bypassing PR, with a motivating reason given for why it bypasses the Restriction.**

### Freeze Template
```
**Restriction area**
*Reason:*
```

Examples:
```
**EMAG interactions**
*Reason:* There are too many at the moment, and should ideally be split up into different items and/or have a design document made.
```
```
**Recipes**
*Reason:* More of a PSA that microwave recipes are subject to potential deletion in future pending chef refactor.
```

## Handling incorrect PRs

There will likely be instances where a PR gets merged that does not adhere to an existing Freeze/Restriction policy. In such a case, the Maintainers that approved the PR should be reached out for comment. If it is deemed that the PR does not meet the requirements listed in the Freeze's Exceptions, the one of the following should take place:

- a) A Project Manager (or above) is contacted and gives bypass approval.
- b) The PR gets reverted.

In either case, a comment should be made on the PR explaining the reason for the decision and linking to the relevant Freeze/Restriction.
