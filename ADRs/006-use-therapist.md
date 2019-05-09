## Use therapist for all linting



|Status       | proposed |
|-----------------|-----------------------------------------------------------|
|**Proposed**     | 2019-05-08
|**Accepted**     | (the date the proposal was accepted/rejected)
|**Supersedes**| n/a
|**Driver**       | Peter Bengtsson
|**Approver**     | (who will make the decision and merge the PR)
|**Consulted** | Ryan Johnson
|**Informed**  | MDN core team and contributors

### Decision

Switch to use [`therapist`](https://github.com/rehandalal/therapist) for doing
all linting locally and in CI in kuma.

### Context

At the moment, we have `precommit` in the root `package.json` which gets
installed with `npm install`. It only does JavaScript things (`eslint`
and `stylelint`). For Python we execute `make lint` from the `Makefile`.

Ideally we should have one file that checks all relevant files in every
commit/pull request. Both Python and JavaScript and possibly other things
like Markdown. Ideally, the way we do linting in CI should be identical to
how a git pre-commit hook would work for every developer.

`therapist` solves this by expecting every developer to install it locally
(e.g. `sudo pip install therapist`) and then run `therapist install` which
sets up your git pre-commit hook. `therapist` has the added advantage,
that as a git pre-commit hook, it only checks touched files that are staged
in git so it's fast.

It also acts as a "recipe" for how all linting is done. The contents of
a checked in `.therapist.yml` file describes how we execute things like
`eslint`, `flake8`, `prettier`, `black` etc.

In CI, the same config file is used as everyone's git pre-commit hook but
with all files instead of just the ones checked in.


### Consequences

#### Pros

* Faster than what we have now.

* Uniform linting checks in local development and CI.

* One file to dictate how we do linting for *all* things.

#### Cons

* `therapist` is maintained and mature but it's not hugely popular.

* Requires git when run in CI. Might cause problems if needed to run inside
`docker-compose` without volume mounts.

* Might cause confusion for people to replace their current git hooks.


### Alternatives Considered

[`pre-commit`](https://pre-commit.com/) is also a Python project that
can be configured to Python, Node, etc. too. It installs its own Python
`virtualenv` which can complicate things in CI.
