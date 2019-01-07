# Build a Feature List

| Type               | Template                       | Example                      | CivilCode | Story Mapping [1] |
| ------------------ | ------------------------------ | ---------------------------- | --------- | ----------------- |
| Major Feature Sets | `<object> management`          | Car Service Management       | Module    | Areas             |
| Feature Sets       | `<action><-ing> a(n) <object>` | Scheduling a Service         | Ability   | Activities        |
| Feature            | `<action><result><object>`     | Schedule a service for a car | Task      | Tasks             |

* Features are granular (max. than 3-days, most take less)
* Full feature template: `<action> the <result> <by|for|of|to> a(n) <object>`

For example **Car Service Management**:

**Scheduling a Service**

1. Schedule a _service_ for a car.
2. Add a _new customer_ to a customer list.

**Performing a Service**

1. Record a _service performed_ for a car.
2. Record a list of parts used for a service.
3. Record a total of labor expended for a service.

**Billing a Service**

1. Calculate a total cost of parts used for a service.
2. Calculate a total cost of labor expended for a service.
3. Calculate a total cost of tax of a service.
4. Create a bill for a service.
5. Send a bill to a customer.
6. Receive a payment for a service.
7. Print a receipt for a customer.

## Extras

Also include the following:

* lists (e.g. List all pending services for the station)
* reports (e.g. Report on average service total for the station)
* constraints (e.g. Determine the customer's account is in good standing)

## Footnotes

1. Influences by [Thoughworks Blog Post](https://www.thoughtworks.com/insights/blog/story-mapping-visual-way-building-product-backlog)
