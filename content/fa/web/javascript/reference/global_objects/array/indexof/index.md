---
title: "Array.prototype.indexOf()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf"
---

---
title: Array.prototype.indexOf()
short-title: indexOf()
slug: Web/JavaScript/Reference/Global_Objects/Array/indexOf
page-type: javascript-instance-method
browser-compat: javascript.builtins.Array.indexOf
sidebar: jsref
---

متد **`indexOf()`** در نمونه‌های {{jsxref("Array")}} اندیس نخستین حضور عضو مشخص‌شده در آرایه را برمی‌گرداند؛ اگر وجود نداشته باشد، `-1` برمی‌گرداند.

{{InteractiveExample("JavaScript Demo: Array.prototype.indexOf()")}}

```js interactive-example
const beasts = ["ant", "bison", "camel", "duck", "bison"];

console.log(beasts.indexOf("bison"));
// Expected output: 1

// Start from index 2
console.log(beasts.indexOf("bison", 2));
// Expected output: 4

console.log(beasts.indexOf("giraffe"));
// Expected output: -1
```

## نحو

```js-nolint
indexOf(searchElement)
indexOf(searchElement, fromIndex)
```

### پارامترها

- `searchElement`
  - : عضوی که باید در آرایه پیدا شود.
- `fromIndex` {{optional_inline}}
  - : اندیس صفرمبنا برای شروع جست‌وجو که [به عدد صحیح تبدیل می‌شود](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number#integer_conversion).
    - اندیس منفی از انتهای آرایه به عقب می‌شمارد؛ اگر `-array.length <= fromIndex < 0` باشد، از `fromIndex + array.length` استفاده می‌شود. بااین‌حال، جست‌وجو همچنان از ابتدا به انتهای آرایه انجام می‌شود.
    - اگر `fromIndex < -array.length` باشد یا حذف شود، مقدار `0` استفاده می‌شود و کل آرایه جست‌وجو می‌شود.
    - اگر `fromIndex >= array.length` باشد، آرایه جست‌وجو نمی‌شود و `-1` برمی‌گردد.

### مقدار بازگشتی

اندیس نخستین حضور `searchElement` در آرایه؛ اگر پیدا نشود `-1`.

## توضیحات

متد `indexOf()` مقدار `searchElement` را با اعضای آرایه با استفاده از [برابری سخت‌گیرانه](/en-US/docs/Web/JavaScript/Reference/Operators/Strict_equality) (همان الگوریتم عملگر `===`) مقایسه می‌کند. مقدارهای [`NaN`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/NaN) هرگز برابر در نظر گرفته نمی‌شوند؛ بنابراین اگر `searchElement` برابر `NaN` باشد، `indexOf()` همیشه `-1` برمی‌گرداند.

متد `indexOf()` خانه‌های خالی در [آرایه‌های تنک](/en-US/docs/Web/JavaScript/Guide/Indexed_collections#sparse_arrays) را نادیده می‌گیرد.

متد `indexOf()` [عمومی](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#generic_array_methods) است و فقط انتظار دارد مقدار `this` ویژگی `length` و ویژگی‌هایی با کلیدهای عدد صحیح داشته باشد.

## مثال‌ها

### استفاده از indexOf()

مثال زیر از `indexOf()` برای پیدا کردن مقدارها در آرایه استفاده می‌کند.

```js
const array = [2, 9, 9];
array.indexOf(2); // 0
array.indexOf(7); // -1
array.indexOf(9, 2); // 2
array.indexOf(2, -1); // -1
array.indexOf(2, -3); // 0
```

نمی‌توان از `indexOf()` برای جست‌وجوی `NaN` استفاده کرد.

```js
const array = [NaN];
array.indexOf(NaN); // -1
```

### یافتن همهٔ موارد حضور یک عضو

```js
const indices = [];
const array = ["a", "b", "a", "c", "a", "d"];
const element = "a";
let idx = array.indexOf(element);
while (idx !== -1) {
  indices.push(idx);
  idx = array.indexOf(element, idx + 1);
}
console.log(indices);
// [0, 2, 4]
```

### بررسی وجود عضو و به‌روزرسانی آرایه

```js
function updateVegetablesCollection(veggies, veggie) {
  if (veggies.indexOf(veggie) === -1) {
    veggies.push(veggie);
    console.log(`New veggies collection is: ${veggies}`);
  } else {
    console.log(`${veggie} already exists in the veggies collection.`);
  }
}

const veggies = ["potato", "tomato", "chillies", "green-pepper"];

updateVegetablesCollection(veggies, "spinach");
// New veggies collection is: potato,tomato,chillies,green-pepper,spinach
updateVegetablesCollection(veggies, "spinach");
// spinach already exists in the veggies collection.
```

### استفاده از indexOf() on sparse arrays

نمی‌توان با `indexOf()` خانه‌های خالی آرایه‌های تنک را جست‌وجو کرد.

```js
console.log([1, , 3].indexOf(undefined)); // -1
```

### فراخوانی indexOf() روی اشیایی غیر از آرایه

متد `indexOf()` ویژگی `length` مقدار `this` را می‌خواند و سپس به ویژگی‌هایی دسترسی پیدا می‌کند که کلیدشان عدد صحیح نامنفی و کوچک‌تر از `length` باشد.

```js
const arrayLike = {
  length: 3,
  0: 2,
  1: 3,
  2: 4,
  3: 5, // ignored by indexOf() since length is 3
};
console.log(Array.prototype.indexOf.call(arrayLike, 2));
// 0
console.log(Array.prototype.indexOf.call(arrayLike, 5));
// -1
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Polyfill of `Array.prototype.indexOf` in `core-js`](https://github.com/zloirock/core-js#ecmascript-array)
- [es-shims polyfill of `Array.prototype.indexOf`](https://www.npmjs.com/package/array.prototype.indexof)
- [Indexed collections](/en-US/docs/Web/JavaScript/Guide/Indexed_collections) guide
- {{jsxref("Array")}}
- {{jsxref("Array.prototype.findIndex()")}}
- {{jsxref("Array.prototype.findLastIndex()")}}
- {{jsxref("Array.prototype.lastIndexOf()")}}
- {{jsxref("TypedArray.prototype.indexOf()")}}
- {{jsxref("String.prototype.indexOf()")}}
