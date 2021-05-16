# An introduction to NodeJS and Express

### Introducing Node

Node (or more formally Node.js) is an open-source, cross-platform runtime environment that allows developers to create all kinds of server-side tools and applications in JavaScript. The runtime is intended for use outside of a browser context (i.e. running directly on a computer or server OS). As such, the environment omits browser-specific JavaScript APIs and adds support for more traditional OS APIs including HTTP and file system libraries.

From a web server development perspective Node has a number of benefits:

1. Great performance! Node was designed to optimize throughput and scalability in web applications and is a good solution for many common web-development problems (e.g. real-time web applications).

2. Code is written in "plain old JavaScript", which means that less time is spent dealing with "context shift" between languages when you're writing both client-side and server-side code.

3. JavaScript is a relatively new programming language and benefits from improvements in language design when compared to other traditional web-server languages (e.g. Python, PHP, etc.) Many other new and popular languages compile/convert into JavaScript so you can also use TypeScript, CoffeeScript, ClojureScript, Scala, LiveScript, etc.

4. The node package manager (NPM) provides access to hundreds of thousands of reusable packages. It also has best-in-class dependency resolution and can also be used to automate most of the build toolchain.

5. Node.js is portable. It is available on Microsoft Windows, macOS, Linux, Solaris, FreeBSD, OpenBSD, WebOS, and NonStop OS. Furthermore, it is well-supported by many web hosting providers, that often provide specific infrastructure and documentation for hosting Node sites.

6. It has a very active third party ecosystem and developer community, with lots of people who are willing to help.

- You can use Node.js to create a simple web server using the Node HTTP package.

### Web Frameworks

Other common web-development tasks are not directly supported by Node itself. If you want to add specific handling for different HTTP verbs (e.g. GET, POST, DELETE, etc.), separately handle requests at different URL paths ("routes"), serve static files, or use templates to dynamically create the response, Node won't be of much use on its own. You will either need to write the code yourself, or you can avoid reinventing the wheel and use a web framework!

### Where did Node and Express come from?

Node was initially released, for Linux only, in 2009. The NPM package manager was released in 2010, and native Windows support was added in 2012. At time of writing the current LTS release is Node v12.18.4 while the latest release is Node 14.13.0. This is a tiny snapshot of a rich history; delve into Wikipedia if you want to know more.

- Express was initially released in November 2010 and is currently on version 4.17.1 of the API (with 5.0 in "alpha").

## What is NPM?

npm is the world's largest software registry. Open source developers from every continent use npm to share and borrow packages, and many organizations use npm to manage private development as well.

npm consists of three distinct components:

1. the website
2. the Command Line Interface (CLI)
3. the registry

Use the website to discover packages, set up profiles, and manage other aspects of your npm experience. For example, you can set up organizations to manage access to public or private packages.

The CLI runs from a terminal, and is how most developers interact with npm.

- The registry is a large public database of JavaScript software and the meta-information surrounding it.

### Use npm to

1. Adapt packages of code for your apps, or incorporate packages as they are.
2. Download standalone tools you can use right away.
3. Run packages without downloading using npx.
4. Share code with any npm user, anywhere.
5. Restrict code to specific developers.
6. Create organizations to coordinate package maintenance, coding, and developers.
7. Form virtual teams by using organizations.
8. Manage multiple versions of code and code dependencies.
9. Update applications easily when underlying code is updated.
10. Discover multiple ways to solve the same puzzle.
11. Find other developers who are working on similar problems and projects. 

## What is TDD?

### Definition

- “Test-driven development” refers to a style of programming in which three activities are tightly interwoven: coding, testing (in the form of writing unit tests) and design (in the form of refactoring).

It can be succinctly described by the following set of rules:

1. write a “single” unit test describing an aspect of the program.
2. run the test, which should fail because the program lacks that feature.
3. write “just enough” code, the simplest possible, to make the test pass.
4. “refactor” the code until it conforms to the simplicity criteria.
5. repeat, “accumulating” unit tests over time.

### Expected Benefits

1. many teams report significant reductions in defect rates, at the cost of a moderate increase in initial development effort.

2. the same teams tend to report that these overheads are more than offset by a reduction in effort in projects’ final phases.

3. although empirical research has so far failed to confirm this, veteran practitioners report that TDD leads to improved design qualities in the code, and more generally a higher degree of “internal” or technical quality, for instance improving the metrics of cohesion and coupling.

### Skill Levels

#### Beginner

1. able to write a unit test prior to writing the corresponding code.

2. able to write code sufficient to make a failing test pass.

#### Intermediate

1. practices “test driven bug fixing”: when a defect is found, writes a test exposing the defect before correction.

2. able to decompose a compound program feature into a sequence of several unit tests to be written.

3. knows and can name a number of tactics to guide the writing of tests (for instance “when testing a recursive algorithm, first write a test for the recursion terminating case”).

4. able to factor out reusable elements from existing unit tests, yielding situation-specific testing tools.

#### Advanced

1. able to formulate a “roadmap” of planned unit tests for a macroscopic features (and to revise it as necessary).

2. able to “test drive” a variety of design paradigms: object-oriented, functional, event-drive.

3. able to “test drive” a variety of technical domains: computation, user interfaces, persistent data access.

**References:**

- An introduction to NodeJS and Express. [Read the full article here](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/Introduction)

- What is NPM? [Read the full article here](https://docs.npmjs.com/about-npm)

- What is TDD? [Read the full article here](https://www.agilealliance.org/glossary/tdd/#q=~(infinite~false~filters~(postType~(~'page~'post~'aa_book~'aa_event_session~'aa_experience_report~'aa_glossary~'aa_research_paper~'aa_video)~tags~(~'tdd))~searchTerm~'~sort~false~sortDirection~'asc~page~1))

- CI/CD [Watch video here](https://www.youtube.com/watch?v=xSv_m3KhUO8)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
