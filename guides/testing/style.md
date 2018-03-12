# Test Style Guide

## General

* Include thoughtfully-worded, well-structured [ExUnit](https://hexdocs.pm/ex_unit/ExUnit.html)
  tests.
* Separate the three parts of the test (arrange, act, assert) with a single line, if any of the three parts are two
  lines or more. Otherwise keep all three parts/lines together (no line separation).
* Variable names should express the expected input and state; e.g. `invalid_customer_params`,
`empty_list`

## Test docstrings

* Treat `describe` as the unit of work. It starts with a verb in present progressive tense (`-ing`)
* Treat `test` as a statement about the state under test and expected behaviour. It starts with a state/input, followed by the resulting behaviour.

```elixir
describe "adding numbers" do
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

## Credit

Some of this style guide is influenced by Roy Osherove's [Naming standards for unit tests](http://osherove.com/blog/2005/4/3/naming-standards-for-unit-tests.html).
  
