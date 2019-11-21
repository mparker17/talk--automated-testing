---
title: Software testing overview - speaker notes
layout: static
---

# Software testing overview
— with mparker17

Speaker notes

## 0/26 - (prep)

1. Screensaver off on computer, phone?
2. Slides working?
3. Speaker notes open on phone?
4. Wireless presenter working?
5. Mute slides, if applicable.

## 1/26 - (title)

1. Unmute slides, if applicable.
2. Can everyone hear me?
3. Shout-out to co-workers in the audience.
4. Start recording, if applicable.
5. Thank everyone for coming.
6. Thank hosts, if applicable.
7. ¤

## 2/26 - Who am I?

1. mparker17; but not on social media
2. I work for a web development firm...
    1. ... of about 80 people
    2. ... in London Ontario,
    3. ... called Digital Echidna,
    4. ... that focuses on open-source technologies... mostly Drupal.
    5. ... and offers professional software development, digital strategy, UX research, and support services.
3. Echidna's clients are mostly North American, and in the healthcare, higher education, and large scale non-profit sectors
4. What is an "Echidna"?
    1. It's an Australian, egg-laying mammal related to the platypus, but looks more like a hedgehog, with spiky quills.
    2. Echidnas - both the animals and my co-workers - are unique, resourceful, and adaptive.
5. You might remember us from conventions because we wear brightly-coloured hockey jerseys and give away cute plush Echidnas as convention booth swag.
6. ¤

## 3/26 - Who am I? (ctd.)

1. (see slide)
2. ¤

## 4/26 - Why test?

1. So this presentation is about software testing.
2. But you might ask "why should I care? I'm just making a small website, so there's no need to make any formal tests."
3. This may be true, but we're being paid to make software that works correctly, and tests are the only way we can be confident of that.
4. ¤

## 5/26 - Tests tell us that…

1. Plus, there's an increasing body of evidence that it takes less time to develop software when you build tests into it from the beginning.
2. Tests tell us that we're done implementing a feature because it works - we spend less time engineering stuff that the customer will never use
3. And they tell us that we haven't broken anything by working in that new feature.
4. And they tell us that our system can handle edge cases that the users of the system can throw at it.
5. ¤

## 6/26 - Dictionary definitions

1. So let's start by defining testing...
2. As a verb, it's evauating a software system for correctness
3. As a noun, it's a procedure leading to us accepting or rejecting that the software system is correct
4. However, keep in mind that testing won't prove your code is free from all bugs; just the ones you're checking for.
    1. This is why we call it "computer science" as opposed to "computer mathematics"
    2. This is a whole other conversation
5. ¤

## 7/26 - Approaching tests

1. So how should we approach software tests?
2. One approach is to run them manually
3. The other approach is to get the computer to test itself
4. We want to automate as many tests as possible to save time and money...
5. ... we don't want to end up with a 500-page manual test plan that requires 10 people and several hours to run, because that would be very expensive...
6. ...but it's also not practical to automate everything...
7. ... and it's not possible to automate certain types of testing - like user experience testing
8. ¤

## 8/26 - Classifying tests

1. So... software development is still a relatively new discipline.
2. Other disciplines have been around longer, and they had their own jargon and classification for testing.
3. So if you're confused about the jargon around software testing, that's because we often end up using terms imported from other disciplines, which don't quite fit what we do.
4. Fortunately, due to the work of people like Kent Beck and Robert C. Martin (aka Uncle Bob), we have...
5. ¤

## 9/26 - (testing automation pyramid)

1. ... the testing pyramid.
2. Note that I'm going to mostly go with Uncle Bob and Kent Beck's definitions, because they've done a lot of thinking about testing, and their way of classifying tests seem to be gaining traction.
3. The testing pyramid has unit tests on the bottom; acceptance tests in the middle, and exploratory tests on the top.
4. And we sub-divide acceptance tests into Component tests, Integration tests, and System tests.
5. ¤

# 10/26 - Classifying tests (ctd.)

1. We will go over all these terms and their synonyms in a bit.
2. ¤

# 11/26 - Classifying tests (ctd.)

1. Why a pyramid?
2. It serves to illustrate that we can/should build a testing system...
3. ... with a lot of low-level tests at the bottom
4. ... and use the confidence that gives us...
5. ... so we only need a few high-level tests at the top
6. ¤

## 12/26 - Unit tests

1. At the bottom of the testing pyramid are unit tests...
2. ... which test code paths
3. They're usually written by developers, for developers
4. ... in the same programming language as the "System Under Test"
5. Interaction tests, integration tests, and the term "integration and testing" often refer to unit tests of interactions between an object and its immediate neighbours
6. Unit tests are part of functional and regression testing
7. ¤

## 13/26 - Unit tests (ctd.)

1. If you've heard of PHPUnit, Hamcrest, Drupal 8's UnitTestCase, Jest, Jasmine, Mocha, Ava - the software not the record label - Unexpected, QUnit, or Unit.js, those are all used in unit testing.
2. ¤

## 14/26 - Acceptance tests

1. We'll break this down later; but in the middle of the pyramid are acceptance tests
2. Acceptance tests exist to communicate and clarify requirements, and understand when development is done
3. Business analysts usually write the first acceptance test cases, because they describe business value.
    1. "Happy path" refers to the "expected" or "ideal" workflow
4. QA analysts and UX designers usually write the next acceptance test cases, because they're specialists in thinking about how things can go wrong
5. Developers can usually think of more ways for things to go wrong, and can add to those acceptance tests
6. Note that "acceptance tests" is generally a really overloaded and overused term.
7. And recall we're going with Uncle Bob and Kent Beck's definitions here.
8. ¤

## 15/26 - Exploratory tests

1. At the top of the pyramid are exploratory tests
2. We use them to discover new "unhappy paths", confirm behaviors of both the system and the users, and evaluate if the system works as well as it can under human operation.
3. Pretty much any stakeholder can and do perform exploratory tests, even if they're not always formalized.
4. If you've heard of "field testing", "refinement testing", or "bug hunting", those often refer to exploratory tests.
5. Some types of exploratory tests are, A/B testing, accessibility testing, end-user testing, pentesting aka security testing, usability testing, and UX testing.
6. ¤

## 16/26 - Acceptance/Component

1. Let's break down Acceptance testing. A lower-level type of acceptance testing is "Component testing".
2. Component testing tests individual features
3. Like other types of acceptance testing, they're often written by QA and business, and test business value
4. You might have heard of "behavioral testing", "confidence testing", "validation testing", or "verification & validation"
5. Testing features is important for functional and regression testing.
6. ¤

## 17/26 - Acceptance/Component (ctd.)

1. Some tools for component testing are...
2. ...the "Gherkin" domain-specific-language (which you might know as Cucumber, or the Given/When/Then syntax)
3. ...also Behat, D8 Kernel tests, cucumber-js, and Chai.
4. ...D7's SimpleTest, and D8's Browser/JS tests can be considered component tests; but they also overlap a bit with system tests which we'll talk about in a minute
5. ¤

## 18/26 - Acceptance/Integration

1. Integration testing is only meaningful in larger systems with independent parts - like...
    1. headless Drupal,
    2. Create-Once-Publish-Everywhere (COPE) strategies where an app accesses the data in your Drupal website,
    3. or where you need other tools to put data from non-Drupal sources into your search index so you can perform federated searchings
2. Interaction tests cover how the independent parts act together
3. ¤

## 19/26 - Acceptance/Integration (ctd.)

1. Interaction tests are usually written by people who put together the plan for how these independent parts talk amongst themselves
2. You might have heard of "contract testing", "choreography testing", "conformance testing", "testing a system's plumbing", or "integration and testing" and these often refer to Integration tests.
3. Performance testing, and throughput testing often cover some parts of interaction testing
4. ¤

## 20/26 - Acceptance/Integration (ctd.)

1. If you've heard of Janus, Pact, Pacto, Apiary, API Blueprint, Hoverfly, Swagger, mount-e-bank, in-proc-tester, plasma, or vcr, these are all used in integration testing
2. ¤

## 21/26 - Acceptance/System

1. Finally, system tests. They cover the working system as a whole.
2. They're also known as "end-to-end" testing
3. Accessibility testing, functional testing, load testing, performane testing, regression testing, throughput testing, user acceptance testing (UAT), alpha testing, beta testing, verification, validation testing, and ISVV testing all overlap with system testing in some way
4. ¤

## 22/26 - Acceptance/System (ctd.)

1. D7's Simpletest, D8 Browser/JS tests, Nightwatch, Selenium, Wraith, AChecker, the "axe" accessibility scanner, the WAVE toolbar, Capybara, flood.io, I think there's a load tester called "locust" or something like that... valgrind, webprofile, jtest, metasploit, parasoft, and zee-map can all be used for various forms of system testing
2. ¤

## 23/26 - Other terms

1. We're almost done, but here are some other terms often associated with testing...
2. Continuous Delivery, and Continuous Integration are related disciplines that really benefit from automated testing
3. ...so sometimes test runners aka task runners, are called "CI / CD" tools
4. Regression testing is essentially a way to see if your changes broke something; and tests in most layers of the testing pyramid function as regression tests
5. ¤

## 24/26 - Other terms (ctd.)

1. Sanity tests can refer to two things...
2. ... either that a workflow makes sense and can be completed
3. ... or whether further testing is needed
4. ... sanity tests are usually ad-hoc, i.e.: rarely formalized
5. Smoke tests are also ad-hoc, and come from electrical engineering, where one informal way of testing what you just built is to plug it in to see if it catches fire
6. Test coverage is a measurement of how much of your software system can be verified by tests
7. Test Driven Development is the discipline, pioneered by Kent Beck, of writing tests before you write the code to make those tests pass.
    1. Unit and Component tests (and some System tests) can often be written first as per TDD
    2. Benefits include certainty (that a change didn't bgit reak anything), defect reduction, courage (to make changes), documentation (by test), and (better) design
    3. Uncle Bob (Robert C. Martin) says the high cycle time stimulates productivity and reminds him of programming video games as a kid
8. A "test fixture" is something you have to set up in order to test something - in software development, this usually involves test doubles like mocks, stubs, fakes, and test harnesses
9. And finally, a "test suite" is just some grouping of tests
10. ¤

## 25/26 - Works cited

1. Whew, that was a lot of jargon to cover. Hopefully your eyes haven't glazed over.
2. Here's some of the resources I used while putting together this presentation
3. ¤

## 26/26 - Thanks!

1. Thanks for sticking though this with me.
2. Thanks also to Digital Echidna, without whom I wouldn't have been able to complete this talk on time
3. Thanks also to my previous employer, OpenConcept, for whom I wrote a blog post a couple of years ago that covered some of this information.
4. Thanks also to Albert Albala, and Andrew Lindsay, whom I both worked with at the Linux Foundation, who patiently walked me through implementing TDD in Drupal.
