---
title: "Math.max()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/max"
---

---
title: Math.max()
short-title: max()
slug: Web/JavaScript/Reference/Global_Objects/Math/max
page-type: javascript-static-method
browser-compat: javascript.builtins.Math.max
sidebar: jsref
---

متد ایستای **`Math.max()`** بزرگ‌ترین عدد را از میان ورودی‌ها برمی‌گرداند. اگر هیچ ورودی‌ای داده نشود، مقدار ‎-{{jsxref("Infinity")}} را برمی‌گرداند.

{{InteractiveExample("JavaScript Demo: Math.max()")}}

```js interactive-example
console.log(Math.max(1, 3, 2));
// Expected output: 3

console.log(Math.max(-1, -3, -2));
// Expected output: -1

const array = [1, 3, 2];

console.log(Math.max(...array));
// Expected output: 3
```

## نحو

```js-nolint
Math.max()
Math.max(value1)
Math.max(value1, value2)
Math.max(value1, value2, /* …, */ valueN)
```

### پارامترها

- `value1`, …, `valueN`
  - : صفر یا چند عدد که بزرگ‌ترین مقدار از میان آن‌ها انتخاب و برگردانده می‌شود.

### مقدار بازگشتی

بزرگ‌ترین عدد ورودی. اگر هر یک از ورودی‌ها `NaN` باشد یا به `NaN` تبدیل شود، نتیجه {{jsxref("NaN")}} است. اگر ورودی‌ای وجود نداشته باشد، ‎-{{jsxref("Infinity")}} برگردانده می‌شود.

## توضیحات

از آنجا که `max()` متدی ایستا از `Math` است، همیشه آن را به‌شکل `Math.max()` به کار می‌برید؛ نمی‌توانید از آن به‌عنوان متد یک شیء ساخته‌شده از `Math` استفاده کنید، چون `Math` سازنده نیست.

مقدار [`Math.max.length`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/length) برابر ۲ است؛ این موضوع به‌طور ضمنی نشان می‌دهد که متد برای دریافت دست‌کم دو پارامتر طراحی شده است.

## مثال‌ها

### استفاده از Math.max()

```js
Math.max(10, 20); // 20
Math.max(-10, -20); // -10
Math.max(-10, 20); // 20
```

### پیدا کردن بزرگ‌ترین عضو آرایه

{{jsxref("Array.prototype.reduce()")}} می‌توان برای پیدا کردن بزرگ‌ترین عضو یک آرایهٔ عددی، مقدارها را با هم مقایسه کرد:

```js
const arr = [1, 2, 3];
const max = arr.reduce((a, b) => Math.max(a, b), -Infinity);
```

تابع زیر با استفاده از {{jsxref("Function.prototype.apply()")}} بیشینهٔ یک آرایه را به دست می‌آورد. فراخوانی `getMaxOfArray([1, 2, 3])` معادل `Math.max(1, 2, 3)` است؛ اما می‌توانید این تابع را برای آرایه‌هایی که در زمان اجرا ساخته می‌شوند نیز به کار ببرید. این روش فقط برای آرایه‌های نسبتاً کوچک مناسب است.

```js
function getMaxOfArray(numArray) {
  return Math.max.apply(null, numArray);
}
```

[نحو گسترش](/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax) راه کوتاه‌تری برای نوشتن راه‌حل `apply` و یافتن بیشینهٔ آرایه است:

```js
const arr = [1, 2, 3];
const max = Math.max(...arr);
```

بااین‌حال، اگر آرایه عناصر بسیار زیادی داشته باشد، هم گسترش (`...`) و هم `apply` ممکن است خطا بدهند یا نتیجهٔ نادرستی تولید کنند؛ زیرا عناصر آرایه را به‌عنوان پارامترهای تابع ارسال می‌کنند. برای جزئیات بیشتر، بخش [استفاده از apply و توابع داخلی](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/apply#using_apply_and_built-in_functions) را ببینید. راه‌حل مبتنی بر `reduce` این مشکل را ندارد.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{jsxref("Math.min()")}}
