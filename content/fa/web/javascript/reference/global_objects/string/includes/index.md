---
title: "String.prototype.includes()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/includes"
---

---
title: String.prototype.includes()
short-title: includes()
slug: Web/JavaScript/Reference/Global_Objects/String/includes
page-type: javascript-instance-method
browser-compat: javascript.builtins.String.includes
sidebar: jsref
---

متد **`includes()`** برای مقدارهای {{jsxref("String")}} جست‌وجویی حساس به بزرگی و کوچکی حروف انجام می‌دهد تا مشخص کند رشته‌ای دیگر در این رشته وجود دارد یا نه؛ نتیجه `true` یا `false` است.

{{InteractiveExample("JavaScript Demo: String.prototype.includes()", "shorter")}}

```js interactive-example
const sentence = "The quick brown fox jumps over the lazy dog.";

const word = "fox";

console.log(
  `The word "${word}" ${
    sentence.includes(word) ? "is" : "is not"
  } in the sentence`,
);
// Expected output: "The word "fox" is in the sentence"
```

## نحو

```js-nolint
includes(searchString)
includes(searchString, position)
```

### پارامترها

- `searchString`
  - : رشته‌ای که باید درون `str` جست‌وجو شود. این مقدار نمی‌تواند [عبارت باقاعده](/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp#special_handling_for_regexes) باشد. مقدارهای دیگر به رشته [تبدیل](/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#string_coercion) می‌شوند؛ بنابراین اگر این آرگومان را حذف کنید یا `undefined` بدهید، متد به‌دنبال رشتهٔ `"undefined"` می‌گردد که معمولاً مطلوب نیست.
- `position` {{optional_inline}}
  - : موقعیتی در رشته که جست‌وجوی `searchString` از آن آغاز می‌شود. مقدار پیش‌فرض `0` است.

### مقدار بازگشتی

اگر رشتهٔ جست‌وجوشده در هر نقطه‌ای از رشتهٔ داده‌شده پیدا شود، `true` برمی‌گرداند؛ حتی اگر `searchString` رشته‌ای خالی باشد. در غیر این صورت `false` است.

### خطاها

- {{jsxref("TypeError")}}
  - : اگر `searchString` [عبارت باقاعده](/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp#special_handling_for_regexes) باشد، خطا رخ می‌دهد.

## توضیحات

این متد مشخص می‌کند که آیا یک رشته، رشتهٔ دیگری را در خود دارد یا نه.

### حساسیت به بزرگی و کوچکی حروف

متد `includes()` به بزرگی و کوچکی حروف حساس است. برای مثال، عبارت زیر `false` برمی‌گرداند:

```js
"Blue Whale".includes("blue"); // returns false
```

برای دور زدن این محدودیت می‌توانید هم رشتهٔ اصلی و هم رشتهٔ جست‌وجو را به حروف کوچک تبدیل کنید:

```js
"Blue Whale".toLowerCase().includes("blue"); // returns true
```

## مثال‌ها

### استفاده از includes()

```js
const str = "To be, or not to be, that is the question.";

console.log(str.includes("To be")); // true
console.log(str.includes("question")); // true
console.log(str.includes("nonexistent")); // false
console.log(str.includes("To be", 1)); // false
console.log(str.includes("TO BE")); // false
console.log(str.includes("")); // true
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Polyfill of `String.prototype.includes` in `core-js`](https://github.com/zloirock/core-js#ecmascript-string-and-regexp)
- [es-shims polyfill of `String.prototype.includes`](https://www.npmjs.com/package/string.prototype.includes)
- {{jsxref("Array.prototype.includes()")}}
- {{jsxref("TypedArray.prototype.includes()")}}
- {{jsxref("String.prototype.indexOf()")}}
- {{jsxref("String.prototype.lastIndexOf()")}}
- {{jsxref("String.prototype.startsWith()")}}
- {{jsxref("String.prototype.endsWith()")}}
