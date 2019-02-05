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

The Mozilla devtools team uses Flow with their React code in multiple repos.
The addons.mozilla.org site 
and the testpilot.mozilla.com site (before it was EOL'ed) use Flow with React. I've
only been able to find two Mozilla projects that are using React and TypeScript:
https://github.com/mozilla/voice-web and
https://github.com/mozilla/addons-code-manager.

On Slack, devtools developers told me:

- "I think both are great"
- "TS has more community support"
- "Flow probably optimizes more for correctness and dealing with Facebook-scale codebases"
- "TypeScript seems more future-proof than Flow"
- "TypeScript definitely has the community mindshare"
- "Flow has been more open with their roadmap recently"
- "The profiler team has been happy and productive with Flow. I feel that we'd be happy and productive with TypeScript too."

None of these develpers were unhappy with their current use of Flow, and none had compelling reasons
for choosing either one or the other.

Flow and TypeScript have evolved rapidly over the last two years, and
they seem to be in real competition for developer mindshare. A year
ago, it seemed like Flow had the momentum, and today it feels to me
like TypeScript has the momentum and that this is tied to its excellent
integration with vscode, which has become a very popular editor.

Nevertheless I think that Flow is the right choice for us, for now because:

- Half the MDN frontend team already has experience with Flow, but no one on the team has experience with TypeScript
- More Mozilla projects use Flow than use TypeScript. The projects using TypeScript seem to be smaller and newer
- Flow is more like a linter that checks types and strips type annotations leaving standard JavaScript.
  TypeScript is more like a compiler for a new language. If we were to choose TypeScript we'd also
  have to decide which of its non-standard language extensions we will use and which we will not allow.
- Fundamentally, it seems wrong to me for Mozilla (the spiritual home of JavaScript) to be starting projects 
  using a language that includes non-standard (and not on a standards track) extensions to JavaScript. As
  Brendan Eich says "Always bet on JavaScript".

If we turn out to have bet wrong, we can switch to TypeScript in the future. The syntax for
simple type annotations is almost identical in the two, so the conversion should not be
terribly difficult. And there are tools, such as https://github.com/bcherny/flow-to-typescript, to help 
automate it.
