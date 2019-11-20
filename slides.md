---
title: Software testing overview - slides
---

<section>
<section>

# Software testing overview
— with [mparker17][mparker17-drupalorg]

<small>Follow along at [mparker17.github.io/talk--software-testing-overview](index.md)</small>

[mparker17-drupalorg]: https://www.drupal.org/u/mparker17

</section>
</section>


<!-- Introduction -->


<section>
<section>

## Who am I?

[mparker17][mparker17-drupalorg] on Drupal.org, [Github][mparker17-github], and [Gitlab][mparker17-gitlab]

I work for [Digital Echidna][echidna], [Brady's Meat & Deli][bradysmeats]

<small>(previously [Environment Canada][wsc], [Versabanq][versabanq], [UWaterloo][uwaterloo], [PeaceWorks][peaceworks], [Myplanet][myplanet], [OpenConcept][openconcept])</small>

[mparker17-github]: https://github.com/mparker17
[mparker17-gitlab]: https://gitlab.com/mparker17
[echidna]: https://echidna.ca
[bradysmeats]: https://bradysmeats.com
[wsc]: https://www.canada.ca/en/environment-climate-change/services/water-overview/quantity/monitoring/survey.html
[versabanq]: https://www.versabank.com
[uwaterloo]: https://uwaterloo.ca
[peaceworks]: https://peaceworks.ca
[myplanet]: https://www.myplanet.com
[openconcept]: https://openconcept.ca

</section>
<section>

## Who am I? (ctd.)

I am an [Acquia Certified Drupal Developer][acquia-cert]

<small><abbr title="Computer Science">CS</abbr> degree not completed at [UWaterloo][uwaterloo]</small>

[acquia-cert]: https://certification.acquia.com/user/843258
[uwaterloo]: https://uwaterloo.ca

</section>
</section>


<!-- About testing. -->


<section>
<section>

## Why test?

* Our customers and employers pay for software that works correctly.
* Tests give us confidence that our system works correctly.

</section>
<section>

### Tests tell us that...

* our system does what it is intended to do,
* changes have not broken existing functionality,
* our system can handle edge-cases.

</section>
<section>

## Dictionary definitions

**Testing (verb)**

To evaluate<sup>1</sup> [a system for correctness]

**A test (noun)**

A procedure leading to acceptance or rejection<sup>1</sup> [of a system's correctness]

<div class="fragment">

**But keep in mind...**

"Testing only shows the presence, not the absence, of bugs" — Edsger W. Dykstra<sup>2</sup>

</div>

</section>
</section>


<!-- Approaching and classifying tests. -->


<section>
<section>

## Approaching tests

1. Manual tests (get a person to test)
2. Automated tests (get the computer to test itself)

<div class="fragment">
<br />

We want to automate as many tests as possible to save time and money, but it's not possible / practical to automate _everything_.

</div>
</section>
<section>

## Classifying tests

</section>
<section>
<img src="assets/images/2019-11-14--test-automaton-pyramid--overview.svg" alt="A pyramid with unit tests on the bottom, acceptance tests in the middle, and exploratory tests on the top." style="margin: 0; padding: 0;"/>
</section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--overview.svg" data-background-size="25%" data-background-position="top right">

### Classifying tests (ctd.)

1. Exploratory tests
2. Acceptance tests <small>(broken down into System, Integration, and Component tests)</small>
3. Unit tests

</section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--overview.svg" data-background-size="25%" data-background-position="top right">

### Classifying tests (ctd.)

<small>Ignoring exploratory tests for a moment...</small>

| Unit tests         | Acceptance/System tests |
| ------------------ | ----------------------- |
| have Small scope   | have Large scope        |
| are Fast to run    | are Slow to run         |
| are Cheap to write | are Expensive to write  |
| are Numerous       | are Sparse in number    |

</section>
</section>


<!-- Unit tests. -->


<section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--unit.svg" data-background-size="25%" data-background-position="top right">

## Unit tests

**What?** highly-isolated, low-level, clear-box tests for code; covering code paths and edge cases for small units and small group interactions

**Who?** by developer for developer; in language of <abbr title="System Under Test">SUT</abbr>

**Synonyms** for individual units — (couldn't find any)
**Synonyms** for unit groups — interaction, integration; integration & testing (I&T)

**Part of/covers** functional, regression testing

</section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--unit.svg" data-background-size="25%" data-background-position="top right">

### Unit tests (ctd.)

**Key tech**

* PHP — [PHPUnit][phpunit], [php-hamcrest][php-hamcrest], [D8 UnitTestCase][d8-unittestcase]
* JavaScript — [Jest][jest] / [Jasmine][jasmine], [Mocha][mocha], [Ava][ava], [Unexpected][unexpectedjs] (previously QUnit, Unit.js)<sup>3</sup>

[phpunit]: https://phpunit.de
[php-hamcrest]: https://github.com/hamcrest/hamcrest-php
[d8-unittestcase]: https://www.drupal.org/docs/8/testing/types-of-tests-in-drupal-8#s-unit-tests
[jest]: https://jestjs.io
[jasmine]: https://jasmine.github.io
[mocha]: https://mochajs.org
[ava]: https://github.com/avajs/ava
[unexpectedjs]: https://unexpected.js.org/

</section>
</section>


<!-- Acceptance tests. -->


<section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--acceptance.svg" data-background-size="25%" data-background-position="top right">

## Acceptance tests

**What?** high-level, black-box tests to communicate; clarify; and understand when a requirement is done.<sup>4</sup>

**Who** business analyists write the "happy path", QA analysts write the "unhappy path", developers provide input into both<sup>4</sup>

**Synonyms** (term overloaded/overused)

</section>
</section>


<!-- Exploratory tests. -->


<section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--exploratory.svg" data-background-size="25%" data-background-position="top right">

## Exploratory tests

**What?** high-level, black-box tests to find unexpected behaviors, confirm expected behaviors, and the system behaves well under human operation

**Who?** business, designers, developers, marketing, QA, etc.

**Synonyms** field, refinement tests; bug-hunting

**Part of/covers** A/B, end-user, penetration (pentesting), security, usability, user experience (UX) testing

</section>
</section>


<!-- Component tests. -->


<section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--component.svg" data-background-size="25%" data-background-position="top right">

## Acceptance/Component

**What?** isolated, mid-level, grey-box tests for behavior; covering the happy-path for features and business rules (as well as obvious corner/alternate paths)

**Who?** by <abbr title="Quality Assurance">QA</abbr> & business, for business; often in a behavioral <abbr title="Domain Specific Language">DSL</abbr>

**Synonyms** behavior/behavioral, confidence, validation; verification & validation (V&V)

**Can be part of** functional, regression

</section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--component.svg" data-background-size="25%" data-background-position="top right">

### Acceptance/Component (ctd.)

**Key tech**

* The [Gherkin][gherkin] DSL ("Given/When/Then")
* PHP — [Behat][behat], [D7 SimpleTest][d7-simpletest], [D8 kernel tests][d8-kernel], [D8 Browser/JS tests][d8-browser]
* JavaScript — [cucumber-js][cucumberjs], [Chai][chai]<sup>6</sup>

[gherkin]: https://cucumber.io/docs/gherkin/reference/
[behat]: https://behat.org
[d7-simpletest]: https://www.drupal.org/docs/7/testing/simpletest-testing-tutorial-drupal-7
[d8-kernel]: https://www.drupal.org/docs/8/testing/types-of-tests-in-drupal-8#s-kernel-tests
[d8-browser]: https://www.drupal.org/docs/8/testing/types-of-tests-in-drupal-8#s-browser-javascript-tests
[cucumberjs]: https://github.com/cucumber/cucumber-js
[chai]: https://www.chaijs.com

</section>
</section>


<!-- Integration tests. -->


<section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--integration.svg" data-background-size="25%" data-background-position="top right">

## Acceptance/Integration

**What?** mid-level, black-box tests for groups of components; covering how they communicate and work together

Only meaningful in larger systems with independent parts (e.g.: headless Drupal, federated search, endpoints beyond the web (<abbr title="Create Once Publish Everywhere">COPE</abbr>))

</section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--integration.svg" data-background-size="25%" data-background-position="top right">

### Acceptance/Integration (ctd.)

**Who?** by system architects or lead system designers, for developers; often in same language as component tests

**Synonyms** contract, choreography, conformance, plumbing; integration and testing (I&T)

**Can be part of** performance, throughput

</section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--integration.svg" data-background-size="25%" data-background-position="top right">

### Acceptance/Integration (ctd.)

**Key tech**<sup>5</sup>

* Contract conformance: [Janus][janus], [Pact][pact], [Pacto][pacto]
* Design/simulation: [Apiary][apiary], [API Blueprint][api-blueprint], [Hoverfly][hoverfly], [Swagger][swagger]
* Simulation/stubbing: [mountebank][mbtest], [inproctester][inproctester], [plasma][plasma], [vcr][vcr]

[apiary]: https://apiary.io
[api-blueprint]: https://apiblueprint.org
[hoverfly]: https://hoverfly.io
[inproctester]: https://github.com/aharin/inproctester
[janus]: https://github.com/gga/janus
[mbtest]: http://www.mbtest.org
[pact]: https://github.com/pact-foundation/pact-ruby
[pacto]: https://github.com/thoughtworks/pacto
[plasma]: https://github.com/plasma-dot-net/plasma
[swagger]: https://swagger.io
[vcr]: https://github.com/vcr/vcr

</section>
</section>


<!-- System tests. -->


<section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--system.svg" data-background-size="25%" data-background-position="top right">

## Acceptance/System

**What?** high-level, black-box tests; covering the whole system

**Who?** by system architects or

**Synonyms** end-to-end (E2E) testing

**Can be part of** accessibility, functional, load, performance, regression, throughput, user acceptance (alpha-testing, beta-testing), verification, validation testing; Independent Verification & Validation (ISVV)

</section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--system.svg" data-background-size="25%" data-background-position="top right">

### Acceptance/System (ctd.)

**Key tech**

* [D7 SimpleTest][d7-simpletest], [D8 kernel tests][d8-kernel], [D8 Browser/JS tests][d8-browser], [Nightwatch][nightwatch], [Selenium][selenium], [Wraith][wraith]
* Accessibility: [AChecker]achecker, [deque axe][axe], [WAVE toolbar][wave-toolbar]
* Load/performance/throughput: Capybara, Flood.io, Locust(?), [Valgrind][valgrind], [webprofiler][webprofiler]
* Security: Jtest, Metasploit, Parasoft, ZMap

[achecker]: https://achecker.ca
[axe]: https://www.deque.com/axe/
[nightwatch]: https://nightwatchjs.org
[selenium]: https://selenium.dev
[valgrind]: https://www.valgrind.org
[wave-toolbar]: http://wave.webaim.org
[webprofiler]: https://www.drupal.org/project/devel
[wraith]: http://bbc-news.github.io/wraith/

</section>
</section>


<!-- Other terms. -->
<section>
<section>

## Other terms

**Continuous delivery (CD)** — the practice of releasing people's work several times per day

**Continuous Integration (CI)** — the practice of merging multiple people's work together several times per day
    * *CI tools* or *CI/CD tools* often refer to automated programs (*task runners*) that run tests and merge automatically (e.g.: Hudson/Jenkins, CircleCI, TravisCI, etc.)

**Regression tests** — a check that new changes haven't broken old work

**Sanity tests** — a check of a program's logic/flow; or whether further testing is needed

</section>
<section>

### Other terms (ctd.)

**Smoke tests** — a check for obvious failure

**Test coverage** — a measure of how much of your application's behavior is verified by tests

**Test Driven Development (TDD)** — the act of writing tests *before* writing code

**Test fixture** — something to satisfy pre-conditions for the thing you're about to test

**Test suite** — some grouping of tests

</section>
</section>


<!-- Conclusion. -->


<section>
<section>

## Works cited

1. Beck, Test Driven Development By Example, Addison-Wesley, 2003. p.123
2. Martin, Clean Architecture, Prentice Hall, 2018. p.26
3. [Zaidman, An Overview of JavaScript Testing in 2019, WellDone Software / Medium, Feb. 2019.](https://medium.com/welldone-software/an-overview-of-javascript-testing-in-2019-264e19514d0a)
4. Martin, The Clean Coder, Prentice Hall, 2011. p.100,103,105-106,115-119
5. [Martin, Testing Strategies in a Microservice Architecture / MartinFowler.com, Nov. 2014](https://martinfowler.com/articles/microservice-testing/)

</section>
<section>

## Thanks!

* [Digital Echidna][echidna] for letting me work on this presentation during work hours
* [@alberto56][alberto56-drupalorg], [@Mirabuck][mirabuck-drupalorg] for walking me through TDD in Drupal while at [the Linux Foundation][linux-foundation]

[alberto56-drupalorg]: https://www.drupal.org/u/alberto56
[mirabuck-drupalorg]: https://www.drupal.org/u/mirabuck
[linux-foundation]: https://www.linuxfoundation.org

</section>
</section>
