---
title: Software testing overview - slides
---

<section>

# Software testing overview
— with [mparker17][mparker17-drupalorg]

<small>Follow along at [mparker17.github.io/talk--software-testing-overview](index.md)</small>

[mparker17-drupalorg]: https://www.drupal.org/u/mparker17

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
<img src="assets/images/2019-11-14--test-automaton-pyramid--overview--color.svg" alt="A pyramid with unit tests on the bottom, acceptance tests in the middle, and exploratory tests on the top." style="margin: 0; padding: 0;"/>
</section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--overview--color.svg" data-background-size="25%" data-background-position="top right">

### Classifying tests (ctd.)

1. Exploratory tests
2. Acceptance tests <small>(broken down into System, Integration, and Component tests)</small>
3. Unit tests

</section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--overview--color.svg" data-background-size="25%" data-background-position="top right">

### Classifying tests (ctd.)

<small>Ignoring exploratory tests for a moment...</small>

| Unit tests         | Acceptance tests       |
| ------------------ | ---------------------- |
| have Small scope   | have Large scope       |
| are Fast to run    | are Slow to run        |
| are Cheap to write | are Expensive to write |
| are Numerous       | are Sparse in number   |

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

**Can be part of** functional, regression testing

</section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--unit.svg" data-background-size="25%" data-background-position="top right">

### Unit tests (ctd.)

**When do I write them?**

* Ideally — Before writing code
* Last chance — Before <abbr title="Version Control System">VCS</abbr> commit

**When do I run them?**

1. Run the ones for the unit you're working on as you are developing
2. Run the whole test suite before VCS commit
3. Run the whole test suite after merging

</section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--unit.svg" data-background-size="25%" data-background-position="top right">

### Unit tests (ctd.)

* **Key tech**
    * PHP — [PHPUnit][phpunit], [php-hamcrest][php-hamcrest], [D8 UnitTestCase][d8-unittestcase]
    * JavaScript — [Jest][jest] / [Jasmine][jasmine], [Mocha][mocha], [Ava][ava], [Unexpected][unexpectedjs] (previously QUnit, Unit.js)<sup>6</sup>
* **How-to/Patterns**:
    * **Manipulate** parameters and pre-/post-conditions with *fixtures* and *parameterized tests (PUTs)*
    * **Verify** output and state changes with *assertions* and *pattern matchers*
    * **Isolate** with *test doubles* (mocks, stubs, fakes, harnesses)

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
<section>

## Acceptance tests

**What?** tests written by all stakeholders to communicate, clarify, and understand when a requirement is done.<sup>1, 2</sup>

**Who** Business analyists write the "happy path" because this describes business value,<sup>3</sup> — QA analysts write the "unhappy path" because their job is to help think about what can go wrong<sup>3</sup> — Developers provide input into both (what is possible, what else can go wrong)<sup>4</sup>

**Synonyms** (term overloaded and overused)

<sup>1</sup> Martin, The Clean Coder, Prentice Hall, 2011. p.100
<sup>2</sup> Martin, The Clean Coder, Prentice Hall, 2011. p.103
<sup>3</sup> Martin, The Clean Coder, Prentice Hall, 2011. p.105-106

</section>
<section>

### Acceptance tests (ctd.)

* **When do I write them?**
    * Ideally — First few acceptance tests for a feature should be ready by the first day of the sprint
    * Last chance — All acceptance tests for a feature should be ready by the mid-point of the sprint
* **When do I run them?**
    * While implementing the feature

</section>
<section>

### Acceptance tests (ctd.)

* **Key tech**
    * TODO
* **How-to/Patterns**:
    * TODO

</section>
</section>

<!-- Exploratory tests. -->

<section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--exploratory.svg" data-background-size="25%" data-background-position="top right">

## Exploratory tests

* **What?**
* **Who?**
* **Synonyms**
* **Can be part of**

</section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--exploratory.svg" data-background-size="25%" data-background-position="top right">

### Exploratory tests (ctd.)

* **When do I write them?**
* **When do I run them?**

</section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--exploratory.svg" data-background-size="25%" data-background-position="top right">

### Exploratory tests (ctd.)

* **Key tech**
* **How-to/Patterns**

</section>
</section>

<!-- Component tests. -->

<section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--component.svg" data-background-size="25%" data-background-position="top right">

## Acceptance/Component

* **What?** isolated, mid-level, grey-box tests for behavior; covering the happy-path for features and business rules (as well as obvious corner/alternate paths)
* **Who?** by <abbr title="Quality Assurance">QA</abbr> & business, for business; often in a behavioral <abbr title="Domain Specific Language">DSL</abbr>
* **Synonyms** behavior, confidence, validation; verification & validation (V&V)
* **Can be part of** acceptance, functional, regression

</section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--component.svg" data-background-size="25%" data-background-position="top right">

### Acceptance/Component (ctd.)

* **When do I write them?**
    * Ideally — Before starting work on a feature
    * Last chance — Before passing feature for review or merging
* **When do I run them?**
    1. Run the ones for the component you're working on as you are developing
    2. Run the whole test suite before VCS commit
    3. Run the whole test suite after merging

</section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--component.svg" data-background-size="25%" data-background-position="top right">

### Acceptance/Component (ctd.)

* **Key tech**
    * The [Gherkin][gherkin] DSL ("Given/When/Then")
    * PHP — [Behat][behat], [D7 SimpleTest][d7-simpletest], [D8 kernel tests][d8-kernel]
    * JavaScript — [cucumber-js][cucumberjs], [Chai][chai]<sup>6</sup>
* **How-to/Patterns**
    * Start with a **user story** ("As a/I want to/So that")
    * Stub **scenario titles** for that user story (success, obvious failure, etc.)
    * Fill out each scenario (given/when/then) in a **declarative** mode (high-level, low-detail)
    * Put low-level **details in the feature context**

[gherkin]: https://cucumber.io/docs/gherkin/reference/
[behat]: https://behat.org
[d7-simpletest]: https://www.drupal.org/docs/7/testing/simpletest-testing-tutorial-drupal-7
[d8-kernel]: https://www.drupal.org/docs/8/testing/types-of-tests-in-drupal-8#s-kernel-tests
[cucumberjs]: https://github.com/cucumber/cucumber-js
[chai]: https://www.chaijs.com

</section>
</section>

<!-- Integration tests. -->

<section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--integration.svg" data-background-size="25%" data-background-position="top right">

## Acceptance/Integration

* **What?** mid-level, black-box tests for groups of components; covering how they communicate and work together
    * Only meaningful in larger systems with independent parts (e.g.: headless Drupal, federated search, endpoints beyond the web (<abbr title="Create Once Publish Everywhere">COPE</abbr>))

</section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--integration.svg" data-background-size="25%" data-background-position="top right">

### Acceptance/Integration (ctd.)

* **Who?** by system architects or lead system designers, for developers; often in same language as component tests
* **Synonyms** choreography, conformance, plumbing
* **Can be part of** acceptance, performance, throughput
* **When do I write them?**
    * Ideally — before adding another major part
* **When do I run them?**
    * Periodically (nightly/weekly) as necessary; i.e.: not with regular CI suite

</section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--integration.svg" data-background-size="25%" data-background-position="top right">

### Acceptance/Integration (ctd.)

* **Key tech**
    * TODO
* **How-to/Patterns**
    * TODO

</section>
</section>

<!-- System tests. -->

<section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--system.svg" data-background-size="25%" data-background-position="top right">

## Acceptance/System

* **What?** high-level, black-box tests; covering the whole system
* **Who?** by system architects or
* **Synonyms**
* **Can be part of** acceptance, functional, performance, regression, throughput, validation

</section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--system.svg" data-background-size="25%" data-background-position="top right">

### Acceptance/System (ctd.)

* **When do I write them?**
* **When do I run them?**

</section>
<section data-background="assets/images/2019-11-14--test-automaton-pyramid--system.svg" data-background-size="25%" data-background-position="top right">

### Acceptance/System (ctd.)

* **Key tech**
    * PHP: [D8 Browser/JS tests][d8-browser]
* **How-to/Patterns**

[d8-browser]: https://www.drupal.org/docs/8/testing/types-of-tests-in-drupal-8#s-browser-javascript-tests

</section>
</section>

<!-- Conclusion. -->

<section>

# Thanks!

Works cited:

1. Beck, Test Driven Development By Example, Addison-Wesley, 2003. p.123
2. Martin, Clean Architecture, Prentice Hall, 2018. p.26
3. Martin, The Clean Coder, Prentice Hall, 2011. p.114
4. Martin, The Clean Coder, Prentice Hall, 2011. p.80-83
5. Martin, The Clean Coder, Prentice Hall, 2011. p.78
6. [Zaidman, An Overview of JavaScript Testing in 2019, WellDone Software / Medium, Feb. 2019.](https://medium.com/welldone-software/an-overview-of-javascript-testing-in-2019-264e19514d0a)

</section>
