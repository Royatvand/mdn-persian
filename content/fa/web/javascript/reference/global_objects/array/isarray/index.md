---
title: "Array.isArray()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/isArray"
---

---
title: Array.isArray()
short-title: isArray()
slug: Web/JavaScript/Reference/Global_Objects/Array/isArray
page-type: javascript-static-method
browser-compat: javascript.builtins.Array.isArray
sidebar: jsref
---

متد ایستای **`Array.isArray()`** بررسی می‌کند که مقدار ورودی یک {{jsxref("Array")}} باشد یا نه.

{{InteractiveExample("JavaScript Demo: Array.isArray()")}}

```js interactive-example
console.log(Array.isArray([1, 3, 5]));
// Expected output: true

console.log(Array.isArray("[]"));
// Expected output: false

console.log(Array.isArray(new Array(5)));
// Expected output: true

console.log(Array.isArray(new Int16Array([15, 33])));
// Expected output: false
```

## نحو

```js-nolint
Array.isArray(value)
```

### پارامترها

- `value`
  - : مقداری که باید بررسی شود.

### مقدار بازگشتی

اگر `value` یک {{jsxref("Array")}} باشد، `true` و در غیر این صورت `false` برمی‌گرداند. اگر `value` نمونه‌ای از {{jsxref("TypedArray")}} باشد، همیشه `false` برمی‌گرداند.

## توضیحات

`Array.isArray()` بررسی می‌کند که مقدار ورودی آرایه باشد. این متد نوع واقعی مقدار را با سازوکاری مشابه عملگر [`in`](/en-US/docs/Web/JavaScript/Reference/Operators/in)، بر اساس یک فیلد خصوصی که سازندهٔ {{jsxref("Array/Array", "Array()")}} مقداردهی کرده است، می‌سنجد.

این متد جایگزین مطمئن‌تری برای [`instanceof Array`](/en-US/docs/Web/JavaScript/Reference/Operators/instanceof) است؛ زیرا از نتیجه‌های مثبت و منفیِ اشتباه جلوگیری می‌کند:

- `Array.isArray()` مقادیری را که واقعاً نمونهٔ `Array` نیستند رد می‌کند، حتی اگر `Array.prototype` در زنجیرهٔ prototype آن‌ها باشد؛ اما `instanceof Array` آن‌ها را می‌پذیرد، چون زنجیرهٔ prototype را بررسی می‌کند.
- `Array.isArray()` آرایه‌هایی را که در محیط اجرایی دیگری ساخته شده‌اند نیز می‌پذیرد؛ اما `instanceof Array` برای آن‌ها `false` برمی‌گرداند، چون سازندهٔ `Array` در محیط‌های مختلف هویت متفاوتی دارد.

برای جزئیات بیشتر، مقالهٔ [«تشخیص دقیق آرایه بودن یک شیء جاوااسکریپت»](https://web.mit.edu/jwalden/www/isArray.html) را ببینید.

## مثال‌ها

### استفاده از Array.isArray()

```js
// تمام فراخوانی‌های زیر true برمی‌گردانند
Array.isArray([]);
Array.isArray([1]);
Array.isArray(new Array());
Array.isArray(new Array("a", "b", "c", "d"));
Array.isArray(new Array(3));
// نکتهٔ جالب: خود Array.prototype نیز یک آرایه است:
Array.isArray(Array.prototype);

// تمام فراخوانی‌های زیر false برمی‌گردانند
Array.isArray();
Array.isArray({});
Array.isArray(null);
Array.isArray(undefined);
Array.isArray(17);
Array.isArray("Array");
Array.isArray(true);
Array.isArray(false);
Array.isArray(new Uint8Array(32));
// این مقدار آرایه نیست، چون با استفاده از
// نحو آرایهٔ لفظی یا سازندهٔ Array ساخته نشده است
Array.isArray({ __proto__: Array.prototype });
```

### مقایسهٔ instanceof و Array.isArray()

برای بررسی آرایه بودن، `Array.isArray()` به `instanceof` ترجیح داده می‌شود، چون در محیط‌های اجرایی مختلف نیز درست کار می‌کند.

```js
const iframe = document.createElement("iframe");
document.body.appendChild(iframe);
const xArray = window.frames[window.frames.length - 1].Array;
const arr = new xArray(1, 2, 3); // [1, 2, 3]

// Correctly checking for Array
Array.isArray(arr); // true
// The prototype of arr is xArray.prototype, which is a
// different object from Array.prototype
arr instanceof Array; // false
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Polyfill of `Array.isArray` in `core-js`](https://github.com/zloirock/core-js#ecmascript-array)
- [es-shims polyfill of `Array.isArray`](https://www.npmjs.com/package/array.isarray)
- [Indexed collections](/en-US/docs/Web/JavaScript/Guide/Indexed_collections) guide
- {{jsxref("Array")}}
