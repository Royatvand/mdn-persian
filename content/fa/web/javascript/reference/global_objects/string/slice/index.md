---
title: "String.prototype.slice()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/slice"
---

---
title: String.prototype.slice()
short-title: slice()
slug: Web/JavaScript/Reference/Global_Objects/String/slice
page-type: javascript-instance-method
browser-compat: javascript.builtins.String.slice
sidebar: jsref
---

متد **`slice()`** از مقدارهای {{jsxref("String")}} بخشی از رشته را استخراج می‌کند و آن را به‌صورت رشته‌ای جدید برمی‌گرداند، بدون اینکه رشتهٔ اصلی تغییر کند.

{{InteractiveExample("JavaScript Demo: String.prototype.slice()", "taller")}}

```js interactive-example
const str = "The quick brown fox jumps over the lazy dog.";

console.log(str.slice(31));
// Expected output: "the lazy dog."

console.log(str.slice(4, 19));
// Expected output: "quick brown fox"

console.log(str.slice(-4));
// Expected output: "dog."

console.log(str.slice(-9, -5));
// Expected output: "lazy"
```

## نحو

```js-nolint
slice(indexStart)
slice(indexStart, indexEnd)
```

### پارامترها

- `indexStart`
  - : اندیس نخستین نویسه‌ای که باید در زیررشتهٔ خروجی قرار بگیرد.
- `indexEnd` {{optional_inline}}
  - : اندیس نخستین نویسه‌ای که نباید در زیررشتهٔ خروجی قرار بگیرد.

### مقدار بازگشتی

رشته‌ای جدید که بخش استخراج‌شده از رشته را در بر دارد.

## توضیحات

`slice()` بخشی از متن یک رشته را استخراج می‌کند و رشته‌ای جدید برمی‌گرداند.

`slice()` تا قبل از `indexEnd` را استخراج می‌کند و خود آن اندیس را شامل نمی‌شود. برای مثال، `str.slice(4, 8)` نویسه‌های پنجم تا هشتم را برمی‌گرداند (اندیس‌های `4`، `5`، `6` و `7`):

```plain
              indexStart        indexEnd
                  ↓               ↓
| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
| T | h | e |   | m | i | r | r | o | r |

                  m   i   r   r
                 _______________
                      ↑
                    Result
```

- اگر `indexStart >= str.length` باشد، رشته‌ای خالی برگردانده می‌شود.
- اگر `indexStart < 0` باشد، اندیس از انتهای رشته محاسبه می‌شود. به‌طور دقیق‌تر، زیررشته از `max(indexStart + str.length, 0)` آغاز می‌شود.
- اگر `indexStart` حذف شود، مقدارش `undefined` باشد یا نتوان آن را [به عدد تبدیل کرد](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number#number_coercion)، مقدار `0` در نظر گرفته می‌شود.
- اگر `indexEnd` حذف شود، `undefined` باشد یا `indexEnd >= str.length` باشد، `slice()` تا انتهای رشته را استخراج می‌کند.
- اگر `indexEnd < 0` باشد، اندیس از انتهای رشته محاسبه می‌شود. در این حالت، زیررشته در `max(indexEnd + str.length, 0)` پایان می‌یابد.
- اگر پس از نرمال‌سازی مقادیر منفی، `indexEnd <= indexStart` باشد (یعنی `indexEnd` به نویسه‌ای پیش از `indexStart` اشاره کند)، رشته‌ای خالی برگردانده می‌شود.

## مثال‌ها

### ساخت رشته‌ای جدید با slice()

مثال زیر با `slice()` یک رشتهٔ جدید می‌سازد.

```js
const str1 = "The morning is upon us."; // The length of str1 is 23.
const str2 = str1.slice(1, 8);
const str3 = str1.slice(4, -2);
const str4 = str1.slice(12);
const str5 = str1.slice(30);
console.log(str2); // he morn
console.log(str3); // morning is upon u
console.log(str4); // is upon us.
console.log(str5); // ""
```

### استفاده از slice() با اندیس‌های منفی

مثال زیر `slice()` را با اندیس‌های منفی به کار می‌برد.

```js
const str = "The morning is upon us.";
str.slice(-3); // 'us.'
str.slice(-3, -1); // 'us'
str.slice(0, -1); // 'The morning is upon us'
str.slice(4, -1); // 'morning is upon us'
```

در این مثال، برای یافتن اندیس آغاز از انتهای رشته ۱۱ خانه به عقب می‌رویم و برای یافتن اندیس پایان از ابتدای رشته ۱۶ خانه جلو می‌رویم.

```js
console.log(str.slice(-11, 16)); // "is u"
```

اینجا برای یافتن اندیس آغاز از ابتدای رشته ۱۱ خانه جلو می‌رویم و برای یافتن اندیس پایان از انتهای رشته ۷ خانه به عقب می‌رویم.

```js
console.log(str.slice(11, -7)); // " is u"
```

در این آرگومان‌ها، برای یافتن اندیس آغاز ۵ خانه و برای اندیس پایان ۱ خانه از انتهای رشته به عقب می‌رویم.

```js
console.log(str.slice(-5, -1)); // "n us"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{jsxref("String.prototype.substr()")}}
- {{jsxref("String.prototype.substring()")}}
- {{jsxref("Array.prototype.slice()")}}
