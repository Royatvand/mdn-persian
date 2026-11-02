---
title: "Math.round()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/round"
---

---
title: Math.round()
short-title: round()
slug: Web/JavaScript/Reference/Global_Objects/Math/round
page-type: javascript-static-method
browser-compat: javascript.builtins.Math.round
sidebar: jsref
---

متد ایستای **`Math.round()`** مقدار عدد را پس از گرد کردن به نزدیک‌ترین عدد صحیح برمی‌گرداند.

{{InteractiveExample("JavaScript Demo: Math.round()")}}

```js interactive-example
console.log(Math.round(0.9));
// Expected output: 1

console.log(Math.round(5.95), Math.round(5.5), Math.round(5.05));
// Expected output: 6 6 5

console.log(Math.round(-5.05), Math.round(-5.5), Math.round(-5.95));
// Expected output: -5 -5 -6
```

## نحو

```js-nolint
Math.round(x)
```

### پارامترها

- `x`
  - : یک عدد.

### مقدار بازگشتی

مقدار `x` که به نزدیک‌ترین عدد صحیح گرد شده است.

## توضیحات

اگر بخش اعشاری آرگومان بیشتر از ۰٫۵ باشد، عدد به سمت عدد صحیحی با قدرمطلق بزرگ‌تر گرد می‌شود. اگر کمتر از ۰٫۵ باشد، به سمت عدد صحیحی با قدرمطلق کوچک‌تر گرد می‌شود. اگر بخش اعشاری دقیقاً ۰٫۵ باشد، عدد به سمت عدد صحیح بعدی در جهت مثبت بی‌نهایت گرد می‌شود.

> [!NOTE]
> این رفتار با تابع `round()` در بسیاری از زبان‌ها متفاوت است؛ آن توابع معمولاً نیم‌واحدها را _دور از صفر_ گرد می‌کنند و در نتیجه برای اعداد منفی با بخش اعشاری دقیقاً ۰٫۵ نتیجهٔ متفاوتی می‌دهند.

`Math.round(x)` دقیقاً با [`Math.floor(x + 0.5)`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/floor) یکسان نیست. وقتی `x` برابر `-0` باشد یا `-0.5 ≤ x < 0`، تابع `Math.round(x)` مقدار `-0` و تابع `Math.floor(x + 0.5)` مقدار `0` برمی‌گرداند. با صرف‌نظر از این تفاوت و خطاهای احتمالی دقت، این دو عبارت معمولاً معادل‌اند.

چون `round()` متدی ایستا از `Math` است، همیشه آن را به‌شکل `Math.round()` به کار ببرید؛ `Math` سازنده ندارد.

## مثال‌ها

### استفاده از round

```js
Math.round(-Infinity); // -Infinity
Math.round(-20.51); // -21
Math.round(-20.5); // -20
Math.round(-0.1); // -0
Math.round(0); // 0
Math.round(20.49); // 20
Math.round(20.5); // 21
Math.round(42); // 42
Math.round(Infinity); // Infinity
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{jsxref("Number.prototype.toPrecision()")}}
- {{jsxref("Number.prototype.toFixed()")}}
- {{jsxref("Math.abs()")}}
- {{jsxref("Math.ceil()")}}
- {{jsxref("Math.floor()")}}
- {{jsxref("Math.sign()")}}
- {{jsxref("Math.trunc()")}}
