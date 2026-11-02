---
title: "String.prototype.trimEnd()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/trimEnd"
---

---
title: String.prototype.trimEnd()
short-title: trimEnd()
slug: Web/JavaScript/Reference/Global_Objects/String/trimEnd
page-type: javascript-instance-method
browser-compat: javascript.builtins.String.trimEnd
sidebar: jsref
---

متد **`trimEnd()`** در مقدارهای {{jsxref("String")}} فاصله‌های خالی انتهای رشته را حذف می‌کند و رشته‌ای جدید برمی‌گرداند، بدون تغییر رشتهٔ اصلی. `trimRight()` نام مستعار همین متد است.

{{InteractiveExample("JavaScript Demo: String.prototype.trimEnd()")}}

```js interactive-example
const greeting = "   Hello world!   ";

console.log(greeting);
// Expected output: "   Hello world!   ";

console.log(greeting.trimEnd());
// Expected output: "   Hello world!";
```

## نحو

```js-nolint
trimEnd()

trimRight()
```

### پارامترها

این متد پارامتری نمی‌گیرد.

### مقدار بازگشتی

رشته‌ای جدید که فاصله‌های خالی انتهای (سمت راست) `str` از آن حذف شده‌اند. فاصلهٔ خالی شامل نویسه‌های [فاصله](/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#white_space) و [پایان‌دهندهٔ خط](/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#line_terminators) است.

اگر انتهای `str` فاصلهٔ خالی نداشته باشد، باز هم رشته‌ای جدید (در عمل کپی `str`) برگردانده می‌شود.

### نام مستعار

پس از استانداردشدن {{jsxref("String/trim", "trim()")}}، موتورهای جاوااسکریپت متد غیراستاندارد `trimRight` را نیز پیاده‌سازی کردند. برای هماهنگی با {{jsxref("String/padEnd", "padEnd()")}}، نام استاندارد این متد `trimEnd` انتخاب شد. برای سازگاری با وب، `trimRight` همچنان نام مستعار `trimEnd` باقی مانده و هر دو به دقیقاً یک شیء تابع اشاره می‌کنند. در برخی موتورهای جاوااسکریپت، نتیجه چنین است:

```js
String.prototype.trimRight.name === "trimEnd";
```

## مثال‌ها

### استفاده از trimEnd()

مثال زیر فاصله‌های خالی انتهای `str` را حذف می‌کند، اما ابتدای آن را تغییر نمی‌دهد.

```js
let str = "   foo  ";

console.log(str.length); // 8

str = str.trimEnd();
console.log(str.length); // 6
console.log(str); // '   foo'
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Polyfill of `String.prototype.trimEnd` in `core-js`](https://github.com/zloirock/core-js#ecmascript-string-and-regexp)
- [es-shims polyfill of `String.prototype.trimEnd`](https://www.npmjs.com/package/string.prototype.trimend)
- {{jsxref("String.prototype.trim()")}}
- {{jsxref("String.prototype.trimStart()")}}
