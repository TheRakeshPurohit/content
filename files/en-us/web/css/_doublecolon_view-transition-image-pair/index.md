---
title: ::view-transition-image-pair()
slug: Web/CSS/::view-transition-image-pair
page-type: css-pseudo-element
browser-compat: css.selectors.view-transition-image-pair
sidebar: cssref
---

The **`::view-transition-image-pair()`** [CSS](/en-US/docs/Web/CSS) [pseudo-element](/en-US/docs/Web/CSS/Pseudo-elements) represents a container for a [view transition's](/en-US/docs/Web/API/View_Transition_API) "old" and "new" view states — before and after the transition.

During a view transition, `::view-transition-image-pair()` is included in the associated pseudo-element tree as explained in [The view transition pseudo-element tree](/en-US/docs/Web/API/View_Transition_API/Using#the_view_transition_pseudo-element_tree). It is only ever a child of a {{cssxref("::view-transition-group()")}}. In terms of children, it can have a {{cssxref("::view-transition-new()")}} or a {{cssxref("::view-transition-old()")}}, or both.

`::view-transition-image-pair()` is given the following default styling in the UA stylesheet:

```css
:root::view-transition-image-pair(*) {
  position: absolute;
  inset: 0;

  animation-duration: inherit;
  animation-fill-mode: inherit;
  animation-delay: inherit;
}
```

During a view transition, `::view-transition-image-pair()` has {{cssxref("isolation", "isolation: isolate")}} set on it in the view transition style sheet so that its children can be blended with non-normal blend modes without affecting other visual outputs.

## Syntax

```css-nolint
::view-transition-image-pair([ <pt-name-selector> <pt-class-selector>? ] | <pt-class-selector>) {
  /* ... */
}
```

### Parameters

- `*`
  - : The [universal selector (`*`)](/en-US/docs/Web/CSS/Universal_selectors); selects all view transition groups on a page.
- `root`
  - : Causes the pseudo-element to match the default `root` view transition snapshot group created by the user agent to contain the view transition for the overall page. This group includes any element not assigned to its own specific view transition snapshot group via the {{cssxref("view-transition-name")}} property.
- `<pt-name-selector>`
  - : The {{cssxref("custom-ident")}} set as the value of the {{cssxref("view-transition-name")}} property.
- `<pt-class-selector>`
  - : The {{cssxref("custom-ident")}} set as the value of the {{cssxref("view-transition-class")}} property preceded by a period (`.`).

## Examples

```css
::view-transition-image-pair(root) {
  isolation: auto;
}

::view-transition-image-pair(.card) {
  isolation: isolate;
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [View Transition API](/en-US/docs/Web/API/View_Transition_API)
- [Smooth transitions with the View Transition API](https://developer.chrome.com/docs/web-platform/view-transitions/)
