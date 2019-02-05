## Use Flow for JavaScript type checking

|Status       | proposed |
|-------------|---------------------------------------------------------------|
|**Proposed** | 2019-02-04
|**Accepted** | (the date the proposal was accepted/rejected)
|**Driver**   | David Flanagan
|**Approver** | John Whitlock
|**Consulted**| Schalk Neethling
|**Informed** | MDN development team

### Decision

We will use Flow for static type checking for new MDN frontend
development work. We won't require that all new code be fully typed,
but that Flow can run over it without reporting type errors.

### Context

Adding "static gradual typing" to JavaScript helps catch bugs and has
other benefits that I'm going to take as a given here. In particular,
it provides a way to specify (and check at build time) the types of
React props. In ADR 001 we decided to adopt React, and in this ADR we
need to choose one of the two extant typing systems for JavaScript:
Flow and TypeScript.

### Consequences

- Using Flow as a linter for type safety will catch errors and corner
  cases that would have otherwise gone unnoticed, making our front-end
  code more robust.

- As with any kind of linting, however, there will be some extra work
  required by developers to satisfy Flow

### Alternatives Considered

We're not considering the "do nothing" alternative. As we adopt React,
good programming practice will be to adopt a type system for our
code. There are only two choices in this area: TypeScript and
Flow.

#### TypeScript

TypeScript is a compiler that compiles a superscript of JavaScript to
standard JavaScript. It is created by Microsoft, and has been around
since 2012. Originally it was valued because it defined language
features like classes at a time when JavaScript did not support
them. Currently, the only significant feature of TypeScript that is
not part of standard JavaScript is its type related features. Because
of its history as a language superset, it still has language features
like `implements`, `public` and `private` keywords that are not on a
standards path and make TypeScript more than just
JavaScript-with-types.

The Angular framework uses TypeScript. There is a large typescript
community that has defined types for common JS libraries.

Early versions of TypeScript did not do type inference and could only
check types that had been explicitly declared. That is no longer the
case, however.

TypeScript has excellent integration with IDEs, and many developers
prefer it for this reason. It feels like TypeScript has more momentum
behind it right now, though this may be largely related to the current
popularity of Microsoft's VSCode editor which works particularly well
with TypeScript.

#### Flow

Flow is not a language itself, but an extension of standard JavaScript
to allow optional type declarations. Where TypeScript works like a
compiler, Flow works like a linter, doing type checking based on
declared and inferred types. It is typically used in conjunction with
a Babel plugin that strips type declarations out of your code.

Flow was created and open-sourced by Facebook, so its integration with
React (also from Facebook) is particularly strong. React also depends
on the Babel transpiler, so using Flow with React is a natural
fit. (Typescript can also be used with Babel, but this is somewhat
awkward since both are JavaScript compilers.)

Flow is a relatively new tool, focused entirely on typing. It does not
define language extensions. If you add flow type declarations to standard
JavaScript, those type declarations merely need to be stripped out at
build time: there is no runtime behavior that needs to be compiled
in. Early versions of Flow were slow, and produced cryptic error
messages. Recent versions have fixed these problems.

On the other hand, it sounds as if the Flow project has been looking
inward at Facebook and has recently not been as responsive as an
open-source project should be:
https://medium.com/flow-type/what-the-flow-team-has-been-up-to-54239c62004f

#### Flow vs TypeScript

For our React and Babel-based project, Flow feels like the path of
least resistance. This post from a member of the Flow team is a couple
of years old but still seems persuasive to me:
https://discuss.reactjs.org/t/if-typescript-is-so-great-how-come-all-notable-reactjs-projects-use-babel/4887

If we had lot of contributors using IDEs, then it might be that
TypeScript's better IDE integration would make it the better choice.

Flow and TypeScript have evolved rapidly over the last two years, and
they seem to be in real competition for developer mindshare. A year
ago, it seemed like Flow had the momentum, and today it feels to me
like TypeScript has the momentum.

I believe, nevertheless, that Flow is the right choice for us, for
now. If we turn out to have chosen wrong, we my need to switch to
TypeScript in the future. I expect, however, that if that becomes
necessary, there will be tools that automate any required code changes.
