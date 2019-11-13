---
title: Software testing overview - slides
---

<section>

# Software testing overview
— with [mparker17][mparker17-drupalorg]

<small>Follow along at [mparker17.github.io/talk--software-testing-overview](index.md)</small>

</section>
<section>

## Who am I?

[mparker17][mparker17-drupalorg] on Drupal.org, [Github][mparker17-github], and [Gitlab][mparker17-gitlab]

* Current employers: [Digital Echidna][echidna], [Brady's Meat & Deli][bradysmeats]
* Former employers: [Environment Canada][wsc], [Versabanq][versabanq], [UWaterloo][uwaterloo], [PeaceWorks][peaceworks], [Myplanet][myplanet], [OpenConcept Consulting][openconcept]
* Qualifications: [Acquia Certified Drupal Developer][acquia-cert], CS degree not completed at UWaterloo

</section>
<section>
<section>

## Types of software testing

<small>In my opinion there are 5 types...</small>

1. Unit tests
2. Interaction tests
3. Acceptance tests
4. System tests
5. Refinement tests

<small>...but be aware that not everyone agrees. Mine are roughly broken up by tool.</small>

</section>
<section>

Unit ▸ Interaction ▸ Acceptance ▸ System ▸ Refinement

In an ideal world...

| Unit tests         | Refinement tests       |
| ------------------ | ---------------------- |
| have Small scope   | have Large scope       |
| are Fast to run    | are Slow to run        |
| are Cheap to write | are Expensive to write |
| are Numerous       | are Sparse in number   |

</section>
<section>

**Unit** ▸ Interaction ▸ Acceptance ▸ System ▸ Refinement

<small>a.k.a. component tests</small>

* **What?** White-box tests to cover edge cases, code branches
* **Covers?** Code paths, individual components (functions)
* **How?** Test parameters, pre/post conditions, state changes, output. Mock dependencies.
* **Who writes?** Developer
* **When?** *Ideally* Before function code; *Last chance* Before commit
* **Key tech:** xUnit, mock objects (PHPUnit, RSpec, QUnit, Jasmine, Unit.js, Hamcrest)

</section>
<section>

Unit ▸ **Interaction** ▸ Acceptance ▸ System ▸ Refinement

<small>a.k.a. integration and testing, I&T</small>

* **What?** Grey-box tests to cover interactions between objects/interfaces
* **Covers?** Success/failure states, component interactions.
* **How?** Test subsystem inputs/outputs. Mock dependencies, shared resources, and IPC
* **Who writes?** Developer
* **When?** *Ideally* Before object code; *Last chance* Before merging feature-branch (while building).
* **Key tech:** xUnit, mock objects

</section>
<section>

Unit ▸ Interaction ▸ **Acceptance** ▸ System ▸ Refinement

<small>a.k.a. conformance tests, behaviour tests, functional tests, UAT, validation testing</small>

* **What?** Black-box tests to cover user paths through the system
* **Covers?** Functions correctly, can complete tasks, meets client's requirements
* **How?** Look at user story/ticket, write steps to complete
* **Who writes?** PO/Client/Tester/Developer
* **When?** *Ideally* Before UI; *Last chance* Before merging feature branch
* **Key tech:** Gherkin, SimpleTest, manual tests (Quail, Behat, Selenium; a11y/browser tests)

</section>
<section>

Unit ▸ Interaction ▸ Acceptance ▸ **System** ▸ Refinement

<small>a.k.a. end-user tests, field tests, regression tests</small>

* **What?** Black-box tests to cover the system as a whole and catch regressions
* **Covers?** The system as a whole
* **How?** Regression, performance, load/stress/volume, compatibility, recovery tests
* **Who writes?** Tester/Developer/PO
* **When?** After integrating code, before demo
* **Key tech:** Continuous integration tools, manual tests (New Relic)

</section>
<section>

Unit ▸ Interaction ▸ Acceptance ▸ System ▸ **Refinement**

<small>a.k.a. UX tests, usability tests, business-value tests, ROI tests, end-user tests, field tests</small>

* **What?** Black-box tests to determine if the proposed UI is useful, usable, aesthetic, identifiable,
inspirational and valuable
* **Covers?** End-user experience
* **How?** Present design to users, gather data on how they experience it
* **Who writes?** Designer/UX expert
* **When?** *Ideally* After 1st design proposal; *Last chance* Before finalizing design, after release
* **Key tech:** Visual diff tools, A/B testing frameworks, observation (Quail, Acquia Lift, PhantomJS, Selenium)

</section>
</section>

[mparker17-drupalorg]: https://www.drupal.org/u/mparker17
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
