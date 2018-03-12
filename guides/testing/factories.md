# Test Factories

## Life cycle or operational states

State is encapsulated by a function:

```elixir
# good

:order
|> build
|> as_complete

# bad

build(:order, state: "complete", completed_at: DateTime.utc_now)
```

Benefits:

* encompasses what is required to make the entity a specific state (it might be more than two attributes)
* if the state implmementation changes, it can be refactored in once place
* it avoids "magic strings" throughout the code base
