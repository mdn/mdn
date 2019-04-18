## Use pnpm for package management

| Status        | proposed |
| ------------- | -------- |
| **Proposed**  | 2019-04-18
| **Accepted**  | (the date the proposal was accepted/rejected)
| **Driver**    | ExE Boss
| **Approver**  | Florian Scholz
| **Consulted** | (who you worked with on this decision)
| **Informed**  | MDN Development Team

### Decision

We will use [pnpm](https://pnpm.js.org) for package management
of new and existing MDN Node projects.

### Context

Using pnpm helps catch bugs caused by failing to declare dependencies
in `package.json`, many of such were found out much later, after
the changes were pushed to production.

#### See also:
- https://www.kochan.io/nodejs/why-should-we-use-pnpm.html
- https://medium.com/pnpm/pnpms-strictness-helps-to-avoid-silly-bugs-9a15fb306308

### Consequences

- Using pnpm for package management will prevent developers from using packages
  without forgetting to declare them in `package.json`'s `dependencies`, catching
  bugs which would have otherwise been deployed to production.

  **Examples:**
  - [mdn/kumascript#1125](https://github.com/mdn/kumascript/pull/1125)
    (uplifted from [mdn/kumascript#1057](https://github.com/mdn/kumascript/pull/1057))

- Using pnpm will also have the benefit of eliminating [doppelgangers](https://rushjs.io/pages/advanced/npm_doppelgangers/),
  which improves harddrive space usage, which when combined with pnpm's use of hardlinks
  and symlinks further improves space savings.

### Alternatives Considered

#### Keep using npm

This will result in bugs like [mdn/kumascript#1125](https://github.com/mdn/kumascript/pull/1125)
to keep piling up.

#### Use Yarn

Yarn is smarter than npm, but it too creates flat node_packages,
so it wouldn't eliminate most of the problems which this ADR is trying to address.
