# Test Style Guide

* Include thoughtfully-worded, well-structured [ExUnit](https://hexdocs.pm/ex_unit/ExUnit.html)
  tests.
* Treat `describe` as the unit of work.
* Treat `test` as a statement about the state under test and expected behaviour.
* Variable names should express the expected input and state; e.g. `invalid_customer_params`,
`empty_list`
* Separate the three parts of the test (arrange, act, assert) with a single line, if any of the three parts are two
  lines or more. Otherwise keep all three parts/lines together (no line separation).

```elixir
describe "sum" do
  test "negative number as 1st param throws exception" do
    # arrange, act, assert
  end

  test "negative number as 2nd param throws exception" do
    # arrange, act, assert    
  end

  test "simple values calculate" do
    # arrange, act, assert    
  end
end
```