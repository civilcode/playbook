# Elixir Architecture Cheatsheet

The architecture we use is heavily influenced by the [example application](https://github.com/VaughnVernon/IDDD_Samples) from Vaughn Vernon's [Implementing Domain-Driven Design](https://vaughnvernon.co/?page_id=168#iddd).

## The Basics

* favor pure functions over impure
* impure functions are those who have side-effects (read, write to DB, sending email) -- anything to do with the "outside" world
* don't call an impure function from a pure function. You've just made it impure :-(
* use a dedicated function to co-ordinate pure and impure functions (e.g. a public function in a `Service` module)
* impure functions are used at the boundaries

## Application/Domain Layer

### Overview

TODO: add diagram

### Service and Query modules

* entry point into the domain is via a `Service` and `Query` modules
* `Service` modules are for commands/writes
* `Query` modules are for reads
* `Service` and `Query` modules are entirely independent of each other (i.e. `Service` does not call a `Query` module)
* `Query` modules could be reading an entirely different database (i.e. a slave) or an entirely different store all together (i.e. CouchDB)
* Inspiration from [CQRS](https://martinfowler.com/bliki/CQRS.html)

### Service modules

* the "write" side
* responsible for processing business use cases
* contain functions reflecting commands to operate on an aggregate
* typically following the pattern of `impure` -> `pure` -> `impure` function calls
* e.g. `read from the repo` -> `call domain logic` -> `write to the repo`
* `Service` modules hydrate domain concepts from a repo, call a function(s) to perform domain logic and then write the "modified" domain concept to the database.
* Top level/public `Service` functions should be only a pipeline (either `|>` or `with`) providing a high-level overview of the processing steps.

**Example**

```elixir
defmodule MyApp.OrderService do
  @moduledoc false

  require Ecto.Query
  alias MyApp.{Order, Repo}

  def acknowledge(%{"order_id" => order_id}, seller_id) do
    with order = fetch_order(order_id, seller_id)
        {:ok, changeset} <- Order.acknowledge(order),
    do: Repo.update(changeset)
  end

  defp fetch_order(order_id, seller_id) do
    Order
    |> Order.for_seller_id(seller_id)
    |> Repo.get(order_id)
  end
end
```

### Domain modules

* represent domain concepts, e.g. entities (aggregates), values
* manage [aggregates](https://martinfowler.com/bliki/DDD_Aggregate.html)
  * manage transactions
  * enforces invariants
* e.g. `Order` -> `LineItem`
  * always work with these as a unit
  * the changeset includes the root `Order` and the children `LineItem`
  * `Order.add_line_item(order, params)` -> an order changeset with a new line item
* contain functions for business logic respecting business rules
* called by `Service` modules
* domain modules do not reference the upper layers (i.e. `Service` or `Query`)
* i.e. all functions are _pure_
* contain _scopes_, _actions_, and _predicates_
* _scopes_ return query types
* _actions_ return changesets
* use domain focused names for actions (i.e. not `insert_changeset`)
* _predicates_ return a boolean

**Example**

```elixir
defmodule MyApp.Order
  use ChannelAdvisor.Schema

  schema "orders" do
  #...
  end

  # actions

  def acknowledge(order) do
    change(order, order_status: "AcknowledgedBySeller")
  end

  #...

  # predicates

  def released_for_shipment?(%{order_status: "ReleasedForShipment"}), do: true
  def released_for_shipment?(_), do: false

  #...

  # scopes

  def for_seller_id(query, seller_id) do
    from(order in query, where: order.seller_id == ^seller_id)
  end

  #...
end

```

## Query modules

* an entry point into the application
* the "read" side
* calls to "scopes" on `Domain` modules and `Repo`
* called by `GET` requests in controllers or the equivalent in GraphQL
* query modules don't call other query modules

**Example**

```elixir
defmodule MyApp.OrderQuery do
  alias MyApp.{Order, Repo}

  def fetch_orders(%{"status" => status, "limit" => limit}, seller_id) do
    Order
    |> Order.for_seller_id(seller_id)
    |> Order.for_order_status(params["status"])
    |> Order.order_by_oldest
    |> Order.limit(params["limit"])
    |> Repo.all
    |> Repo.preload([:items, :buyer_address, :shipping_address])
  end
end
```

## Transforming Collections

The following guidance is *vitally important*:

* design your functions for processing collection of items as you would a single item
* that pattern again: `impure` -> `pure` -> `impure` function calls
* this allows you to leverage lazy evaluation, streaming SQL calls in the future
* See [Collection Pipeline](https://martinfowler.com/articles/collection-pipeline/)

## Represent (new) concerns as modules

- avoid "god" modules
- compose the application with small modules representing a specific concern
- avoid circular dependencies between modules `Approvals` -> `Catalog`
- when referencing modules from a different name space, use a qualified module name, (e.g. when referencing `Variant` in the `Catalog` module, just alias `MyApp.Catalog`, and reference `Catalog.Variant` in functions). This highlights references to referencing modules outside of the current context
- create "shadow" modules that represent existing domain concepts in different Concerns
- e.g. `Catalog.Variant` is an existing domain concept that can be represented in other contexts as `Approvals.Variant`
- consider creating specific schemas as well
- ["Optimize for Deletability"](https://vimeo.com/108441214) (i.e. how easy can the module be deleted)
- think service oriented architecture or micro-services in a monolith
