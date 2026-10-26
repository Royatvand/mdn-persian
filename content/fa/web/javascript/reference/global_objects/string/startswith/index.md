---
title: "String.prototype.startsWith()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/startsWith"
---

---
title: String.prototype.startsWith()
short-title: startsWith()
slug: Web/JavaScript/Reference/Global_Objects/String/startsWith
page-type: javascript-instance-method
browser-compat: javascript.builtins.String.startsWith
sidebar: jsref
---

متد **`startsWith()`** برای مقدارهای {{jsxref("String")}} بررسی می‌کند که آیا این رشته با نویسه‌های رشتهٔ مشخص‌شده آغاز می‌شود یا نه؛ نتیجه `true` یا `false` است.

{{InteractiveExample("JavaScript Demo: String.prototype.startsWith()")}}

```js interactive-example
const str = "Saturday night plans";

console.log(str.startsWith("Sat"));
// Expected output: true

console.log(str.startsWith("Sat", 3));
// Expected output: false
```

## نحو

```js-nolint
startsWith(searchString)
startsWith(searchString, position)
```

### پارامترها

- `searchString`
  - : نویسه‌هایی که باید در ابتدای این رشته جست‌وجو شوند. این مقدار نمی‌تواند [عبارت باقاعده](/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp#special_handling_for_regexes) باشد. مقدارهای دیگر به رشته [تبدیل](/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#string_coercion) می‌شوند؛ بنابراین حذف آرگومان یا ارسال `undefined` باعث جست‌وجوی رشتهٔ `"undefined"` می‌شود که معمولاً مطلوب نیست.
- `position` {{optional_inline}}
  - : موقعیتی که انتظار می‌رود `searchString` از آنجا آغاز شود (اندیس نخستین نویسهٔ آن). مقدار پیش‌فرض `0` است.

### مقدار بازگشتی

اگر نویسه‌های داده‌شده در ابتدای رشته وجود داشته باشند، `true` برمی‌گرداند؛ حتی اگر `searchString` خالی باشد. در غیر این صورت `false` است.

### خطاها

- {{jsxref("TypeError")}}
  - : اگر `searchString` [عبارت باقاعده](/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp#special_handling_for_regexes) باشد، خطا رخ می‌دهد.

## توضیحات

این متد مشخص می‌کند که آیا یک رشته با رشتهٔ دیگری آغاز می‌شود یا نه. این بررسی به بزرگی و کوچکی حروف حساس است.

## مثال‌ها

### استفاده از startsWith()

```js
const str = "To be, or not to be, that is the question.";

console.log(str.startsWith("To be")); // true
console.log(str.startsWith("not to be")); // false
console.log(str.startsWith("not to be", 10)); // true
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Polyfill of `String.prototype.startsWith` in `core-js`](https://github.com/zloirock/core-js#ecmascript-string-and-regexp)
- [es-shims polyfill of `String.prototype.startsWith`](https://www.npmjs.com/package/string.prototype.startswith)
- {{jsxref("String.prototype.endsWith()")}}
- {{jsxref("String.prototype.includes()")}}
- {{jsxref("String.prototype.indexOf()")}}
- {{jsxref("String.prototype.lastIndexOf()")}}
