---
title: "Array.prototype.at()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/at"
---

---
title: Array.prototype.at()
short-title: at()
slug: Web/JavaScript/Reference/Global_Objects/Array/at
page-type: javascript-instance-method
browser-compat: javascript.builtins.Array.at
sidebar: jsref
---

متد **`at()`** در نمونه‌های {{jsxref("Array")}} یک عدد صحیح می‌گیرد و عضو واقع در آن اندیس را برمی‌گرداند. اندیس می‌تواند مثبت یا منفی باشد؛ اندیس منفی از آخرین عضو آرایه به عقب می‌شمارد.

{{InteractiveExample("JavaScript Demo: Array.prototype.at()")}}

```js interactive-example
const array = [5, 12, 8, 130, 44];

let index = 2;

console.log(`An index of ${index} returns ${array.at(index)}`);
// Expected output: "An index of 2 returns 8"

index = -2;

console.log(`An index of ${index} returns ${array.at(index)}`);
// Expected output: "An index of -2 returns 130"
```

## نحو

```js-nolint
at(index)
```

### پارامترها

- `index`
  - : اندیسِ صفرمبنا برای عضو موردنظر آرایه که [به عدد صحیح تبدیل می‌شود](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number#integer_conversion). اندیس منفی از انتهای آرایه محاسبه می‌شود؛ اگر `index < 0` باشد، اندیس `index + array.length` دسترسی داده می‌شود.

### مقدار بازگشتی

عضو آرایه در اندیس داده‌شده. اگر `index < -array.length` یا `index >= array.length` باشد، بدون تلاش برای دسترسی به ویژگی متناظر، همیشه {{jsxref("undefined")}} برمی‌گرداند.

## توضیحات

وقتی `index` عدد صحیحی نامنفی باشد، متد `at()` معادل استفاده از براکت است؛ برای مثال، `array[0]` و `array.at(0)` هر دو عضو اول را برمی‌گردانند. اما برای شمردن از انتهای آرایه نمی‌توان مانند Python یا R از `array[-1]` استفاده کرد؛ زیرا مقدار داخل براکت به‌عنوان نام ویژگی رشته‌ای در نظر گرفته می‌شود و در واقع `array["-1"]` خوانده خواهد شد، نه اندیس آرایه.

روش معمول این است که با استفاده از {{jsxref("Array/length", "length")}} اندیس را محاسبه کنیم؛ مثلاً `array[array.length - 1]`. متد `at()` اندیس‌گذاری نسبی را ممکن می‌کند و این عبارت را می‌توان به `array.at(-1)` کوتاه کرد.

با ترکیب `at()` و {{jsxref("Array/with", "with()")}} می‌توانید با اندیس‌های منفی به‌ترتیب مقدار آرایه را بخوانید و تغییر دهید.

متد `at()` [عمومی](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#generic_array_methods) است؛ فقط انتظار دارد مقدار `this` ویژگی `length` و ویژگی‌هایی با کلیدهای عدد صحیح داشته باشد.

## مثال‌ها

### برگرداندن آخرین مقدار آرایه

مثال زیر تابعی می‌سازد که آخرین عضو آرایهٔ مشخص‌شده را برمی‌گرداند.

```js
// Our array with items
const cart = ["apple", "banana", "pear"];

// A function which returns the last item of a given array
function returnLast(arr) {
  return arr.at(-1);
}

// Get the last item of our array 'cart'
const item1 = returnLast(cart);
console.log(item1); // 'pear'

// Add an item to our 'cart' array
cart.push("orange");
const item2 = returnLast(cart);
console.log(item2); // 'orange'
```

### مقایسهٔ روش‌ها

این مثال روش‌های مختلف انتخاب عضو یکی مانده به آخر یک {{jsxref("Array")}} را مقایسه می‌کند. همهٔ روش‌های زیر معتبرند، اما این نمونه کوتاه‌بودن و خوانایی `at()` را نشان می‌دهد.

```js
// Our array with items
const colors = ["red", "green", "blue"];

// Using length property
const lengthWay = colors[colors.length - 2];
console.log(lengthWay); // 'green'

// Using slice() method. Note an array is returned
const sliceWay = colors.slice(-2, -1);
console.log(sliceWay[0]); // 'green'

// Using at() method
const atWay = colors.at(-2);
console.log(atWay); // 'green'
```

### فراخوانی at() روی اشیایی غیر از آرایه

متد `at()` ویژگی `length` مقدار `this` را می‌خواند و اندیس مورد دسترسی را محاسبه می‌کند.

```js
const arrayLike = {
  length: 2,
  0: "a",
  1: "b",
  2: "c", // ignored by at() since length is 2
};
console.log(Array.prototype.at.call(arrayLike, 0)); // "a"
console.log(Array.prototype.at.call(arrayLike, 2)); // undefined
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Polyfill of `Array.prototype.at` in `core-js`](https://github.com/zloirock/core-js#relative-indexing-method)
- [es-shims polyfill of `Array.prototype.at`](https://www.npmjs.com/package/array.prototype.at)
- [Indexed collections](/en-US/docs/Web/JavaScript/Guide/Indexed_collections) guide
- {{jsxref("Array")}}
- {{jsxref("Array.prototype.findIndex()")}}
- {{jsxref("Array.prototype.indexOf()")}}
- {{jsxref("Array.prototype.with()")}}
- {{jsxref("TypedArray.prototype.at()")}}
- {{jsxref("String.prototype.at()")}}
