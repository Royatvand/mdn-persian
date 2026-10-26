---
title: "String.prototype.charAt()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/charAt"
---

---
title: String.prototype.charAt()
short-title: charAt()
slug: Web/JavaScript/Reference/Global_Objects/String/charAt
page-type: javascript-instance-method
browser-compat: javascript.builtins.String.charAt
sidebar: jsref
---

متد **`charAt()`** در مقدارهای {{jsxref("String")}} رشته‌ای جدید شامل یک واحد کد UTF-16 در اندیس داده‌شده برمی‌گرداند.

`charAt()` همیشه رشته را به‌صورت دنباله‌ای از [واحدهای کد UTF-16](/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#utf-16_characters_unicode_code_points_and_grapheme_clusters) اندیس‌گذاری می‌کند؛ بنابراین ممکن است surrogate منفرد برگرداند. برای دریافت کدپوینت کامل یونیکد در اندیس مشخص‌شده، از {{jsxref("String.prototype.codePointAt()")}} و {{jsxref("String.fromCodePoint()")}} استفاده کنید.

{{InteractiveExample("JavaScript Demo: String.prototype.charAt()", "shorter")}}

```js interactive-example
const sentence = "The quick brown fox jumps over the lazy dog.";

const index = 4;

console.log(`The character at index ${index} is ${sentence.charAt(index)}`);
// Expected output: "The character at index 4 is q"
```

## نحو

```js-nolint
charAt(index)
```

### پارامترها

- `index`
  - : اندیس صفرمبنای نویسه‌ای که باید برگردانده شود. این مقدار [به عدد صحیح تبدیل می‌شود](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number#integer_conversion)؛ `undefined` به ۰ تبدیل می‌شود.

### مقدار بازگشتی

رشته‌ای که نویسهٔ واقع در `index` مشخص‌شده را نمایش می‌دهد (دقیقاً یک واحد کد UTF-16). اگر `index` خارج از بازهٔ `0` تا `str.length - 1` باشد، `charAt()` رشته‌ای خالی برمی‌گرداند.

## توضیحات

نویسه‌های رشته از چپ به راست اندیس‌گذاری می‌شوند. اندیس نخستین نویسه `0` و اندیس آخرین نویسهٔ رشته‌ای به نام `str` برابر `str.length - 1` است.

کدپوینت‌های یونیکد از `0` تا `1114111` (`0x10FFFF`) هستند. `charAt()` همیشه نویسه‌ای با مقدار کمتر از `65536` برمی‌گرداند؛ زیرا کدپوینت‌های بزرگ‌تر با _یک جفت_ شبه‌نویسهٔ surrogate شانزده‌بیتی نمایش داده می‌شوند. بنابراین برای دریافت نویسهٔ کامل با مقدار بیشتر از `65535` باید هم `charAt(i)` و هم `charAt(i + 1)` را بگیرید، یا به‌جای آن از {{jsxref("String/codePointAt", "codePointAt(i)")}} و {{jsxref("String.fromCodePoint()")}} استفاده کنید. برای اطلاعات بیشتر، [نویسه‌های UTF-16، کدپوینت‌های یونیکد و خوشه‌های گرافیمی](/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#utf-16_characters_unicode_code_points_and_grapheme_clusters) را ببینید.

`charAt()` بسیار شبیه استفاده از [نشانه‌گذاری براکتی](/en-US/docs/Web/JavaScript/Reference/Operators/Property_accessors#bracket_notation) برای دسترسی به نویسه‌ای در اندیس مشخص است. تفاوت‌های اصلی عبارت‌اند از:

- `charAt()` تلاش می‌کند `index` را به عدد صحیح تبدیل کند؛ اما نشانه‌گذاری براکتی این کار را نمی‌کند و `index` را مستقیماً به‌عنوان نام ویژگی به کار می‌برد.
- اگر `index` خارج از محدوده باشد، `charAt()` رشتهٔ خالی و نشانه‌گذاری براکتی `undefined` برمی‌گرداند.

## مثال‌ها

### استفاده از charAt()

مثال زیر نویسه‌های موقعیت‌های مختلف رشتهٔ `"Brave new world"` را نمایش می‌دهد:

```js
const anyString = "Brave new world";
console.log(`The character at index 0   is '${anyString.charAt()}'`);
// No index was provided, used 0 as default

console.log(`The character at index 0   is '${anyString.charAt(0)}'`);
console.log(`The character at index 1   is '${anyString.charAt(1)}'`);
console.log(`The character at index 2   is '${anyString.charAt(2)}'`);
console.log(`The character at index 3   is '${anyString.charAt(3)}'`);
console.log(`The character at index 4   is '${anyString.charAt(4)}'`);
console.log(`The character at index 999 is '${anyString.charAt(999)}'`);
```

این خط‌ها خروجی زیر را نمایش می‌دهند:

```plain
The character at index 0   is 'B'

The character at index 0   is 'B'
The character at index 1   is 'r'
The character at index 2   is 'a'
The character at index 3   is 'v'
The character at index 4   is 'e'
The character at index 999 is ''
```

`charAt()` may return lone surrogates, which are not valid Unicode characters.

```js
const str = "𠮷𠮾";
console.log(str.charAt(0)); // "\ud842", which is not a valid Unicode character
console.log(str.charAt(1)); // "\udfb7", which is not a valid Unicode character
```

برای دریافت کدپوینت کامل یونیکد در اندیس داده‌شده، از روشی استفاده کنید که بر اساس کدپوینت‌های یونیکد جدا می‌کند؛ مانند {{jsxref("String.prototype.codePointAt()")}} یا [گسترش رشته](/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/Symbol.iterator) به آرایه‌ای از کدپوینت‌های یونیکد.

```js
const str = "𠮷𠮾";
console.log(String.fromCodePoint(str.codePointAt(0))); // "𠮷"
console.log([...str][0]); // "𠮷"
```

> [!NOTE]
> از بازپیاده‌سازی راه‌حل‌های بالا با `charAt()` خودداری کنید. تشخیص surrogateهای منفرد و جفت‌کردن آن‌ها پیچیده است و APIهای داخلی ممکن است کارآمدتر باشند، زیرا مستقیماً از نمایش داخلی رشته استفاده می‌کنند. در صورت نیاز برای APIهای ذکرشده polyfill نصب کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{jsxref("String.prototype.indexOf()")}}
- {{jsxref("String.prototype.lastIndexOf()")}}
- {{jsxref("String.prototype.charCodeAt()")}}
- {{jsxref("String.prototype.codePointAt()")}}
- {{jsxref("String.prototype.split()")}}
- {{jsxref("String.fromCodePoint()")}}
- [JavaScript has a Unicode problem](https://mathiasbynens.be/notes/javascript-unicode) by Mathias Bynens (2013)
