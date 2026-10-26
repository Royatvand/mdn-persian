---
title: "Number.isFinite()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/isFinite"
---

---
title: Number.isFinite()
short-title: isFinite()
slug: Web/JavaScript/Reference/Global_Objects/Number/isFinite
page-type: javascript-static-method
browser-compat: javascript.builtins.Number.isFinite
sidebar: jsref
---

متد ایستای **`Number.isFinite()`** بررسی می‌کند که مقدار ورودی یک عدد متناهی باشد؛ یعنی از نوع عدد باشد و نه مثبت یا منفیِ {{jsxref("Infinity")}} و نه {{jsxref("NaN")}}.

{{InteractiveExample("JavaScript Demo: Number.isFinite()")}}

```js interactive-example
console.log(Number.isFinite(1 / 0));
// Expected output: false

console.log(Number.isFinite(10 / 5));
// Expected output: true

console.log(Number.isFinite(0 / 0));
// Expected output: false
```

## نحو

```js-nolint
Number.isFinite(value)
```

### پارامترها

- `value`
  - : مقداری که متناهی بودن آن بررسی می‌شود.

### مقدار بازگشتی

اگر مقدار داده‌شده عددی متناهی باشد، `true` و در غیر این صورت `false` برمی‌گرداند.

## مثال‌ها

### استفاده از isFinite()

```js
Number.isFinite(Infinity); // false
Number.isFinite(NaN); // false
Number.isFinite(-Infinity); // false

Number.isFinite(0); // true
Number.isFinite(2e64); // true
```

### تفاوت Number.isFinite() با isFinite() سراسری

در مقایسه با تابع سراسری {{jsxref("isFinite()")}}، این متد ابتدا پارامتر را به عدد تبدیل نمی‌کند. بنابراین فقط مقادیر نوع `number` که متناهی باشند `true` برمی‌گردانند و مقادیر غیرعددی همیشه `false` خواهند بود.

```js
isFinite("0"); // true; coerced to number 0
Number.isFinite("0"); // false
isFinite(null); // true; coerced to number 0
Number.isFinite(null); // false
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Polyfill of `Number.isFinite` in `core-js`](https://github.com/zloirock/core-js#ecmascript-number)
- [es-shims polyfill of `Number.isFinite`](https://www.npmjs.com/package/number.isfinite)
- {{jsxref("Number")}}
- {{jsxref("isFinite()")}}
