# Development

## How work

Before contributing to development there are a number of concepts you need to understand:

1. How we model the domain
2. How we develop features
3. How we automate acceptance tests

We leverage the following techniques:

1. Modelling the domain: Peter Coad's Object Modeling Technique (aka "Modeling in Colour")
2. Develop features: Feature Driven-Design (FDD)
3. Acceptance Tests: Example by Specification via Cucumber (aka Behaviour-driven Development)

It is recommended to review the following resources explaining these techniques:

1. Peter Coad's Object Modeling Technique
    * Nicholas' introductory talk [Modeling on the Right Side of the Brain](http://blog.firsthand.ca/2014/04/modeling-on-right-side-of-brain.html)
    * Stephen. R. Palmer's Online Documentation ([Online](http://www.step-10.com/SoftwareDesign/ModellingInColour/index.html) | [PDF Format](https://www.dropbox.com/s/66spkldm40foh5l/Peter%20Coad%27s%20Modeling%20in%20Color.pdf?dl=0))
    * The book [Java Modeling In Color With UML: Enterprise Components and Process](http://www.amazon.com/Java-Modeling-Color-UML-Enterprise/dp/013011510X/ref=sr_1_1?ie=UTF8&qid=1447701102&sr=8-1&keywords=modeling+in+colour) - however Palmer's online document is sufficient.
2. Feature-driven Design
    * While we don't following FDD to the letter, it's an important concept that drives how we manage the project and structure the application.
    * [Wikipedia Entry](https://en.wikipedia.org/wiki/Feature-driven_development)
    * The book [A Practical Guide to Feature-Driven Development](http://www.amazon.com/Practical-Guide-Feature-Driven-Development/dp/0130676152/ref=sr_1_1?ie=UTF8&qid=1447701643&sr=8-1&keywords=feature+driven+development)
3. Example by Specification via Cucumber
    * We design our acceptance tests based on the approach prescribed in [Cucumber School](https://cucumber.io/school), there we highly recommend viewing this screencast series.

## How we develop features

We develop the application feature by feature using the [Feature-Driven Development](https://en.wikipedia.org/wiki/Feature-driven_development) process. This means:

1. We start with _Developing an Overall Object Model_
2. We _Build a Feature Roadmap_ based on the Object Model
3. We _Plan Feature Development_ based on the Roadmap
4. We [[Design by Feature]]
5. We [[Build by Feature]]

## Design by Feature

## For each module:

* Obtain any related documents
* Conduct a domain walk-through
* Model the state transitions
* Refine the object model (assign attributes)
* Determine business rules
* Identify UI components (mockup with [Balsamiq Mockups](https://balsamiq.com/products/mockups/)
* Specify the Acceptance Test (by example)

## For each feature set:

* Add more detail to the mockups

Then you're ready to [[Build by Feature]]...

## Peer Review

- [ ] review code
- [ ] check I18n
- [ ] review against style guides
- [ ] review database design
- [ ] review development log (SQL)
- [ ] review demo seeds
- [ ] verify feature/exploratory testing (manual)
- [ ] verify data migration
- [ ] verify code coverage (i.e. check output from simplecov)
- [ ] verify acceptance test answers the 6W's (why, what, who, when, where, how)
