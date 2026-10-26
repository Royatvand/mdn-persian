---
title: "String.prototype.trimStart()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/trimStart"
---

---
title: String.prototype.trimStart()
short-title: trimStart()
slug: Web/JavaScript/Reference/Global_Objects/String/trimStart
page-type: javascript-instance-method
browser-compat: javascript.builtins.String.trimStart
sidebar: jsref
---

متد **`trimStart()`** در مقدارهای {{jsxref("String")}} فاصله‌های خالی ابتدای رشته را حذف می‌کند و رشته‌ای جدید برمی‌گرداند، بدون تغییر رشتهٔ اصلی. `trimLeft()` نام مستعار همین متد است.

{{InteractiveExample("JavaScript Demo: String.prototype.trimStart()")}}

```js interactive-example
const greeting = "   Hello world!   ";

console.log(greeting);
// Expected output: "   Hello world!   ";

console.log(greeting.trimStart());
// Expected output: "Hello world!   ";
```

## نحو

```js-nolint
trimStart()

trimLeft()
```

### پارامترها

این متد پارامتری نمی‌گیرد.

### مقدار بازگشتی

رشته‌ای جدید که فاصله‌های خالی ابتدای (سمت چپ) `str` از آن حذف شده‌اند. فاصلهٔ خالی شامل نویسه‌های [فاصله](/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#white_space) و [پایان‌دهندهٔ خط](/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#line_terminators) است.

اگر ابتدای `str` فاصلهٔ خالی نداشته باشد، باز هم رشته‌ای جدید (در عمل کپی `str`) برگردانده می‌شود.

### نام مستعار

پس از استانداردشدن {{jsxref("String/trim", "trim()")}}، موتورهای جاوااسکریپت متد غیراستاندارد `trimLeft` را نیز پیاده‌سازی کردند. برای هماهنگی با {{jsxref("String/padStart", "padStart()")}}، نام استاندارد این متد `trimStart` انتخاب شد. برای سازگاری با وب، `trimLeft` همچنان نام مستعار `trimStart` باقی مانده و هر دو به دقیقاً یک شیء تابع اشاره می‌کنند. در برخی موتورهای جاوااسکریپت، نتیجه چنین است:

```js
String.prototype.trimLeft.name === "trimStart";
```

## مثال‌ها

### استفاده از trimStart()

مثال زیر فاصله‌های خالی ابتدای `str` را حذف می‌کند، اما انتهای آن را تغییر نمی‌دهد.

```js
let str = "   foo  ";

console.log(str.length); // 8

str = str.trimStart();
console.log(str.length); // 5
console.log(str); // 'foo  '
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Polyfill of `String.prototype.trimStart` in `core-js`](https://github.com/zloirock/core-js#ecmascript-string-and-regexp)
- [es-shims polyfill of `String.prototype.trimStart`](https://www.npmjs.com/package/string.prototype.trimstart)
- {{jsxref("String.prototype.trim()")}}
- {{jsxref("String.prototype.trimEnd()")}}
