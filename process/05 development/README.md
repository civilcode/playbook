# Development

## How we work

Before contributing to development there are a number of concepts you need to understand:

1. How we model the domain
2. How we develop features
3. How we automate acceptance tests

## How we develop features

We develop the application feature by feature using the [Feature-Driven Development](https://en.wikipedia.org/wiki/Feature-driven_development) process. This means:

1. We start with _Developing an Overall Object Model_
2. We _Build a Feature Roadmap_ based on the Object Model
3. We _Plan Feature Development_ based on the Roadmap
4. We [Design by Feature](./fdd/design-feature.md)
5. We [Build by Feature](./fdd/build-feature.md)

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

Then you're ready to [Build by Feature](./fdd/build-feature.md)...

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
