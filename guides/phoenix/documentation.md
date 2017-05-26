# Documenting Elixir

- do not provide module-level documentation for modules suffixed with their archetype (e.g. `Service`, `Controller`, `Query`, `Repo`)
- apply `@module false` to these modules.
- [typespec](http://elixir-lang.org/getting-started/typespecs-and-behaviours.html#types-and-specs) is mandatory for public functions (except in controllers and views)
- there are recommendations for documenting specific archetypes:

## Services

As functions on services tend to delegate to domain concepts, function level `@doc` is optional, however type specs are still mandatory.

Example:

```elixir
defmodule MyApp.OrderService do
  @spec acknowledge(integer) :: {:ok, MyApp.Order.t}
  def acknowledge(order_id) do
    # ...
  end
end
```

The following conventions are under consider, **please ignore these for now**.

## Domain Concepts - Entities and Values

Domain concepts contain two sections:
  - `ddd-archetypes` listing the archetypes from Domain Driven Design:
    - entity
    - value
    - aggregate-root
    - event
    - command
  - `represents` what concept in the domain

Example:

```elixir
defmodule MyApp.Order
  @moduledoc """
  - ddd-archetypes: entity, aggregate-root
  - represents: the purchase of multiple `Product`s
  """

  @doc """
  Flags an `Order` as being acknowledge by a `Merchant`.
  """
  @spec acknowledge(MyApp.Order.t) :: Ecto.Changeset
  def acknowledge(order) do
    # ...
  end
end
```
