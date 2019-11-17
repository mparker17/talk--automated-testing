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

I am an [Acquia Certified Drupal Developer][acquia-cert]

<small><abbr title="Computer Science">CS</abbr> degree not completed at UWaterloo</small>

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
[acquia-cert]: https://certification.acquia.com/user/843258

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

<div class="fragment fade-in-then-semi-out">

**Testing (verb)**

To evaluate<sup>1</sup> [a system for correctness]

</div>
<div class="fragment fade-in-then-semi-out">

**A test (noun)**

A procedure leading to acceptance or rejection<sup>1</sup> [of a system's correctness]

</div>
<div class="fragment fade-in-then-semi-out">

**But keep in mind...**

"Testing only shows the presence, not the absence, of bugs" — Edsger W. Dykstra<sup>2</sup>

</div>

</section>
</section>

<!-- Classifying tests. -->

<section>
<section>

## Approaches

1. Manual tests (get a person to test)
2. Automated tests (get the computer to test itself)

<div class="fragment">
<br />

We want to automate as many tests as possible to save time and money, but it's not possible / practical to automate _everything_.

</div>

</section>
<section>

## Types

1. Exploratory tests
2. System tests
3. Integration tests
4. Component tests
5. Unit tests

</section>
<section>

Unit ▸ Component ▸ Integration ▸ System ▸ Exploratory

<small>Exploratory tests are a special case, so let's ignore them for a bit.</small>

In an ideal world...

| Unit tests         | System tests           |
| ------------------ | ---------------------- |
| have Small scope   | have Large scope       |
| are Fast to run    | are Slow to run        |
| are Cheap to write | are Expensive to write |
| are Numerous       | are Sparse in number   |

</section>
<section>
<img src="assets/images/2019-11-14--test-automaton-pyramid--overview--color.svg" alt="" style="margin: 0; padding: 0;"/>
</section>
</section>

<!-- Unit tests. -->

<section>
<section>

## Unit tests

* **What?** highly-isolated, low-level, clear-box tests
* **Covers?** code paths and edge cases for small units and small group interactions
* **Who?** by developer for developer; in language of <abbr title="System Under Test">SUT</abbr>
* **Synonyms**
    * individual units — (couldn't find any)
    * unit groups — interaction, integration; integration & testing (I&T)

</section>
<section>

### Unit tests (ctd.)

* **When do I write them?**
    * Ideally — Before writing code
    * Last chance — Before <abbr title="Version Control System">VCS</abbr> commit
* **When do I run them?**
    1. Run the ones for the component you're working on as you are developing
    2. Run the whole test suite before VCS commit
    3. Run the whole test suite after merging

</section>
<section>

### Unit tests (ctd.)

* **Key tech**
    * PHP — [PHPUnit][phpunit], [php-hamcrest][php-hamcrest]
    * JavaScript — [Jest][jest] / [Jasmine][jasmine], [Mocha][mocha], [Ava][ava], [Unexpected][unexpectedjs] (previously QUnit, Unit.js)<sup>6</sup>
* **How-to/Patterns**:
    * **Manipulate** parameters and pre-/post-conditions with *fixtures*, and *parameterized tests (PUTs)*
    * **Verify** output and state changes with *assertions*, and *pattern matchers*
    * **Isolate** with *test doubles* (mocks, stubs, fakes, harnesses)

[phpunit]: https://phpunit.de
[php-hamcrest]: https://github.com/hamcrest/hamcrest-php
[jest]: https://jestjs.io
[jasmine]: https://jasmine.github.io
[mocha]: https://mochajs.org
[ava]: https://github.com/avajs/ava
[unexpectedjs]: https://unexpected.js.org/

</section>
</section>

<!-- Component tests. -->

<section>
<section>

## Component tests

* **What?** mid/high-level, grey-box tests
* **Covers?** happy-path for features and business rules (also obvious corner/alternate paths)
* **Who?** by <abbr title="Quality Assurance">QA</abbr> & business, for business; often in a behavioral <abbr title="Domain Specific Language">DSL</abbr>
* **When?** Ideally — Before feature is built<br />Last chance — Before merging feature
* **Synonyms** behaviour, confidence, validation; verification & validation (V&V)

</section>
<section>

### Component tests (ctd.)

* **Key tech**
    * The [Gherkin][gherkin] DSL
    * PHP — [Behat][behat]
    * JavaScript — [cucumber-js][cucumberjs], [Chai][chai]<sup>6</sup>
* **How-to/Patterns**
    * TODO

[gherkin]: https://cucumber.io/docs/gherkin/reference/
[cucumber]: https://cucumber.io
[behat]: https://behat.org
[cucumberjs]: https://github.com/cucumber/cucumber-js
[chai]: https://www.chaijs.com

</section>
</section>

<!-- Integration tests. -->

<section>
<section>

## Integration tests

* **What?** 
* **Covers?** 
* **Who?** 
* **When?** 
* **Synonyms** 

</section>
<section>

### Integration tests (ctd.)

</section>
</section>

<!-- System tests. -->

<section>
<section>

## System tests

* **What?** 
* **Covers?** 
* **Who?** 
* **When?** 
* **Synonyms** 

</section>
<section>

### System tests (ctd.)

* **Key tech**
* **How-to/Patterns**

</section>
</section>

<!-- Exploratory tests. -->

<section>
<section>

## Exploratory tests

* **What?** 
* **Covers?** 
* **Who?** 
* **When?** 
* **Synonyms** 

</section>
<section>

### Exploratory tests (ctd.)

* **Key tech**
* **How-to/Patterns**

</section>
</section>


<!-- Other terms. -->

<section>
<section>

## Other terms

1. **Regression tests** check that new changes haven't broken old work.
    * Unit, Component, Integration, and System tests can all act as regression tests.
    * You probably want to automate as many as you can to avoid a massive, time-consuming stack of manual tests to run after every change.
2. **Acceptance tests** check that the work meets the requirements of a specification or contract.
    * Unit, Component, Integration, and System tests can all act as acceptance tests.
    * These don't have to be automated.

</section>
<section>

## Other terms (ctd.)

3. **Test Driven Development** (TDD) — write tests *before* writing code to meet those tests
    * Unit and Component tests (and some System tests) can often be written first as per TDD
    * Benefits include certainty (that a change didn't break anything), defect reduction, courage (to make changes), documentation (by test), and (better) design<sup>4</sup>
    * Uncle Bob (Robert C. Martin) says the high cycle time stimulates productivity and reminds him of programming games as a kid<sup>5</sup>

</section>
<section>

## Other terms (ctd.)

4. **Test suite** — a bunch of tests
    * Unit, Component, Integration, and System tests could all be in the same suite
    * You probably only want to run the *whole test suite* (i.e.: every single test) once a day; for smaller tasks, you might want to run a smaller test suite
5. **Test coverage** — how much of your application has tests to verify its behaviour
6. 

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
