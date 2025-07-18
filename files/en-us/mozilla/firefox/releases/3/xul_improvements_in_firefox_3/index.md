---
title: XUL improvements in Firefox 3
slug: Mozilla/Firefox/Releases/3/XUL_improvements_in_Firefox_3
page-type: guide
sidebar: firefox
---

Firefox 3 provides a number of new XUL elements, as well as improvements to existing elements. While this material is documented in detail elsewhere, this article provides a convenient list of these improvements as well as links to the detailed documentation.

### New elements

- Numeric controls:
  - The new `<scale>` element lets you create sliding scales that let the user select any value in a specified range. This widget would typically be used, for example, to create a volume control.
  - A new value, `number`, for the `type` attribute of textboxes creates a textbox in which only numbers may be entered. In addition, arrow buttons appear to one side which may be used to step through values. [More information about numeric textboxes](https://wiki.mozilla.org/XUL:Specs:NumberBox). ([Firefox bug 345510](https://bugzil.la/345510))
  - A `<spinbuttons>` element is added which can be used when creating widgets using XBL bindings. ([Firefox bug 155053](https://bugzil.la/155053))
  - Two widgets, `<datepicker>` and `<timepicker>`, can be used to allow the entry of dates and times. The datepicker is available in a number of styles by setting the `type` attribute, to allow entry with textboxes or a calendar grid. [More information about date pickers.](https://wiki.mozilla.org/XUL:Specs:DateTimePickers)

- A guide has been created for menus and popups describing new features available:
  - A `<dropmarker>` element is added which is useful when creating menu-like widgets using XBL bindings. ([Firefox bug 348614](https://bugzil.la/348614))
  - The `<panel>` element is new and designed for popups that are not menus. They can support any type of content. The \<menupopup> element should be used for menus. Menus provide keyboard navigation and support opening and closing submenus.

### Improvements to trees

- Trees can now be scrolled horizontally. If the columns don't fit into the available width, a horizontal scrollbar appears. This happens if the columns' specified widths add up to more than the available space. See [Firefox bug 212789](https://bugzil.la/212789) for details.
- A new selection style allows cells to be selected individually, instead of entire rows. To use this selection style, set the tree's `seltype` attribute to `cell`.
- Trees now support editing of individual cells. When the user double-clicks an editable cell, a text field appears in which the user can edit the cell's contents. See [these notes](https://wiki.mozilla.org/XUL:Tree) for details.
- \<treecol> elements now support an `overflow` attribute which may be set to true to allow the text of cells within that column to expand to neighboring blank cells if the text is too large to fit into that single cell.

### Improvements to menus

- The `image` attribute is now used consistently for setting images.
- Menu lists fire the `select` event when selecting an item.
- The `inputField` and `editable` properties have been added to menulist
- The `<menu>`, `<menuitem>` and `<menuseparator>` elements now have a readonly `selected` property which retrieves whether the item is selected in a \<menulist>
- The `<menu>`, `<menuitem>` and `<menuseparator>` elements now have a readonly `control` property which returns the enclosing \<menulist>
- The `<menu>`, `<menuitem>` and `<menuseparator>` elements now support the `accessKey`, `disabled`, `crop`, `image` and `label` properties which set the corresponding attribute
- The \<menu> element now has methods to append, insert and remove menuitems. ([Firefox bug 372552](https://bugzil.la/372552))
- Editable menu lists now offer an `editor` property to get the internal `nsIEditor` for its text field.
- Menus may now be made translucent on platforms that support it ([Firefox bug 70798](https://bugzil.la/70798)).

### Improvements to textboxes

- Setting a textbox's `spellcheck` attribute to `true` enables inline spellchecking for that textbox.
- The `<textbox>` now has a `reset()` method to reset the value of the textbox to the default value. The `defaultValue` property may be used to retrieve and modify the default value of the textbox.
- An `editor` property is now offered, which lets you get the internal `nsIEditor` for the text field.
- `textbox` now supports a `newlines` attribute which specifies how line breaks in pasted text are handled. Possible values are:
  - `pasteintact` - paste everything as is
  - `pastetofirst` - (default value) paste only up to the first line break
  - `replacewithspaces` - replace line breaks with spaces
  - `replacewithcommas` - replace line breaks with commas
  - `strip` - strip out all line breaks
  - `stripsurroundingwhitespace` - strip out all line breaks and surrounding whitespace

### Other improvements

- The `type` attribute on a `<button>` may be set to `repeat` to create buttons which fire their command event repeatedly while the mouse button is held down.
- The `buttondisabledaccept` attribute can now be used on the `<dialog>` element to have the accept (OK) button initially disabled.
- The `<titlebar>` element now supports the `allowevents` attribute to allow events to be passed to the children of the titlebar.
- The `<splitter>` now supports an additional value for the `collapse` attribute of `'both'` which indicates that the splitter can collapse elements on both sides of it when dragged. The `substate` attribute will set to either before or after when one is collapsed. ([Firefox bug 337955](https://bugzil.la/337955))
- The `<richlistbox>` element now supports multiple selection. Set the `seltype` attribute to `'multiple'` to enable this.
- The `<radio>` element has a `group` attribute which may be set to the id of a `<radiogroup>` element which the radio button belongs to. This allows the radio buttons to arranged in a manner that may not be as suitable when placing them all inside a radiogroup.
- Menus, panels and tooltips support two additional methods, `openPopup()` and `openPopupAtScreen()`. These methods should be used instead of `showPopup()` which was found to be confusing to use.
- Handling of the `<key>` element improved for non-Latin keyboard layout users.
- On Mac OS X, the `activetitlebarcolor` and `inactivetitlebarcolor` attributes of the root elements (`<window>`, `<dialog>`, `<prefwindow>` and `<wizard>`) are available to customize the color of the windows' title bars.

### See also

- [Firefox 3 for developers](/en-US/docs/Mozilla/Firefox/Releases/3)
