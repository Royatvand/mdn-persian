---
title: "String.prototype.endsWith()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/endsWith"
---

---
title: String.prototype.endsWith()
short-title: endsWith()
slug: Web/JavaScript/Reference/Global_Objects/String/endsWith
page-type: javascript-instance-method
browser-compat: javascript.builtins.String.endsWith
sidebar: jsref
---

متد **`endsWith()`** برای مقدارهای {{jsxref("String")}} بررسی می‌کند که آیا رشته با نویسه‌های مشخص‌شده پایان می‌یابد یا نه؛ نتیجه `true` یا `false` است.

{{InteractiveExample("JavaScript Demo: String.prototype.endsWith()")}}

```js interactive-example
const str1 = "Cats are the best!";

console.log(str1.endsWith("best!"));
// Expected output: true

console.log(str1.endsWith("best", 17));
// Expected output: true

const str2 = "Is this a question?";

console.log(str2.endsWith("question"));
// Expected output: false
```

## نحو

```js-nolint
endsWith(searchString)
endsWith(searchString, endPosition)
```

### پارامترها

- `searchString`
  - : نویسه‌هایی که باید در انتهای `str` جست‌وجو شوند. این مقدار نمی‌تواند [عبارت باقاعده](/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp#special_handling_for_regexes) باشد. مقدارهای دیگر به رشته [تبدیل](/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#string_coercion) می‌شوند؛ بنابراین حذف آرگومان یا ارسال `undefined` باعث جست‌وجوی رشتهٔ `"undefined"` می‌شود که معمولاً مطلوب نیست.
- `endPosition` {{optional_inline}}
  - : موقعیت پایانی‌ای که انتظار می‌رود `searchString` تا آن نقطه پیدا شود (اندیس آخرین نویسهٔ رشته به‌علاوهٔ ۱). مقدار پیش‌فرض `str.length` است.

### مقدار بازگشتی

اگر نویسه‌های داده‌شده در انتهای رشته وجود داشته باشند، `true` برمی‌گرداند؛ حتی اگر `searchString` خالی باشد. در غیر این صورت `false` است.

### خطاها

- {{jsxref("TypeError")}}
  - : اگر `searchString` [عبارت باقاعده](/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp#special_handling_for_regexes) باشد، خطا رخ می‌دهد.

## توضیحات

این متد مشخص می‌کند که آیا یک رشته با رشتهٔ دیگری پایان می‌یابد یا نه. این بررسی به بزرگی و کوچکی حروف حساس است.

## مثال‌ها

### استفاده از endsWith()

```js
const str = "To be, or not to be, that is the question.";

console.log(str.endsWith("question.")); // true
console.log(str.endsWith("to be")); // false
console.log(str.endsWith("to be", 19)); // true
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Polyfill of `String.prototype.endsWith` in `core-js`](https://github.com/zloirock/core-js#ecmascript-string-and-regexp)
- [es-shims polyfill of `String.prototype.endsWith`](https://www.npmjs.com/package/string.prototype.endswith)
- {{jsxref("String.prototype.startsWith()")}}
- {{jsxref("String.prototype.includes()")}}
- {{jsxref("String.prototype.indexOf()")}}
- {{jsxref("String.prototype.lastIndexOf()")}}
