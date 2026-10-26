---
title: "String.prototype.toUpperCase()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/toUpperCase"
---

---
title: String.prototype.toUpperCase()
short-title: toUpperCase()
slug: Web/JavaScript/Reference/Global_Objects/String/toUpperCase
page-type: javascript-instance-method
browser-compat: javascript.builtins.String.toUpperCase
sidebar: jsref
---

متد **`toUpperCase()`** در مقدارهای {{jsxref("String")}} رشته را به حروف بزرگ تبدیل کرده و برمی‌گرداند.

{{InteractiveExample("JavaScript Demo: String.prototype.toUpperCase()", "shorter")}}

```js interactive-example
const sentence = "The quick brown fox jumps over the lazy dog.";

console.log(sentence.toUpperCase());
// Expected output: "THE QUICK BROWN FOX JUMPS OVER THE LAZY DOG."
```

## نحو

```js-nolint
toUpperCase()
```

### پارامترها

این متد پارامتری نمی‌گیرد.

### مقدار بازگشتی

رشته‌ای جدید که نسخهٔ حروف‌بزرگ‌شدهٔ رشتهٔ فراخوانی‌کننده است.

## توضیحات

متد `toUpperCase()` مقدار رشته را به حروف بزرگ تبدیل می‌کند و برمی‌گرداند. از آنجا که رشته‌ها در جاوااسکریپت تغییرناپذیرند، مقدار رشتهٔ اصلی تغییر نمی‌کند.

## مثال‌ها

### استفادهٔ پایه

```js
console.log("alphabet".toUpperCase()); // 'ALPHABET'
```

### تبدیل مقدارهای غیررشته‌ای this به رشته

اگر مقدار `this` را به مقداری غیر از رشته تنظیم کنید، این متد آن مقدار را به رشته تبدیل می‌کند:

```js
const a = String.prototype.toUpperCase.call({
  toString() {
    return "abcdef";
  },
});

const b = String.prototype.toUpperCase.call(true);

// prints out 'ABCDEF TRUE'.
console.log(a, b);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{jsxref("String.prototype.toLocaleLowerCase()")}}
- {{jsxref("String.prototype.toLocaleUpperCase()")}}
- {{jsxref("String.prototype.toLowerCase()")}}
