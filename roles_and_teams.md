# Roles and Teams in the MDN Organization

GitHub provides many features such as [organizations](https://help.github.com/articles/about-organizations/) and [teams](https://help.github.com/articles/about-teams/) to help organize projects. MDN works with open source projects with outside collaborators, and we don't need many features needed to support enterprise clients.

Here's how we use the roles provided by GitHub:

## Repository Roles
Repositories are where the work gets done. GitHub splits [repository permissions](https://help.github.com/articles/repository-permission-levels-for-an-organization/) into read, write, and admin permissions.  Read permissions are only important for private repositories, which are not used in the MDN organization. Admin permissions are usually restricted to organization members (see below). This policy is mostly concerned with write permissions, which gives users the ability to merge pull requests and manage projects.

The repositories can be categorized by their impact:

* Tier 1: Code in this repo runs on Mozilla servers, and/or on mozilla.org domains. Changes need to be reviewed for security. Examples include [Kuma](https://github.com/mozilla/kuma), [KumaScript](https://github.com/mdn/kumascript), and [samples-server](https://github.com/mdn/samples-server) repositories.
* Tier 2: Code and data in this repo appears on MDN Web Docs, but is served from an non-mozilla.org domain. Changes need to be reviewed to ensure they meet MDN standards. Examples include [browser-compat-data](https://github.com/mdn/browser-compat-data), [interactive-examples](https://github.com/mdn/interactive-examples), and [webaudio-examples](https://github.com/mdn/webaudio-examples) repositories.
* Tier 3: Code and data in this repo do not appear on MDN Web Docs. Changes need to be reviewed to meet the standards of the repository maintainer(s). Examples include [pab](https://github.com/mdn/pab) and [wp-promote-mdn](https://github.com/mdn/wp-promote-mdn) repositories.

### Requirements

Repository members with write permissions have the ability to review and merge pull requests, and in some cases can deploy to production. This means that Tier 1 membership has the same requirements as for organization roles (see below). A Tier 1 project should have at least 3 members, at least one with admin permissions.

For Tier 2 projects, only organizational members should have admin permissions. The organizational members can invite others to help manage the project as outside collaborators with write permissions. A Tier 2 project should have at least 2 members, at least one with admin permissions.

For Tier 3 projects, an outside collaborator can get administration permissions. A Tier 3 project needs 1 admin.

Projects with no members should be [archived](https://help.github.com/articles/about-archiving-repositories/) or deleted by an organization owner.

### Responsibilities

* All Tiers: Ensure the repository meets the minimum requirements, such as having a ``LICENSE`` and ``README.md`` files.
* All Tiers: At least one member should respond to an issue or pull request within one week
* Tier 1 and 2: Use pull requests for most changes, rather than pushing directly to the master branch, to facilitate discussion on GitHub.
* Tier 1 and 2: Ensure that pull requests will not break MDN Web Docs, using automated and manual checks as appropriate, before merging.
* Tier 2 and 3: Repository admins can decide pull request policy (are reviews required, who can review, etc.). This policy should be documented.
* Tier 1: Review pull requests for security impact before merging
* Tier 1: A positive review is needed to merge a pull request, so that two people have seen the code before it goes into production.

## Organization Roles

Owners and Members at the Organization level are [granted permissions across all repositories](https://help.github.com/articles/permission-levels-for-an-organization/).

There should be three to five owners. With less than three, there is a high risk that owner-level actions will be delayed. With more than five, there is higher risk that there will be Owners that never need their increased access, and don't take the role seriously.

### Requirements
Organization Owners and Members have wide permissions to manage users, teams, and repositories, and to see details about the organization. Because of this we require that Organization Owners and Members are:

* Current Mozilla staff and core contributors
* For current staff, be assigned to MDN, a related project, or a supporting team
* For core contributors, have a vouched [Mozillians](https://mozillians.org) profile in the [nda group](https://mozillians.org/en-US/group/nda/)
* Have [Two-Factor Authentication](https://help.github.com/articles/securing-your-account-with-two-factor-authentication-2fa/) enabled for their account

We encourage organization-level members to publicize their membership on GitHub.

### Responsibilities

Members should:

* Follow and enforce MDN team norms, including the [code of conduct](CODE_OF_CONDUCT.md) and [Mozilla Policies](https://www.mozilla.org/en-US/about/governance/policies/)
* Follow and contribute to issues and discussions on this [mdn meta repo](https://github.com/mdn/mdn). An issue should get feedback from one or more members within one week.
* Follow MDN organization policies described in this repo, to show a good example and to ensure they are not overly burdensome
* Suggest, document, and implement new policies through the pull request process
* Add and remove outside collaborators to repositories as needed
* [Archive](https://help.github.com/articles/about-archiving-repositories/) or delete unmaintained projects
* Discuss GitHub features, decide which to use, and document decisions in this repository

In addition, Owners should:

* Add and Remove organization owners and members as needed
* Add repositories (as fresh projects or as transfers) as needed

## Teams

GitHub's [Teams feature](https://help.github.com/articles/organizing-members-into-teams/) has evolved as GitHub adds project management features. The MDN team experimented with teams in the past, but they are currently under-used.

*Our current teams currently give wide permissions to repositories, making it unclear who is responsible for maintaining a given repository.
We should assign repository members as collaborators, and see if this eliminates our need for teams. If we decide to use teams, they should be marked as Public, not Private, and the team policy documented here. If we don't use teams, we should remove them.*
