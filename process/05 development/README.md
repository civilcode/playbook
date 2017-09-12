# Development

## How we work

Before contributing to development there are a number of concepts you need to understand:

1. How we model the domain
2. How we develop features
3. How we automate acceptance tests

## 1. How we model the domain

See the [Object Modeling Trail](../../education/trails/object-modeling.md).

## 2. How we develop features

We develop the application feature by feature using the [Feature-Driven Development](https://en.wikipedia.org/wiki/Feature-driven_development) process. This means:

1. We start with _Developing an Overall [Object Model](../../education/trails/object-modeling.md)_
2. We [Build a Feature Roadmap](./fdd/feature-list.md) (module, feature-set, feature) based on the Object Model
3. We _Plan Feature Development_ based on the Roadmap
4. We [Design by Feature](./fdd/design-feature.md)
5. We [Build by Feature](./fdd/build-feature.md)

### Design by Feature

#### For each module:

- [ ] Complete Discovery using Eventstorming or Story Mapping (if not previously done so)
* Obtain any related documents
* Conduct a domain walk-through
* Model the state transitions
* Refine the object model (assign attributes)
* Determine business rules
* Identify UI components (mockup with [Balsamiq Mockups](https://balsamiq.com/products/mockups/)
* Specify the Acceptance Test (by example)

#### For each feature set:

* Add more detail to the mockups

#### For each feature:

1. [Design](./fdd/design-feature.md)
2. [Build](./fdd/build-feature.md)

## 3. How we automate acceptance tests

See the [Specification By Example Trail](../../education/trails/specification-by-example.md).
