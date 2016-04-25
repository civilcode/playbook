# SMACSS - Scalable and Module Architecture for CSS

Summarized from the [Online Book](https://smacss.com/).

## Categories

Rules are categorized by:

1. Base: the defaults. Example:

```css
html, body, form { margin: 0; padding: 0; }
input[type=text] { border: 1px solid #999; }
a { color: #039; }
a:hover { color: #03C; }
```

2. Layout: divide the page into sections. Layouts hold one or more modules together.
3. Module: reusable, modular parts of our design. e.g. callouts, the sidebar sections, the product lists and so on.
4. State: describe how our modules or layouts will look when in a particular state. e.g. hidden or expanded, active or inactive, home page or the inside page.
5. Theme: describe how modules or layouts might look, most sites don't need it.

## Naming Rules

Prefixes

- Layout: `.l-` and `.grid-`
- State: `.is-`, e.g. `.is-hidden`, `.is-collapsed`
- Module: prefix is the name of the module, e.g. `callout`. Related elements within a module use the base name as a prefix. e.g. `.callout-caption`

```css
/* Example Module */
.example { }

/* Callout Module */
.callout { }

/* Callout Module with State */
.callout.is-collapsed { }

/* Form field module */
.field { }

/* Inline layout  */
.l-inline { }
```

## Layout Rules

- Major components identified by ID e.g. `#header, #footer`.
- Minor components are modules e.g. `.callout`
- Modified the layout with `.l-flipped` and `.l-fixed`

Grid module applied to OL or UL:

```css
.l-grid {
    margin: 0;
    padding: 0;
    list-style-type: none;
}

.l-grid > li {
    display: inline-block;
    margin: 0 0 10px 10px;

    /* IE7 hack to mimic inline-block on block elements */
    *display: inline;
    *zoom: 1;
}
```

## Module Rules

The goal of this approach is to  avoid "specificity issues that require adding even more selectors to battle against it or to quickly fall back to using !important."

- avoid using IDs and element selectors
- only class names
- only include a selector that includes semantics

```css
<div class="fld">
    <span class="fld-name">Folder Name</span>
    <span class="fld-items">(32 items)</span>
</div>
```

### Subsclassing

```css
.pod {
    width: 100%;
}
.pod input[type=text] {
    width: 50%;
}
.pod-constrained input[type=text] {
    width: 100%;
}

.pod-callout {
    width: 200px;
}
.pod-callout input[type=text] {
    width: 180px;
}
```

```html
<div class="pod pod-constrained">...</div>
<div class="pod pod-callout">...</div>
```

## State Rules

- global
- can apply to layout and/or module styles
- indicate a JavaScript dependency
- made to stand alone
- are usually built of a single class selector
- in contrast to sub-module styles, are applied to an element at render time and then are never changed again

```css
.is-hidden {
  display: none;
}
```

Rules for specific modules:

- the state class name should include the module name in it.
- state rule should also reside with the module rules and not with the rest of the global state rules

```css
.tab {
    background-color: purple;
    color: white;
}

.is-tab-active {
    background-color: white;
    color: black;
}
```
