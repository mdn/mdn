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

Use Prettier for JavaScript code formatting across all MDN codebases.

### Context

We have a number of repositories across the MDN organization that uses JavaScript. To ease 
contributions, shorten pull requests review time, and ease transition between projects,
it is suggested that we adopt Prettier across all projects inside the MDN org for JavaScript code formatting.

To ensure consistency, it is also suggested that we utilise Husky[] and enable a pre-commit hook to auto format all JavaScript.

### Configuration

Use Prettier defualts:

```
// .prettierrc
{}
```

package.json config

```
// package.json
"scripts": {
  "format": "prettier --write \"src/**/*.{js,jsx}\"",
  "format:check": "prettier --list-different \"src/**/*.{js,jsx}\"",
},
"husky": {
  "hooks": {
    "pre-commit": "npm format"
  }
}
```

### Consequences

We have standard JavaScript code formatting across projects, and tools that enforce these standards. 

### Alternatives Considered

This is very norrowly scoped and suggests a tool that is standard across the industry, and already used on projects such as Kuma, so other options have not been explored.
