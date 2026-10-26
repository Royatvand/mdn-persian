---
title: "Math.abs()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/abs"
---

---
title: Math.abs()
short-title: abs()
slug: Web/JavaScript/Reference/Global_Objects/Math/abs
page-type: javascript-static-method
browser-compat: javascript.builtins.Math.abs
sidebar: jsref
---

متد ایستای **`Math.abs()`** قدرمطلق یک عدد را برمی‌گرداند.

{{InteractiveExample("JavaScript Demo: Math.abs()")}}

```js interactive-example
function difference(a, b) {
  return Math.abs(a - b);
}

console.log(difference(3, 5));
// Expected output: 2

console.log(difference(5, 3));
// Expected output: 2

console.log(difference(1.23456, 7.89012));
// Expected output: 6.6555599999999995
```

## نحو

```js-nolint
Math.abs(x)
```

### پارامترها

- `x`
  - : یک عدد.

### مقدار بازگشتی

قدر مطلق `x`. اگر `x` منفی یا `-0` باشد، عدد مخالف آن یعنی `-x` (که نامنفی است) برگردانده می‌شود؛ در غیر این صورت خود `x` برگردانده می‌شود. بنابراین نتیجه همیشه عددی نامنفی یا `0` است.

## توضیحات

چون `abs()` متدی ایستا از `Math` است، همیشه آن را به‌شکل `Math.abs()` به کار ببرید؛ `Math` سازنده نیست و از آن نمونه ساخته نمی‌شود.

## مثال‌ها

### استفاده از Math.abs()

```js
Math.abs(-Infinity); // Infinity
Math.abs(-1); // 1
Math.abs(-0); // 0
Math.abs(0); // 0
Math.abs(1); // 1
Math.abs(Infinity); // Infinity
```

### تبدیل پارامتر

`Math.abs()` پارامتر خود را [به عدد تبدیل می‌کند](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number#number_coercion). مقدارهایی که قابل تبدیل نیستند به `NaN` تبدیل می‌شوند و در نتیجه `Math.abs()` نیز `NaN` برمی‌گرداند.

```js
Math.abs("-1"); // 1
Math.abs(-2); // 2
Math.abs(null); // 0
Math.abs(""); // 0
Math.abs([]); // 0
Math.abs([2]); // 2
Math.abs([1, 2]); // NaN
Math.abs({}); // NaN
Math.abs("string"); // NaN
Math.abs(); // NaN
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{jsxref("Math.ceil()")}}
- {{jsxref("Math.floor()")}}
- {{jsxref("Math.round()")}}
- {{jsxref("Math.sign()")}}
- {{jsxref("Math.trunc()")}}
