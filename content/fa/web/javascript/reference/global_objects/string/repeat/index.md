---
title: "String.prototype.repeat()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/repeat"
---

---
title: String.prototype.repeat()
short-title: repeat()
slug: Web/JavaScript/Reference/Global_Objects/String/repeat
page-type: javascript-instance-method
browser-compat: javascript.builtins.String.repeat
sidebar: jsref
---

متد **`repeat()`** در مقدارهای {{jsxref("String")}} رشته‌ای جدید می‌سازد و برمی‌گرداند که تعداد مشخصی از نسخه‌های همین رشته را به‌هم چسبانده است.

{{InteractiveExample("JavaScript Demo: String.prototype.repeat()", "shorter")}}

```js interactive-example
const mood = "Happy! ";

console.log(`I feel ${mood.repeat(3)}`);
// Expected output: "I feel Happy! Happy! Happy! "
```

## نحو

```js-nolint
repeat(count)
```

### پارامترها

- `count`
  - : عدد صحیحی بین `0` و {{jsxref("Number/POSITIVE_INFINITY", "Infinity")}} که تعداد تکرار رشته را مشخص می‌کند.

### مقدار بازگشتی

رشته‌ای جدید شامل تعداد مشخص‌شده‌ای از نسخه‌های رشتهٔ ورودی.

### خطاها

- {{jsxref("RangeError")}}
  - : اگر `count` منفی باشد یا از بیشینهٔ طول رشته فراتر رود، خطا رخ می‌دهد.

## مثال‌ها

### استفاده از repeat()

```js
"abc".repeat(-1); // RangeError
"abc".repeat(0); // ''
"abc".repeat(1); // 'abc'
"abc".repeat(2); // 'abcabc'
"abc".repeat(3.5); // 'abcabcabc' (count will be converted to integer)
"abc".repeat(1 / 0); // RangeError

({ toString: () => "abc", repeat: String.prototype.repeat }).repeat(2);
// 'abcabc' (repeat() is a generic method)
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Polyfill of `String.prototype.repeat` in `core-js`](https://github.com/zloirock/core-js#ecmascript-string-and-regexp)
- [es-shims polyfill of `String.prototype.repeat`](https://www.npmjs.com/package/string.prototype.repeat)
- {{jsxref("String.prototype.concat()")}}
