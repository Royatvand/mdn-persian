---
title: "Math.min()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/min"
---

---
title: Math.min()
short-title: min()
slug: Web/JavaScript/Reference/Global_Objects/Math/min
page-type: javascript-static-method
browser-compat: javascript.builtins.Math.min
sidebar: jsref
---

متد ایستای **`Math.min()`** کوچک‌ترین عدد را از میان ورودی‌ها برمی‌گرداند. اگر هیچ ورودی‌ای داده نشود، مقدار {{jsxref("Infinity")}} را برمی‌گرداند.

{{InteractiveExample("JavaScript Demo: Math.min()")}}

```js interactive-example
console.log(Math.min(2, 3, 1));
// Expected output: 1

console.log(Math.min(-2, -3, -1));
// Expected output: -3

const array = [2, 3, 1];

console.log(Math.min(...array));
// Expected output: 1
```

## نحو

```js-nolint
Math.min()
Math.min(value1)
Math.min(value1, value2)
Math.min(value1, value2, /* …, */ valueN)
```

### پارامترها

- `value1`, …, `valueN`
  - : صفر یا چند عدد که کوچک‌ترین مقدار از میان آن‌ها انتخاب و برگردانده می‌شود.

### مقدار بازگشتی

کوچک‌ترین عدد ورودی. اگر هر یک از ورودی‌ها `NaN` باشد یا به `NaN` تبدیل شود، نتیجه {{jsxref("NaN")}} است. اگر ورودی‌ای وجود نداشته باشد، {{jsxref("Infinity")}} برگردانده می‌شود.

## توضیحات

از آنجا که `min()` متدی ایستا از `Math` است، همیشه آن را به‌شکل `Math.min()` به کار می‌برید؛ نمی‌توانید از آن به‌عنوان متد یک شیء ساخته‌شده از `Math` استفاده کنید، چون `Math` سازنده نیست.

مقدار [`Math.min.length`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/length) برابر ۲ است؛ این موضوع به‌طور ضمنی نشان می‌دهد که متد برای دریافت دست‌کم دو پارامتر طراحی شده است.

## مثال‌ها

### استفاده از Math.min()

این کد کوچک‌ترین مقدار `x` و `y` را پیدا می‌کند و در `z` قرار می‌دهد:

```js
const x = 10;
const y = -20;
const z = Math.min(x, y); // -20
```

### محدود کردن مقدار با Math.min()

معمولاً از `Math.min()` برای محدود کردن یک مقدار استفاده می‌شود تا همیشه کوچک‌تر یا مساوی یک حد مشخص باشد. برای نمونه، کد زیر

```js
let x = f(foo);

if (x > boundary) {
  x = boundary;
}
```

را می‌توان به شکل زیر نوشت:

```js
const x = Math.min(f(foo), boundary);
```

{{jsxref("Math.max()")}} را می‌توان به روشی مشابه برای محدود کردن مقدار از سمت دیگر به کار برد.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{jsxref("Math.max()")}}
