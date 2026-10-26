---
title: "Number.isInteger()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/isInteger"
---

---
title: Number.isInteger()
short-title: isInteger()
slug: Web/JavaScript/Reference/Global_Objects/Number/isInteger
page-type: javascript-static-method
browser-compat: javascript.builtins.Number.isInteger
sidebar: jsref
---

متد ایستای **`Number.isInteger()`** بررسی می‌کند که مقدار ورودی عدد صحیح است یا نه.

{{InteractiveExample("JavaScript Demo: Number.isInteger()")}}

```js interactive-example
function fits(x, y) {
  if (Number.isInteger(y / x)) {
    return "Fits!";
  }
  return "Does NOT fit!";
}

console.log(fits(5, 10));
// Expected output: "Fits!"

console.log(fits(5, 11));
// Expected output: "Does NOT fit!"
```

## نحو

```js-nolint
Number.isInteger(value)
```

### پارامترها

- `value`
  - : مقداری که صحیح بودن آن بررسی می‌شود.

### مقدار بازگشتی

اگر مقدار داده‌شده عدد صحیح باشد `true` و در غیر این صورت `false` برمی‌گرداند.

## توضیحات

اگر مقدار موردنظر عدد صحیح باشد، `true` و در غیر این صورت `false` برگردانده می‌شود. برای {{jsxref("NaN")}} یا {{jsxref("Infinity")}} نتیجه `false` است. این متد برای اعداد اعشاری‌ای که می‌توان آن‌ها را به‌صورت عدد صحیح نمایش داد نیز `true` برمی‌گرداند. اگر مقدار عدد نباشد، نتیجه همیشه `false` است.

توجه کنید که برخی مقادیر عددی با وجود ظاهر اعشاری، به‌دلیل محدودیت دقت در نمایش اعداد ممیز شناور ECMAScript (IEEE-754) در واقع عدد صحیح محسوب می‌شوند. برای مثال، تفاوت `5.0000000000000001` با `5` فقط `1e-16` است که برای نمایش دقیق بسیار کوچک است. (برای مقایسه، [`Number.EPSILON`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/EPSILON) فاصلهٔ ۱ تا عدد ممیز شناور قابل نمایش بعدی را نگه می‌دارد که حدود `2.22e-16` است.) بنابراین `5.0000000000000001` مانند `5` نمایش داده می‌شود و `Number.isInteger(5.0000000000000001)` مقدار `true` می‌دهد.

به همین ترتیب، عددهای نزدیک به بزرگی [`Number.MAX_SAFE_INTEGER`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/MAX_SAFE_INTEGER) ممکن است دقت خود را از دست بدهند و باعث شوند `Number.isInteger` حتی برای مقداری که در اصل صحیح نیست `true` برگرداند. (حد دقیق به تعداد بیت‌های لازم برای نمایش عدد بستگی دارد؛ برای نمونه، `Number.isInteger(4500000000000000.1)` برابر `true` است، اما `Number.isInteger(4500000000000000.5)` برابر `false` است.)

## مثال‌ها

### استفاده از isInteger

```js
Number.isInteger(0); // true
Number.isInteger(1); // true
Number.isInteger(-100000); // true
Number.isInteger(99999999999999999999999); // true

Number.isInteger(0.1); // false
Number.isInteger(Math.PI); // false

Number.isInteger(NaN); // false
Number.isInteger(Infinity); // false
Number.isInteger(-Infinity); // false
Number.isInteger("10"); // false
Number.isInteger(true); // false
Number.isInteger(false); // false
Number.isInteger([1]); // false

Number.isInteger(5.0); // true
Number.isInteger(5.000000000000001); // false
Number.isInteger(5.0000000000000001); // true, because of loss of precision
Number.isInteger(4500000000000000.1); // true, because of loss of precision
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Polyfill of `Number.isInteger` in `core-js`](https://github.com/zloirock/core-js#ecmascript-number)
- [es-shims polyfill of `Number.isInteger`](https://www.npmjs.com/package/number.isinteger)
- {{jsxref("Number")}}
