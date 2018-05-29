# The Elixir Style Guide Amendments

## Table of Contents

* [Introduction](#introduction)
* [The Guide](#the-guide)
  * [Source Code Layout](#source-code-layout)
  * [Syntax](#syntax)  
  * [Typespec](#typespecs)
  * [Documentation](#documentation)    

## Introduction

This documents outlines amendments to the [Elixir Community Style Guide](https://github.com/christopheradams/elixir_style_guide).
These amendments are items that are not covered in the Community Guide or in very rare cases where we
deviate from the community standard.

## The Guide

### Source Code Layout

* <a name="indentation"></a>
  Indention kills readability. If the body of the function is indented more than three soft tabs
  (i.e. 6 spaces), that is a smell that functions should be extracted, reducing the indention.
  <sup>[[link](#indentation)]</sup>     

### Syntax

* <a name="pipeline"></a>
  Do not visually "break" the pipeline; i.e. when piping into function that is formatted across
  multiple lines, extract that into a single line function.
  <sup>[[link](#pipeline)]</sup>

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

* <a name="with-else"></a>
  The head of the `with` macro should have single function calls.
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

* <a name="map-put-struct"></a>
  Do not use `Map.put/3` with a struct as it is possible to put a new key in the struct that
  that does not exist. Use `Map.replace!/3` instead or the merge syntax.
  <sup>[[link](#map-put-struct)]</sup>

    ```elixir
  # not preferred
  Map.put(my_struct, :bar, "foo")

  # preferred
  Map.replace!(my_struct, :bar, "foo")

  # ideal
  %{my_struct | bar: "foo"}
  ```

* <a name="conditional-macros"></a>
  When selecting a macro to implement a conditional statement, e.g. `if`, `case`, or `with`, it is easy to select a more complex macro than is required. We should always use the simpliest macro to express our intent.
  <sup>[[link](#conditional-macros)]</sup>

  ```elixir
  # not preferred
  case foo(bar) do
    true -> baz()
    _ -> nil
  end

  # preferred
  if foo(bar) do
    baz()
  end

  # not preferred
  case foo(bar) do
    true -> baz()
    false -> qux()
  end

  # preferred
  if foo(bar) do
    baz()
  else
    qux()
  end

  # not preferred
  with {:ok, bar} <- foo() do
    baz()
  else
    _ -> qux()
  end

  # preferred
  case foo() do
    {:ok, bar} -> baz()
    _ -> qux()
  end
  ```  

### Naming

* <a name="acronyms"></a>
    Treat acronyms as words in names (XmlHttpRequest not XMLHTTPRequest), even if the acronym is the entire name (class Html not class HTML).
    <sup>[[link](#acronyms)]</sup>

## Typespecs

* <a name="typespecs-required"></a>
  Add typespecs for all public functions.
  <sup>[[link](#typespecs-required)]</sup>

## Documentation

- do not provide module-level documentation for modules suffixed with their archetype (e.g. `Service`, `Controller`, `Query`, `Repo`)
- apply `@module false` to these modules.
- [typespec](http://elixir-lang.org/getting-started/typespecs-and-behaviours.html#types-and-specs) is mandatory for public functions (except in controllers and views)
