---
title: "Number.isNaN()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/isNaN"
---

---
title: Number.isNaN()
short-title: isNaN()
slug: Web/JavaScript/Reference/Global_Objects/Number/isNaN
page-type: javascript-static-method
browser-compat: javascript.builtins.Number.isNaN
sidebar: jsref
---

متد ایستای **`Number.isNaN()`** بررسی می‌کند که آیا مقدار ورودی دقیقاً مقدار عددی {{jsxref("NaN")}} است یا نه. اگر ورودی از نوع `Number` نباشد، `false` برمی‌گرداند. این متد نسخه‌ای مطمئن‌تر از تابع سراسری {{jsxref("isNaN()")}} است.

{{InteractiveExample("JavaScript Demo: Number.isNaN()", "taller")}}

```js interactive-example
function typeOfNaN(x) {
  if (Number.isNaN(x)) {
    return "Number NaN";
  }
  if (isNaN(x)) {
    return "NaN";
  }
}

console.log(typeOfNaN("100F"));
// Expected output: "NaN"

console.log(typeOfNaN(NaN));
// Expected output: "Number NaN"
```

## نحو

```js-nolint
Number.isNaN(value)
```

### پارامترها

- `value`
  - : مقداری که باید از نظر برابر بودن با {{jsxref("NaN")}} بررسی شود.

### مقدار بازگشتی

اگر مقدار داده‌شده عددی با مقدار {{jsxref("NaN")}} باشد، `true` و در غیر این صورت `false` برمی‌گرداند.

## توضیحات

تابع `Number.isNaN()` راهی ساده برای بررسی مقدار `NaN` فراهم می‌کند. توجه کنید که نمی‌توان با عملگرهای [`==`](/en-US/docs/Web/JavaScript/Reference/Operators/Equality) یا [`===`](/en-US/docs/Web/JavaScript/Reference/Operators/Strict_equality) برابری با `NaN` را سنجید؛ چون اگر یکی از عملوندها `NaN` باشد، نتیجه همیشه `false` است، حتی اگر عملوند دیگر هم `NaN` باشد.

از آنجا که در میان همهٔ مقادیر جاوااسکریپت، عبارت `x !== x` فقط برای `NaN` درست است، می‌توان از آن به‌جای `Number.isNaN(x)` استفاده کرد؛ هرچند خوانایی کمتری دارد.

برخلاف تابع سراسری {{jsxref("isNaN()")}}، متد `Number.isNaN()` پارامتر را به عدد تبدیل نمی‌کند. بنابراین می‌توان مقادیری را که معمولاً به `NaN` تبدیل می‌شوند، با اطمینان به آن داد؛ این مقادیر لزوماً خودِ `NaN` نیستند. در نتیجه، فقط مقداری از نوع `Number` که واقعاً `NaN` باشد، `true` برمی‌گرداند.

## مثال‌ها

### استفاده از isNaN()

```js
Number.isNaN(NaN); // true
Number.isNaN(Number.NaN); // true
Number.isNaN(0 / 0); // true
Number.isNaN(37); // false
```

### تفاوت Number.isNaN() با isNaN() سراسری

`Number.isNaN()` پارامتر را به عدد تبدیل نمی‌کند؛ بنابراین برای مقادیر غیرعددی همیشه `false` برمی‌گرداند. نتیجهٔ همهٔ نمونه‌های زیر `false` است:

```js
Number.isNaN("NaN");
Number.isNaN(undefined);
Number.isNaN({});
Number.isNaN("blabla");
Number.isNaN(true);
Number.isNaN(null);
Number.isNaN("37");
Number.isNaN("37.37");
Number.isNaN("");
Number.isNaN(" ");
```

تابع سراسری {{jsxref("isNaN()")}} پارامتر خود را به عدد تبدیل می‌کند:

```js
isNaN("NaN"); // true
isNaN(undefined); // true
isNaN({}); // true
isNaN("blabla"); // true
isNaN(true); // false, this is coerced to 1
isNaN(null); // false, this is coerced to 0
isNaN("37"); // false, this is coerced to 37
isNaN("37.37"); // false, this is coerced to 37.37
isNaN(""); // false, this is coerced to 0
isNaN(" "); // false, this is coerced to 0
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Polyfill of `Number.isNaN` in `core-js`](https://github.com/zloirock/core-js#ecmascript-number)
- [es-shims polyfill of `Number.isNaN`](https://www.npmjs.com/package/number.isnan)
- {{jsxref("Number")}}
- {{jsxref("isNaN()")}}
