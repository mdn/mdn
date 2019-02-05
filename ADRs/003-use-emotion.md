## Use Emotion as our CSS-in-JS solution

|Status       | proposed <!--becomes accepted, rejected or superseded later-->|
|-------------|---------------------------------------------------------------|
|**Proposed** | 2019-02-04
|**Accepted** | (the date the proposal was accepted/rejected)
|**Driver**   | David Flanagan
|**Approver** | John Whitlock
|**Consulted**| Schalk Neethling
|**Informed** | MDN development team

### Decision

We will use Emotion as our CSS-in-JS solution for React frontend
development. (This does not mean we will not also use regular SCSS/CSS
stylesheets as well.)

### Context

In React-based frontend development, it has become very common to
express the CSS styles of React components using JavaScript rather
than external stylesheets. Done well, this can be quite efficient, and
there are static analysis and type checking benefits to expressing CSS
styles as code (just as there are for expressing HTML layouts as
code). Also, CSS-in-JS libraries can do things like automatically
adding vendor prefixes to CSS properties when needed. Developers often
find that CSS-in-JS improves their productivity. There are quite a few
CSS-in-JS libraries in common use, and the point of this ADR is to
settle on one.

### Consequences

While we will probably still use standard CSS stylesheets (via SCSS) to define
global and site-wide styles and themes, we will use a new system for
expressing styles (especially layouts) that are specific to individual
React components.

There may be a small learning curve for developers while we get used
to the new system. But I do not expect there to be a performance
impact.

### Alternatives Considered

There are *many* CSS-in-JS libraries.
https://css-tricks.com/the-fragmented-but-evolving-state-of-css-in-js/
is a recent and helpful summary.

#### No Library

One option with React is to express sets of CSS properties as JS
objects, and set these objects as the value of the `style` property on
React components. This works, but creates inline styles on individual
HTML elements, which is quite inefficient.

#### Aphrodite

Instead of setting JS-defined styles on the `style` property of
elements, what we want instead is a library that will take a
JavaScript object representing a set of CSS styles, convert that to a
CSS class definition in a stylesheet and then return us the name
of the class so we can set it on the `className` property of an
element. 

This is exactly what the Aphrodite library does, combining the
convenience of scoped styles in JS with the efficiency of stylesheets.
Aphrodite was created
at and open-sourced by Khan Academy. It is still used at KA, but is
not being actively developed anymore. It is one of
the older libraries and is slower and with fewer features than the
leading libraries.

#### Styled Components

The Styled Components library introduced a couple of innovations to
the universe of CSS-in-JS. First, it allows styles to be represented
using JS template literals instead of objects so that css properties
with hyphens don't need to be converted to camelCase identifiers, and
so that only a single string is involved instead of an object. Second
it introduced the syntax of using tagged template literals to create
new React components given an HTML tag name and a string of
CSS. Unlike Aphrodite where you define a bunch of objects to represent
a bunch of CSS classes, Styled Components allows you to define a bunch
of simple React components that are efficiently pre-styled just how
you want them.

Styled Components is now one of the most popular css-in-js libraries.

#### Emotion

Emotion picked up where Styled Components stopped, copying the ability
to create a React component from an html element and a set of
styles. But it went further, supporting both template literal styles
and object-based styles.  This is nice because object styles are more
convenient when you want to dynamically alter the styles based on a
global theme, for example.

Emotion also can also be used like Aphrodite, taking a set of styles
(as an object or as a string) and returning a class name that you can
use on the `className` property.

In addition, though, Emotion also introduced a powerful new
innovation: Instead of setting inline styles on the `style` property
or a class name on the `className` property, Emotion allows you to set
object or string styles on the `css` property of a React element. When
used with a Babel plugin (and Babel is already required to compile
React's JSX syntax) this `css` property is transformed into an
efficient class name. The Babel plugin also performs some minfication,
can create source maps, and adds meaningful identifiers to the
otherwise meaningless generated classnames.

Emotion has an large developer community and is actively maintained.
It works with server-side rendering and has a helpful ecosystem of
tools. In addition to the Babel plugin described above, there is a
Jest plugin, for example, that improves snapshot testing for React
components that use Emotion.

Emotion appears to be one of the top 3 libraries in terms of
popularity and performance. Although Styled Components currently has
more weekly downloads, Emotion is growing faster and is today's trending 
library. I'm picking it because of its flexiblity,
however: it provides a number of different ways to do CSS-in-JS, so we
can experiment and find the ones that work the best for our code.

As the css-tricks.com article above points out, Styled Components has
copied Emotion's recent innovations and the two libraries now have
essentially the same API, so it should be easy to switch to Styled
Components if we ever need to.
