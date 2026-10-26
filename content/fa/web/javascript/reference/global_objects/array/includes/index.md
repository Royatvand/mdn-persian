---
title: "Array.prototype.includes()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/includes"
---

---
title: Array.prototype.includes()
short-title: includes()
slug: Web/JavaScript/Reference/Global_Objects/Array/includes
page-type: javascript-instance-method
browser-compat: javascript.builtins.Array.includes
sidebar: jsref
---

متد **`includes()`** در نمونه‌های {{jsxref("Array")}} بررسی می‌کند که آیا مقدار مشخصی در میان اعضای آرایه وجود دارد یا نه؛ نتیجه `true` یا `false` است.

{{InteractiveExample("JavaScript Demo: Array.prototype.includes()")}}

```js interactive-example
const array = [1, 2, 3];

console.log(array.includes(2));
// Expected output: true

const pets = ["cat", "dog", "bat"];

console.log(pets.includes("cat"));
// Expected output: true

console.log(pets.includes("at"));
// Expected output: false
```

## نحو

```js-nolint
includes(searchElement)
includes(searchElement, fromIndex)
```

### پارامترها

- `searchElement`
  - : مقداری که باید جست‌وجو شود.
- `fromIndex` {{optional_inline}}
  - : اندیس صفرمبنا برای شروع جست‌وجو که [به عدد صحیح تبدیل می‌شود](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number#integer_conversion).
    - اندیس منفی از انتهای آرایه به عقب می‌شمارد؛ اگر `-array.length <= fromIndex < 0` باشد، از `fromIndex + array.length` استفاده می‌شود. بااین‌حال، جست‌وجو همچنان از ابتدا به انتهای آرایه انجام می‌شود.
    - اگر `fromIndex < -array.length` باشد یا آرگومان حذف شود، مقدار `0` استفاده می‌شود و کل آرایه جست‌وجو خواهد شد.
    - اگر `fromIndex >= array.length` باشد، آرایه جست‌وجو نمی‌شود و `false` برمی‌گردد.

### مقدار بازگشتی

مقدار بولی؛ اگر `searchElement` در آرایه (یا در بخشی که با `fromIndex` مشخص شده) پیدا شود `true` است.

## توضیحات

متد `includes()` مقدار `searchElement` را با اعضای آرایه با استفاده از الگوریتم [SameValueZero](/en-US/docs/Web/JavaScript/Guide/Equality_comparisons_and_sameness#same-value-zero_equality) مقایسه می‌کند. این الگوریتم مانند برابری سخت‌گیرانهٔ `===` عمل می‌کند (`-0` و `+0` را برابر می‌داند)، با این تفاوت که {{jsxref("NaN")}} را با خودش برابر در نظر می‌گیرد.

هنگام استفاده روی [آرایه‌های تنک](/en-US/docs/Web/JavaScript/Guide/Indexed_collections#sparse_arrays)، متد `includes()` خانه‌های خالی را مانند خانه‌هایی با مقدار `undefined` بررسی می‌کند.

متد `includes()` [عمومی](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#generic_array_methods) است و فقط انتظار دارد مقدار `this` ویژگی `length` و ویژگی‌هایی با کلید عدد صحیح داشته باشد.

## مثال‌ها

### استفاده از includes()

```js
[1, 2, 3].includes(2); // true
[1, 2, 3].includes(4); // false
[1, 2, 3].includes(3, 3); // false
[1, 2, 3].includes(3, -1); // true
[1, 2, NaN].includes(NaN); // true
["1", "2", "3"].includes(3); // false
```

### وقتی fromIndex بزرگ‌تر یا مساوی طول آرایه است

اگر `fromIndex` بزرگ‌تر یا مساوی طول آرایه باشد، `false` برگردانده می‌شود و آرایه جست‌وجو نخواهد شد.

```js
const arr = ["a", "b", "c"];

arr.includes("c", 3); // false
arr.includes("c", 100); // false
```

### وقتی اندیس محاسبه‌شده منفی است

اگر `fromIndex` منفی باشد، اندیس محاسبه‌شده محل آغاز جست‌وجوی `searchElement` در آرایه است. اگر این اندیس کوچک‌تر یا مساوی `0` باشد، کل آرایه جست‌وجو می‌شود.

```js
// array length is 3
// fromIndex is -100
// computed index is 3 + (-100) = -97

const arr = ["a", "b", "c"];

arr.includes("a", -100); // true
arr.includes("b", -100); // true
arr.includes("c", -100); // true
arr.includes("a", -2); // false
```

### استفاده از includes() on sparse arrays

می‌توانید در آرایهٔ تنک به‌دنبال `undefined` بگردید و `true` دریافت کنید.

```js
console.log([1, , 3].includes(undefined)); // true
```

### فراخوانی includes() روی اشیایی غیر از آرایه

متد `includes()` ویژگی `length` مقدار `this` را می‌خواند و سپس به ویژگی‌هایی دسترسی پیدا می‌کند که کلیدشان عدد صحیح نامنفی و کوچک‌تر از `length` باشد.

```js
const arrayLike = {
  length: 3,
  0: 2,
  1: 3,
  2: 4,
  3: 1, // ignored by includes() since length is 3
};
console.log(Array.prototype.includes.call(arrayLike, 2));
// true
console.log(Array.prototype.includes.call(arrayLike, 1));
// false
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Polyfill of `Array.prototype.includes` in `core-js`](https://github.com/zloirock/core-js#ecmascript-array)
- [es-shims polyfill of `Array.prototype.includes`](https://www.npmjs.com/package/array-includes)
- [Indexed collections](/en-US/docs/Web/JavaScript/Guide/Indexed_collections) guide
- {{jsxref("Array")}}
- {{jsxref("Array.prototype.indexOf()")}}
- {{jsxref("Array.prototype.find()")}}
- {{jsxref("Array.prototype.findIndex()")}}
- {{jsxref("TypedArray.prototype.includes()")}}
- {{jsxref("String.prototype.includes()")}}
