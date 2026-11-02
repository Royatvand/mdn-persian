---
title: "String.prototype.trim()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/trim"
---

---
title: String.prototype.trim()
short-title: trim()
slug: Web/JavaScript/Reference/Global_Objects/String/trim
page-type: javascript-instance-method
browser-compat: javascript.builtins.String.trim
sidebar: jsref
---

متد **`trim()`** در مقدارهای {{jsxref("String")}} فاصله‌های خالی را از هر دو سوی رشته حذف می‌کند و رشته‌ای جدید برمی‌گرداند؛ رشتهٔ اصلی تغییر نمی‌کند.

برای حذف فاصله‌ها فقط از یک سمت، از {{jsxref("String/trimStart", "trimStart()")}} یا {{jsxref("String/trimEnd", "trimEnd()")}} استفاده کنید.

{{InteractiveExample("JavaScript Demo: String.prototype.trim()")}}

```js interactive-example
const greeting = "   Hello world!   ";

console.log(greeting);
// Expected output: "   Hello world!   ";

console.log(greeting.trim());
// Expected output: "Hello world!";
```

## نحو

```js-nolint
trim()
```

### پارامترها

این متد پارامتری نمی‌گیرد.

### مقدار بازگشتی

رشته‌ای جدید که فاصله‌های خالی ابتدا و انتهای `str` از آن حذف شده‌اند. فاصلهٔ خالی شامل نویسه‌های [فاصله](/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#white_space) و [پایان‌دهندهٔ خط](/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#line_terminators) است.

حتی اگر ابتدا و انتهای `str` هیچ فاصله‌ای نداشته باشد، باز هم رشته‌ای جدید (در عمل یک کپی از `str`) برگردانده می‌شود.

## مثال‌ها

### استفاده از trim()

مثال زیر فاصله‌های خالی را از هر دو سوی `str` حذف می‌کند.

```js
const str = "   foo  ";
console.log(str.trim()); // 'foo'
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{jsxref("String.prototype.trimStart()")}}
- {{jsxref("String.prototype.trimEnd()")}}
