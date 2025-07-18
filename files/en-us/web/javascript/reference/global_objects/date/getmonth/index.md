---
title: Date.prototype.getMonth()
short-title: getMonth()
slug: Web/JavaScript/Reference/Global_Objects/Date/getMonth
page-type: javascript-instance-method
browser-compat: javascript.builtins.Date.getMonth
sidebar: jsref
---

The **`getMonth()`** method of {{jsxref("Date")}} instances returns the month for this date according to local time, as a zero-based value (where zero indicates the first month of the year).

{{InteractiveExample("JavaScript Demo: Date.prototype.getMonth()", "shorter")}}

```js interactive-example
const moonLanding = new Date("July 20, 69 00:20:18");

console.log(moonLanding.getMonth()); // (January gives 0)
// Expected output: 6
```

## Syntax

```js-nolint
getMonth()
```

### Parameters

None.

### Return value

An integer, between 0 and 11, representing the month for the given date according to local time: 0 for January, 1 for February, and so on. Returns `NaN` if the date is [invalid](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date#the_epoch_timestamps_and_invalid_date).

## Description

The return value of `getMonth()` is zero-based, which is useful for indexing into arrays of months, for example:

```js
const valentines = new Date("1995-02-14");
const month = valentines.getMonth();
const monthNames = ["January", "February", "March" /* , … */];

console.log(monthNames[month]); // "February"
```

However, for the purpose of internationalization, you should prefer using {{jsxref("Intl.DateTimeFormat")}} with the `options` parameter instead.

```js
const options = { month: "long" };
console.log(new Intl.DateTimeFormat("en-US", options).format(valentines));
// "February"
console.log(new Intl.DateTimeFormat("de-DE", options).format(valentines));
// "Februar"
```

## Examples

### Using getMonth()

The `month` variable has value `11`, based on the value of the {{jsxref("Date")}} object `xmas95`.

```js
const xmas95 = new Date("1995-12-25T23:15:30");
const month = xmas95.getMonth();

console.log(month); // 11
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{jsxref("Date.prototype.getUTCMonth()")}}
- {{jsxref("Date.prototype.setMonth()")}}
