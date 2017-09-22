# Aggregates

Vaughn Vernon describes aggregates best in his book [Domain-Driven Design Distilled](https://books.google.ca/books?id=k9zIDAAAQBAJ&printsec=frontcover&dq=Domain-Driven+Design+Distilled&hl=en&sa=X&redir_esc=y#v=onepage&q=Domain-Driven%20Design%20Distilled&f=false)

> …Aggregate is composed of one or more Entities, where one Entity is called the Aggregate Root.
Aggregates may also have Value Objects composed on them.

> The Root Entity of each Aggregate owns all the other elements clustered inside it.

> Each Aggregate forms a transactional consistency boundary. This means that within a single
Aggregate, all composed parts must be consistent, according to business rules, when the
controlling transaction is committed to the database. This doesn’t necessarily mean that you are
not supposed to compose other elements within an Aggregate that don’t need to be consistent after a
transaction. After all, an Aggregate also models a conceptual whole. But you should be first and
foremost concerned with transactional consistency.

> The reasons for the transactional boundary are business motivated, because it is the business
that determines what a valid state of the cluster should be at any given time. In other words, if
the Aggregate was not stored in a whole and valid state, the business operation that was performed
would be considered incorrect according to business rules.

He has four rules for basic aggregate design:

> 1. Protect business invariants inside Aggregate boundaries.
> 2. Design small Aggregates.
> 3. Reference other Aggregates by identity only.
> 4. Update other Aggregates using eventual consistency.

For more details read [Chapter 5 -- Tactical Design with Aggregates](https://books.google.ca/books?id=k9zIDAAAQBAJ&printsec=frontcover&dq=Domain-Driven+Design+Distilled&hl=en&sa=X&redir_esc=y#v=onepage&q=Domain-Driven%20Design%20Distilled&f=false)
from his book.

There are also some free references that are based on his book [Implementing Domain-Driven Design](https://books.google.ca/books?id=X7DpD5g3VP8C&printsec=frontcover&dq=Domain-Driven+Design&hl=en&sa=X&ved=0ahUKEwj9mr67rrnWAhUB3YMKHScjDzoQ6AEILDAB#v=onepage&q=Domain-Driven%20Design&f=false):

[Effective Aggregate Design - Part I: Modeling a Single Aggregate](http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_1.pdf)
[Effective Aggregate Design - Part II: Making Aggregates Work Together](http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)

Finally, Vladimir Khorikov's on [Domain-Driven in Practice](https://app.pluralsight.com/player?course=domain-driven-design-in-practice&author=vladimir-khorikov&name=domain-driven-design-in-practice-m1&clip=0)
has a good clip on [How to Find Boundaries for Aggregates](https://app.pluralsight.com/player?course=domain-driven-design-in-practice&author=vladimir-khorikov&name=domain-driven-design-in-practice-m4&clip=4) in
in the section titled [Extending the Bounded Context with Aggregates](https://app.pluralsight.com/player?course=domain-driven-design-in-practice&author=vladimir-khorikov&name=domain-driven-design-in-practice-m4&clip=0).
In this clip he discusses the idea of "one to many" versus "one to some". For example, a blog `post`
will have a "one to many" relationship with `comments`. You can imagine a blog `post` possibly
having hundreds of `comment`s. However, an `order` is more like a "one to some" than a "one to many"
relationship with `line-items`, where an `order` will only have a few `line-items`.

-
