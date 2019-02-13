## Use React for the MDN Frontend

|Status       | proposed    |
|-------------|-------------|
|**Proposed** | 2019-02-01
|**Accepted** | 2019-02-05
|**Driver**   | David Flanagan
|**Approver** | John Whitlock
|**Consulted**| Schalk Neethling
|**Informed** | MDN core team and contributors

### Decision

We will use the React framework and related technologies when
developing significant new frontend features for the MDN website.
We may also convert existing features to React as time and
opportunity allows, but this ADR does not mandate that.

### Context

The Kuma frontend is currenly implemented using jQuery and, to a lesser extent, jQueryUI,
but without a modern frontend framework.  As a result our UX (the menus in
the navigation header, for example) feels dated. The development team
feels that our development velocity is hampered by lack of a
framework. Furthermore, we believe that our ability to collaborate
with contractors and with open-source contributors would be enhanced
if we were using a modern framework with a large developer community.

### Consequences

Using React will enable us to develop front-end features more quickly,
and should make it easier to work with contractors on front-end
features.

Any large front-end framework can impact the page load time for sites
that use it. During the transition to React there is a risk that page
performance will decrease if we are not careful. A page that depends
on both jQueryUI and on React, for example, will be slower to load
than a page that depends on only one of those two libraries.
As we transition to React, we will need to carefully measure the
performance impact before we ship anything to users.

React supports server-side rendering which can (but does not always)
help with performance, and will be necessary if we want to continue
to support logged-out users who have JavaScript disabled. Server
side rendering is well supported by React and its ecosystem, but
doing it will add complexity on the backend and in the build pipeline.

### Alternatives Considered

#### Status Quo

We did not seriously consider maintaining the status quo with jQuery
and jQueryUI. It seems clear that we need a modern solution.

#### React

React was the presumed winner going into the research process, and it
did, in fact, come out on top. Points in favor of React:

- David has 18 months experience with it; Schalk was already learning
  it.

- Massively popular with an order of magnitude more weekly downloads
  on npm than its competitors.

- Backed by the resources of a large corporation; reliable, high
  quality releases.

- Large ecosystem of existing components and developers

- Strong support from tools and libraries like webpack, babel and emotion.

- Great developer ergonomics: jsx plus a css-in-js library allows
  components to be developed as single-file JS modules which turns out
  to be a very efficient (IMO) way to work.

A consultant John and I spoke with recently told us that all of his
corporate clients in 2018 (except MDN) were using React.

Mozilla maintains a number of React-based websites, including

- [addons.mozilla.org](https://addons.mozilla.org/)
  ([mozilla/addons-frontend](https://github.com/mozilla/addons-frontend/))
- [testpilot.firefox.com](https://testpilot.firefox.com/)
  ([mozilla/testpilot master](https://github.com/mozilla/testpilot/tree/master),
  before [end-of-life](https://github.com/mozilla/testpilot/tree/eol))
- [donate.mozilla.org](https://donate.mozilla.org)
  ([mozilla/donate.mozilla.org](https://github.com/mozilla/donate.mozilla.org))
- [hubs.mozilla.com](https://hubs.mozilla.com/)
  ([mozilla/hubs](https://github.com/mozilla/hubs))
- [data.firefox.com](https://data.firefox.com/)
  ([mozilla/ensemble](https://github.com/mozilla/ensemble))
- [learning.mozilla.org](https://learning.mozilla.org)
  ([mozilla/learning.mozilla.org](https://github.com/mozilla/learning.mozilla.org))
- [changecopyright.org](https://changecopyright.org)
  ([mozilla/copyright](https://github.com/mozilla/copyright))
- [foundation.mozilla.org](https://foundation.mozilla.org)
  ([mozilla/foundation.mozilla.org](https://github.com/mozilla/foundation.mozilla.org))
- [webmaker.org](https://webmaker.org)
  ([mozilla/webmaker.org](https://github.com/mozilla/webmaker.org))

I was not able to find any Mozilla websites that use Angular, Vue or Polymer.

#### Angular

Angular is a template based framework, from Google, with a bias toward
TypeScript instead of JavaScript. It is less popular than React and I
found the use of templates unappealing. The Angular (version 2 and
later) framework is completely different than the AngularJS (version 1)
framework, and it appears that the Angular community is still
fractured because of that break in compatibility.

#### Vue

Vue is another template-based framework that seems to be slightly more
popular that Angular. It does not appear to have major corporate backing the
way that React and Angular do. I did not investigate this framework
very deeply because none of its features seemed compelling enough to
make us pick it over React.

#### Web Components

Web components are the standard component system for the web,
and in that sense they seem like the best choice for Mozilla.

Firefox is [migrating from XBL to WebComponents](https://mozilla.github.io/firefox-browser-architecture/text/0007-xbl-design-review-packet.html).

##### Polymer

Polymer versions before 3.x aren't well supported by browsers
other than Chrome.

If we didn't have such ambitious goals for 2019 and weren't expecting
to work with contractors on those goals, I would want to seriously
consider using Web Components because they seem like the best solution
for the open web. But the lack of tools, ecosystem, and developer
community makes this a non-starter for now.

In the future maybe we'll be able to use Web Components for small
components, and tie them together into larger components with React.
