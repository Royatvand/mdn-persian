---
title: "Math.random()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random"
---

---
title: Math.random()
short-title: random()
slug: Web/JavaScript/Reference/Global_Objects/Math/random
page-type: javascript-static-method
browser-compat: javascript.builtins.Math.random
sidebar: jsref
---

متد ایستای **`Math.random()`** عددی شبه‌تصادفی از نوع ممیز شناور در بازهٔ ۰ (شامل) تا ۱ (غیرشامل) برمی‌گرداند که توزیعی تقریباً یکنواخت دارد. سپس می‌توانید آن را به بازهٔ دلخواه تبدیل کنید. پیاده‌سازی، seed اولیهٔ الگوریتم تولید عدد تصادفی را انتخاب می‌کند و کاربر نمی‌تواند آن را تعیین یا بازنشانی کند.

> [!NOTE]
> `Math.random()` عددهای تصادفیِ امن از نظر رمزنگاری تولید _نمی‌کند_. برای کارهای مرتبط با امنیت از آن استفاده نکنید؛ به‌جای آن از Web Crypto API، به‌ویژه متد {{domxref("Crypto.getRandomValues()")}}، استفاده کنید.

{{InteractiveExample("JavaScript Demo: Math.random()")}}

```js interactive-example
function getRandomInt(max) {
  return Math.floor(Math.random() * max);
}

console.log(getRandomInt(3));
// Expected output: 0, 1 or 2

console.log(getRandomInt(1));
// Expected output: 0

console.log(Math.random());
// Expected output: a number from 0 to <1
```

## نحو

```js-nolint
Math.random()
```

### پارامترها

این متد پارامتری نمی‌گیرد.

### مقدار بازگشتی

عدد شبه‌تصادفی ممیز شناور در بازهٔ ۰ (شامل) تا ۱ (غیرشامل).

## مثال‌ها

از آنجا که عددهای جاوااسکریپت از نوع ممیز شناور IEEE 754 هستند و از قاعدهٔ گردکردن به نزدیک‌ترین عدد زوج پیروی می‌کنند، بازه‌های ادعاشده برای توابع زیر (به‌جز خود `Math.random()`) دقیق نیستند. معمولاً رسیدن به کران بالا ممکن نیست؛ اما اگر `Math.random()` عددی بسیار نزدیک به ۱ برگرداند، اختلاف کوچک ممکن است در بیشینهٔ درخواستی قابل نمایش نباشد و کران بالا به دست آید.

### تولید عدد تصادفی بین ۰ (شامل) و ۱ (غیرشامل)

```js
function getRandom() {
  return Math.random();
}
```

### تولید عدد تصادفی بین دو مقدار

این مثال عددی تصادفی بین دو مقدار مشخص‌شده برمی‌گرداند. مقدار خروجی بزرگ‌تر یا مساوی `min` و کوچک‌تر از `max` است.

```js
function getRandomArbitrary(min, max) {
  return Math.random() * (max - min) + min;
}
```

### تولید عدد صحیح تصادفی بین دو مقدار

این مثال عدد صحیح تصادفی‌ای بین دو مقدار مشخص‌شده برمی‌گرداند. مقدار خروجی از `min` (یا اگر `min` صحیح نباشد، از عدد صحیح بعدی) کوچک‌تر نیست و از `max` کوچک‌تر است.

```js
function getRandomInt(min, max) {
  const minCeiled = Math.ceil(min);
  const maxFloored = Math.floor(max);
  return Math.floor(Math.random() * (maxFloored - minCeiled) + minCeiled); // The maximum is exclusive and the minimum is inclusive
}
```

> [!NOTE]
> ممکن است وسوسه شوید از [`Math.round()`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/round) استفاده کنید، اما این کار توزیع عددهای تصادفی را غیریکنواخت می‌کند و ممکن است مناسب نیاز شما نباشد.

### تولید عدد صحیح تصادفی بین دو مقدار, inclusive

تابع `getRandomInt()` بالا کران پایین را شامل می‌شود اما کران بالا را نه. اگر بخواهید هر دو کران در نتیجه ممکن باشند، تابع `getRandomIntInclusive()` زیر این کار را انجام می‌دهد.

```js
function getRandomIntInclusive(min, max) {
  const minCeiled = Math.ceil(min);
  const maxFloored = Math.floor(max);
  return Math.floor(Math.random() * (maxFloored - minCeiled + 1) + minCeiled); // The maximum is inclusive and the minimum is inclusive
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("Crypto.getRandomValues()")}}
