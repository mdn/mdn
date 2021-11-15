JavaScript code formatting with Prettier across MDN repositories


|Status       | proposed <!--becomes accepted, rejected or superseded later-->|
|-----------------|-----------------------------------------------------------|
|**Proposed**     | 31 May 2019
|**Accepted**     | (the date the proposal was accepted/rejected)
|**Driver**       | Schalk Neethling
|**Approver**     | TBD
|**Consulted**    | MDN Team
|**Informed**     | MDN Team

### Decision

Use Prettier for JavaScript code formatting across all MDN repositories.

### Context

We have a number of repositories across the MDN organization that uses JavaScript. To ease 
contributions, shorten pull requests review time, and ease transition between projects,
it is suggested that we adopt Prettier across all projects inside the MDN org for JavaScript code formatting.

### Configuration

Our configuration is the default configuration in Prettier. I.e. `{}`. 

### Consequences

We have standard JavaScript code formatting across projects, and tools that enforce these standards. Code formatting is no longer manually maintained or reviewed. CI is used to verify strict adherence to this rather than human intervention. Failure to format code correctly, with Prettier, in pull requests should break and put the onus on the contributor to fix linting before commencing human code review.

### Alternatives Considered

While alternative tooling was not explored, alternative Prettier configurations will be acceptable if there are solid reasons to do so. For example, kuma already uses 4-spaces indentation and should be allowed to continue doing so in order to avoid crazy-big change sets that ruin too much of the git history.

With that said, this rule is only allowed for existing projects with a significant amount of JavaScript code.
