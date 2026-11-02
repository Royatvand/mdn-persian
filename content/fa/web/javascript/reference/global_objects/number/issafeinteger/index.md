---
title: "Number.isSafeInteger()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/isSafeInteger"
---

---
title: Number.isSafeInteger()
short-title: isSafeInteger()
slug: Web/JavaScript/Reference/Global_Objects/Number/isSafeInteger
page-type: javascript-static-method
browser-compat: javascript.builtins.Number.isSafeInteger
sidebar: jsref
---

متد ایستای **`Number.isSafeInteger()`** بررسی می‌کند که آیا مقدار داده‌شده یک _عدد صحیح امن_ است یا نه.

{{InteractiveExample("JavaScript Demo: Number.isSafeInteger()")}}

```js interactive-example
function warn(x) {
  if (Number.isSafeInteger(x)) {
    return "Precision safe.";
  }
  return "Precision may be lost!";
}

console.log(warn(2 ** 53));
// Expected output: "Precision may be lost!"

console.log(warn(2 ** 53 - 1));
// Expected output: "Precision safe."
```

## نحو

```js-nolint
Number.isSafeInteger(testValue)
```

### پارامترها

- `testValue`
  - : مقداری که امن‌بودن عدد صحیح آن بررسی می‌شود.

### مقدار بازگشتی

اگر مقدار داده‌شده عدد صحیح امن باشد، `true` و در غیر این صورت `false` برمی‌گرداند.

## توضیحات

اعداد صحیح امن، تمام عددهای صحیح از ‎-(2<sup>53</sup> - 1) تا 2<sup>53</sup> - 1 (با احتساب دو کران، یعنی ±9,007,199,254,740,991) را شامل می‌شوند. عدد صحیح امن عددی است که:

- بتوان آن را دقیقاً به‌صورت عدد ممیز شناور با دقت دوبرابر IEEE-754 نمایش داد؛ و
- نمایش IEEE-754 آن حاصل گردکردن عدد صحیح دیگری برای جا شدن در قالب IEEE-754 نباشد.

برای مثال، 2<sup>53</sup> - 1 عدد صحیح امنی است: دقیق نمایش داده می‌شود و هیچ عدد صحیح دیگری در حالت‌های گردکردن IEEE-754 به آن گرد نمی‌شود. در مقابل، 2<sup>53</sup> عدد صحیح امنی _نیست_: خودش دقیق نمایش داده می‌شود، اما 2<sup>53</sup> + 1 قابل نمایش مستقیم نیست و در روش‌های گردکردن به نزدیک‌ترین و به سمت صفر، به 2<sup>53</sup> گرد می‌شود.

برای پردازش دقیق مقادیری بزرگ‌تر یا کوچک‌تر از حدود ۹ کوادریلیون، به [کتابخانهٔ محاسبات با دقت دلخواه](https://en.wikipedia.org/wiki/Arbitrary-precision_arithmetic) نیاز دارید. برای اطلاعات بیشتر دربارهٔ نمایش ممیز شناور، مقالهٔ [آنچه هر برنامه‌نویس باید دربارهٔ محاسبات ممیز شناور بداند](https://floating-point-gui.de/) را ببینید.

برای عددهای صحیح بزرگ‌تر، استفاده از نوع {{jsxref("BigInt")}} را در نظر بگیرید.

## مثال‌ها

### استفاده از isSafeInteger()

```js
Number.isSafeInteger(3); // true
Number.isSafeInteger(2 ** 53); // false
Number.isSafeInteger(2 ** 53 - 1); // true
Number.isSafeInteger(NaN); // false
Number.isSafeInteger(Infinity); // false
Number.isSafeInteger("3"); // false
Number.isSafeInteger(3.1); // false
Number.isSafeInteger(3.0); // true
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Polyfill of `Number.isSafeInteger` in `core-js`](https://github.com/zloirock/core-js#ecmascript-number)
- [es-shims polyfill of `Number.isSafeInteger`](https://www.npmjs.com/package/number.issafeinteger)
- {{jsxref("Number")}}
- {{jsxref("Number.MIN_SAFE_INTEGER")}}
- {{jsxref("Number.MAX_SAFE_INTEGER")}}
- {{jsxref("BigInt")}}
