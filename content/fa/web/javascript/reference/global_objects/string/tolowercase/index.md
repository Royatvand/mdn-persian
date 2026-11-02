---
title: "String.prototype.toLowerCase()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/toLowerCase"
---

---
title: String.prototype.toLowerCase()
short-title: toLowerCase()
slug: Web/JavaScript/Reference/Global_Objects/String/toLowerCase
page-type: javascript-instance-method
browser-compat: javascript.builtins.String.toLowerCase
sidebar: jsref
---

متد **`toLowerCase()`** در مقدارهای {{jsxref("String")}} رشته را به حروف کوچک تبدیل کرده و برمی‌گرداند.

{{InteractiveExample("JavaScript Demo: String.prototype.toLowerCase()", "shorter")}}

```js interactive-example
const sentence = "The quick brown fox jumps over the lazy dog.";

console.log(sentence.toLowerCase());
// Expected output: "the quick brown fox jumps over the lazy dog."
```

## نحو

```js-nolint
toLowerCase()
```

### پارامترها

این متد پارامتری نمی‌گیرد.

### مقدار بازگشتی

رشته‌ای جدید که نسخهٔ حروف‌کوچک‌شدهٔ رشتهٔ فراخوانی‌کننده است.

## توضیحات

متد `toLowerCase()` مقدار رشته را به حروف کوچک تبدیل می‌کند و برمی‌گرداند. خود رشتهٔ `str` با اجرای `toLowerCase()` تغییر نمی‌کند.

## مثال‌ها

### استفاده از `toLowerCase()`

```js
console.log("ALPHABET".toLowerCase()); // 'alphabet'
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{jsxref("String.prototype.toLocaleLowerCase()")}}
- {{jsxref("String.prototype.toLocaleUpperCase()")}}
- {{jsxref("String.prototype.toUpperCase()")}}
