# Owners Handbook

This provides owner guidelines for the MDN organization. Owners are those that work on the core team at Mozilla and manage community requests, access to repositories, content proposals and platform updates.

## Contents

- [Platform updates](#platform-updates)
- [Managing peers]()
- [Translated content](#translated-content)

## Platform updates

Or new features. These will usually come in the form of issues raised on other repositories, or issues raised within the dedicated project itself. New issues will be added to the [dedicated project here on mdn/yari](https://github.com/mdn/yari/projects/11) with the `needs triage` label. They should be added to the 'To triage' column.

Time is set aside every fortnight (vaguely a sprint) to work on platform improvements. They can be anything from new requests of features, to updates that would be helpful, to urgent issues that affect our users.

Issues should be read and discussed. If there are any irrelevant issues, they should be closed with the `won't fix` label applied, and a comment explaining why. `on hold` should be applied if there are any blockers to doing the work. If the issue has been added to the project by mistake and should exist elsewhere, move it.

An issue should be reviewed with the following criteria:

- Priority:
   - p0 Urgent: Something is broken and needs to be fixed immediately.
   - p1 High priority: This is needed, but not something that's broken and affecting our users.
   - p2 Medium priority: It would be great to get this done if there aren't any other high priority tasks, chances are this issue will escalate to high priority soon enough.
   - p3 Low priority: This is a nice to have. Small chance of it escalating, but something we should consider.

- Time:
   - t-30 Less than 30 mins: A quick fix, a ten minute task, however no task is just ten minutes but the developer can change, test and pr within less than an hour.
   - t-180 Less that 3 hours: This change will take about half a day for a developer to modify and test and raise a pr.
   - t-2day This task will keep an engineer involved for a day or two. Or more than one input is needed, such as a fix from front end as well as back end.
   - t+2day This task will take a few days or more to complete. With these type of issues there are probably sub-issues which should be raised, or more definition needed. Multiple engineers are probably needed (such as front end work and back end work).

This will give a good idea of what issues need and can be worked on. Issues that can be completed within the fortnight should be assigned and moved to the 'To do' column.


## Managing peers

## Translated content

Requests for Translated content can either be support from the unfrozen locale teams or a team looking to unfreeze a locale.

### Support

The current locale teams are fairly self sufficient and requests from them are low traffic. Most can be dealt with by the guidelines set above as they will be platform updates or new features, or requests for peers to be added removed.

Anything else can be discussed directly with the contributor. If input is needed from a wider set of translated content contributors, open a discussion or issue on the [Translated content repository](https://github.com/mdn/translated-content) following the [issue guidelines]()

### Unfreezing a locale

The guidelines for a community member to request a [locale to be unfrozen are here](https://github.com/mdn/translated-content/blob/main/PEERS_GUIDELINES.md#activating-a-locale). They will get in touch with one of the core peers or owners through [appropriate channels](). If the request is agreed upon the locale can be unfrozen and added to mdn/translated-content.

Task list for unfreezing a locale

- Raise a platform request to unfreeze locale
- Communicate with requester time scale
- Create a team under the Translated Content team, with contributors, update the [CODEOWNERS file](https://github.com/mdn/translated-content/blob/main/.github/CODEOWNERS) and set team to be sent pr reviews for their locale prs
- Create a label on mdn/translated-content and mdn/content for that locale
- Update github action to move any issues on mdn/content with that label to mdn/translated-content
- Introduce requester to other locale teams - they will help with 'How tos' and other queries


