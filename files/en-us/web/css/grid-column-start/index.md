---
title: grid-column-start
slug: Web/CSS/grid-column-start
page-type: css-property
browser-compat: css.properties.grid-column-start
sidebar: cssref
---

The **`grid-column-start`** [CSS](/en-US/docs/Web/CSS) property specifies a grid item's start position within the grid column by contributing a line, a span, or nothing (automatic) to its grid placement. This start position defines the block-start edge of the {{glossary("grid areas", "grid area")}}.

{{InteractiveExample("CSS Demo: grid-column-start")}}

```css interactive-example-choice
grid-column-start: auto;
```

```css interactive-example-choice
grid-column-start: 2;
```

```css interactive-example-choice
grid-column-start: -1;
```

```css interactive-example-choice
grid-column-start: span 2;
```

```html interactive-example
<section class="default-example" id="default-example">
  <div class="example-container">
    <div class="transition-all" id="example-element">One</div>
    <div>Two</div>
    <div>Three</div>
  </div>
</section>
```

```css interactive-example
.example-container {
  border: 1px solid #c5c5c5;
  display: grid;
  grid-template-columns: 1fr 1.5fr 1fr;
  grid-template-rows: repeat(3, minmax(40px, auto));
  grid-gap: 10px;
  width: 200px;
}

.example-container > div {
  background-color: rgb(0 0 255 / 0.2);
  border: 3px solid blue;
}

#example-element {
  background-color: rgb(255 0 200 / 0.2);
  border: 3px solid rebeccapurple;
}
```

## Syntax

```css
/* Keyword value */
grid-column-start: auto;

/* <custom-ident> value */
grid-column-start: some-grid-area;

/* <integer> + <custom-ident> values */
grid-column-start: 2;
grid-column-start: some-grid-area 4;

/* span + <integer> + <custom-ident> values */
grid-column-start: span 3;
grid-column-start: span some-grid-area;
grid-column-start: span some-grid-area 5;

/* Global values */
grid-column-start: inherit;
grid-column-start: initial;
grid-column-start: revert;
grid-column-start: revert-layer;
grid-column-start: unset;
```

This property is specified as a single `<grid-line>` value. A `<grid-line>` value can be specified as:

- either the `auto` keyword
- or a `<custom-ident>` value
- or an `<integer>` value
- or both `<custom-ident>` and `<integer>`, separated by a space
- or the keyword `span` together with either a `<custom-ident>` or an `<integer>` or both.

### Values

- `auto`
  - : A keyword indicating that the property contributes nothing to the grid item's placement, indicating auto-placement, an automatic span, or a default span of `1`.
- `<custom-ident>`
  - : If there is a named line with the name `<custom-ident>-start`, it contributes the first such line to the grid item's placement.

    > [!NOTE]
    > Named grid areas automatically generate implicit named lines of this form, so specifying `grid-column-start: foo;` will choose the start edge of that named grid area (unless another line named `foo-start` was explicitly specified before it).

    Otherwise, this is treated as if the integer `1` had been specified along with the `<custom-ident>`.

- `<integer> && <custom-ident>?`
  - : Contributes the nth grid line to the grid item's placement. If a negative integer is given, it counts in reverse, starting from the end edge of the explicit grid.

    If a name is given as a `<custom-ident>`, only lines with that name are counted. If not enough lines with that name exist, all implicit grid lines are assumed to have that name for the purpose of finding this position.

    An {{cssxref("integer")}} value of `0` is invalid.

- `span && [ <integer> || <custom-ident> ]`
  - : Contributes a grid span to the grid item's placement, such that the column start edge of the grid item's grid area is n lines from the end edge.

    If a name is given as a `<custom-ident>`, only lines with that name are counted. If not enough lines with that name exist, all implicit grid lines on the side of the explicit grid corresponding to the search direction are assumed to have that name for the purpose of counting this span.

    If the \<integer> is omitted, it defaults to `1`. Negative integers and `0` are invalid.

    The `<custom-ident>` cannot take the `span` and `auto` values.

## Formal definition

{{cssinfo}}

## Formal syntax

{{csssyntax}}

## Examples

### Setting column start for a grid item

#### HTML

```html
<div class="wrapper">
  <div class="box1">One</div>
  <div class="box2">Two</div>
  <div class="box3">Three</div>
  <div class="box4">Four</div>
  <div class="box5">Five</div>
</div>
```

#### CSS

```css
.wrapper {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-auto-rows: 100px;
}

.box1 {
  grid-column-start: 1;
  grid-column-end: 4;
  grid-row-start: 1;
  grid-row-end: 3;
}

.box2 {
  grid-column-start: 1;
  grid-row-start: 3;
  grid-row-end: 5;
}
```

```css hidden
* {
  box-sizing: border-box;
}

.wrapper {
  border: 2px solid #f76707;
  border-radius: 5px;
  background-color: #fff4e6;
}

.wrapper > div {
  border: 2px solid #ffa94d;
  border-radius: 5px;
  background-color: #ffd8a8;
  padding: 1em;
  color: #d9480f;
}

.nested {
  border: 2px solid #ffec99;
  border-radius: 5px;
  background-color: #fff9db;
  padding: 1em;
}
```

#### Result

{{ EmbedLiveSample('Setting_column_start_for_a_grid_item', '230', '420') }}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{cssxref("grid-column-end")}}
- {{cssxref("grid-column")}}
- {{cssxref("grid-row-start")}}
- {{cssxref("grid-row-end")}}
- {{cssxref("grid-row")}}
- [Line-based placement with CSS grid](/en-US/docs/Web/CSS/CSS_grid_layout/Grid_layout_using_line-based_placement)
- Video: [Line-based placement](https://gridbyexample.com/video/series-line-based-placement/)
