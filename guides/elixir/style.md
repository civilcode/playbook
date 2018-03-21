# The Elixir Style Guide Amendments

## Table of Contents

* [Introduction](#introduction)
* [The Guide](#the-guide)
  * [Source Code Layout](#source-code-layout)
  * [Syntax](#syntax)  
  * [Typespec](#typespecs)    

## Introduction

This documents outlines amendments to the [Elixir Community Style Guide](https://github.com/christopheradams/elixir_style_guide).
These amendments are items that are not covered in the Community Guide or in very rare cases where we
deviate from the community standard.

## The Guide

### Source Code Layout

Alignment of parameters is not addressed in the Community Guide.

* <a name="align-parameters"></a>
  Use the single indent style for aligning parameters when
  conforming to line-length constraints.
  <sup>[[link](#align-parameters)]</sup>

  ```elixir  
  # single line
  Order.ship(order, params)

  # multi-line
  Order.ship(
    order,
    params
  )
  ```  

* <a name="align-keywords"></a>
  With keyword lists, these are aligned separately to other params. This style is mostly applicable for factory libraries.
  <sup>[[link](#align-keywords)]</sup>

  ```elixir
  # single line
  order = build(:order, customer: customer, seller: seller, quantity: 3)

  # explanation only - do not use  
  order = build(:order, [
    customer_id: seller_id,
    quantity: 3
  ])

  # multi-line - preferred  
  order = build(:order,
    customer_id: seller_id,
    quantity: 3
  )  
  ```

* <a name="align-anon-functions"></a>
  The body of anonymous function starts on a new line. Single
  line anonymous functions as a parameter are allowed only
  with the capture syntax.
  <sup>[[link](#align-anon-functions)]</sup>  

  ```elixir
  # not preferred
  Enum.find_index([2, 3, 4], fn(x) -> rem(x, 2) == 1 end)  

  # preferred
  Enum.find_index([2, 3, 4], fn(x) ->
    rem(x, 2) == 1
  end)

  # preferred
  Enum.find_index([2, 3, 4], &(rem(&1, 2) == 1))

  # multi-line - preferred
  Enum.find_index(
    [2, 3, 4],
    &(rem(&1, 2) == 1)
  )     
  ```  

### Syntax

* <a name="with-else"></a>
  If the `with` expression has a `do` block with more than one line, or has an
  `else` option, use multiline syntax.
  <sup>[[link](#with-else)]</sup>

  ```elixir
  with {:ok, foo} <- fetch(opts, :foo),
       {:ok, bar} <- fetch(opts, :bar)
  do
    {:ok, foo, bar}
  else
    :error ->
      {:error, :bad_arg}
  end
  ```

  NOTE: this is a deviation from the [community guide](https://github.com/christopheradams/elixir_style_guide#with-else
). The `do` is aligned with the other keywords. This makes it easier to see the body of the `do` block as there maybe multiple statements in the `with` block.

* <a name="pipeline"></a>
  Do not visually "break" the pipeline; i.e. when piping into function that is formatted across
  multiple lines, extract that into a single line function.

  ```elixir
  # not preferred
  foo
  |> Enum.map(fn(%{bar: bar, qux: qux}) ->
        upcased = String.upcase(bar)
        {:ok, upcased, qux}
    end)
  |> baz

  # preferred
  foo
  |> Enum.map(&extracted_function/1)
  |> baz

  def extracted_function(%{bar: bar, qux: qux}) do
    upcased = String.upcase(bar)
    {:ok, upcased, qux}
  end
  ```

* <a name="map-put-struct"></a>
  Do not use `Map.put/3` with a struct as it is possible to put a new key in the struct that
  that does not exist. Use `Map.replace!/3` instead or the merge syntax.

    ```elixir
  # not preferred
  Map.put(my_struct, :bar, "foo")

  # preferred
  Map.replace!(my_struct, :bar, "foo")

  # ideal
  %{my_struct | bar: "foo"}
  ```

### Naming

* <a name="acronyms"></a>
    Treat acronyms as words in names (XmlHttpRequest not XMLHTTPRequest), even if the acronym is the entire name (class Html not class HTML).
    <sup>[[link](#acronyms)]</sup>

## Typespecs

* <a name="typespecs-required"></a>
  Add typespecs for all public functions.
* If the spec does not fit on one line, indent using two spaces and place the `::` separator at the end of the line:

  ```elixir
  @spec calculate_payouts(shipment_id :: number) ::
    {:ok, PayoutWithALongNameToShowHowToSplitTheLine.t} |
    {:error, reason :: String.t | atom}
  ```    
