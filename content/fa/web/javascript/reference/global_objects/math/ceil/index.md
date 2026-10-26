---
title: "Math.ceil()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/ceil"
---

---
title: Math.ceil()
short-title: ceil()
slug: Web/JavaScript/Reference/Global_Objects/Math/ceil
page-type: javascript-static-method
browser-compat: javascript.builtins.Math.ceil
sidebar: jsref
---

متد ایستای **`Math.ceil()`** همیشه عدد را به سمت بالا گرد می‌کند و کوچک‌ترین عدد صحیح بزرگ‌تر یا مساوی عدد ورودی را برمی‌گرداند.

{{InteractiveExample("JavaScript Demo: Math.ceil()")}}

```js interactive-example
console.log(Math.ceil(0.95));
// Expected output: 1

console.log(Math.ceil(4));
// Expected output: 4

console.log(Math.ceil(7.004));
// Expected output: 8

console.log(Math.ceil(-7.004));
// Expected output: -7
```

## نحو

```js-nolint
Math.ceil(x)
```

### پارامترها

- `x`
  - : یک عدد.

### مقدار بازگشتی

کوچک‌ترین عدد صحیح بزرگ‌تر یا مساوی `x`؛ این مقدار با [`-Math.floor(-x)`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/floor) برابر است.

## توضیحات

چون `ceil()` متدی ایستا از `Math` است، همیشه آن را به‌شکل `Math.ceil()` به کار ببرید؛ `Math` سازنده نیست و از آن نمونه ساخته نمی‌شود.

## مثال‌ها

### استفاده از Math.ceil()

```js
Math.ceil(-Infinity); // -Infinity
Math.ceil(-7.004); // -7
Math.ceil(-4); // -4
Math.ceil(-0.95); // -0
Math.ceil(-0); // -0
Math.ceil(0); // 0
Math.ceil(0.95); // 1
Math.ceil(4); // 4
Math.ceil(7.004); // 8
Math.ceil(Infinity); // Infinity
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{jsxref("Math.abs()")}}
- {{jsxref("Math.floor()")}}
- {{jsxref("Math.round()")}}
- {{jsxref("Math.sign()")}}
- {{jsxref("Math.trunc()")}}
