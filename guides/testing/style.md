# Test Style Guide

## Structure

* Include thoughtfully-worded, well-structured [ExUnit](https://hexdocs.pm/ex_unit/ExUnit.html)
  tests.
* Separate the three parts of the test (arrange, act, assert) with a single line, if any of the
  three parts are two lines or more. Otherwise keep all three parts/lines together
  (no line separation).

## Test docstrings

* Treat `describe` as the unit of work. It starts with a verb in present progressive tense (`-ing`)
* Treat `test` as a statement about the state under test and expected behaviour. It starts with
  a state/input, followed by the resulting behaviour.
* Avoid using commas in docstings to reduce the noise

## Variable names

* Variable names should express the input and expected state;
  e.g. `product_in_stock`, `order_with_new_line_item`
* The qualify names used in docstings are reflected in the variables names;
  e.g. "product in-stock" -> `product_in_stock`
* Always assign the value of a factory function to a variable even if it is not being used (underscore will be required) to help communicate then intent.

## Example

```elixir
describe "adding a product to a new order" do
  setup :new_order

  test "product in-stock returns an order with a new line item", %{new_order: new_order} do
    product_in_stock = create(:product, count_on_hand: 10)

    ok_result = Order.add_product(new_order, product_in_stock.id, qty = 3)

    assert {:ok, order_with_new_line_item} = ok_result
    assert Enum.find(order_with_new_line_item.line_items, &1.product_id == product_in_stock.id)
  end

  test "product out-of-stock returns an error" do
    product_out_of_stock = create(:product, count_on_hand: 0)

    error_result = Order.add_product(product_out_of_stock.id, qty = 3)

    assert {:error, :product_out_of_stock} = error_result
  end
end
```

## Credit

Some of this style guide is influenced by Roy Osherove's [Naming standards for unit tests](http://osherove.com/blog/2005/4/3/naming-standards-for-unit-tests.html).
