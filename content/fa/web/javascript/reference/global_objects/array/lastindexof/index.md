---
title: "Array.prototype.lastIndexOf()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/lastIndexOf"
---

---
title: Array.prototype.lastIndexOf()
short-title: lastIndexOf()
slug: Web/JavaScript/Reference/Global_Objects/Array/lastIndexOf
page-type: javascript-instance-method
browser-compat: javascript.builtins.Array.lastIndexOf
sidebar: jsref
---

متد **`lastIndexOf()`** در نمونه‌های {{jsxref("Array")}} اندیس آخرین حضور عضو مشخص‌شده را برمی‌گرداند؛ اگر وجود نداشته باشد، `-1` برمی‌گرداند. جست‌وجو از `fromIndex` به سمت عقب انجام می‌شود.

{{InteractiveExample("JavaScript Demo: Array.prototype.lastIndexOf()")}}

```js interactive-example
const animals = ["Dodo", "Tiger", "Penguin", "Dodo"];

console.log(animals.lastIndexOf("Dodo"));
// Expected output: 3

console.log(animals.lastIndexOf("Tiger"));
// Expected output: 1
```

## نحو

```js-nolint
lastIndexOf(searchElement)
lastIndexOf(searchElement, fromIndex)
```

### پارامترها

- `searchElement`
  - : عضوی که باید در آرایه پیدا شود.
- `fromIndex` {{optional_inline}}
  - : اندیس صفرمبنا برای آغاز جست‌وجو به سمت عقب که [به عدد صحیح تبدیل می‌شود](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number#integer_conversion).
    - اندیس منفی از انتهای آرایه به عقب می‌شمارد؛ اگر `-array.length <= fromIndex < 0` باشد، از `fromIndex + array.length` استفاده می‌شود.
    - اگر `fromIndex < -array.length` باشد، آرایه جست‌وجو نمی‌شود و `-1` برمی‌گردد. می‌توان تصور کرد جست‌وجو از موقعیتی ناموجود پیش از ابتدای آرایه آغاز می‌شود و به عقب می‌رود؛ در این مسیر عضوی از آرایه وجود ندارد، پس `searchElement` پیدا نمی‌شود.
    - اگر `fromIndex >= array.length` باشد یا `fromIndex` حذف شود یا `undefined` باشد، از `array.length - 1` استفاده می‌شود و کل آرایه جست‌وجو خواهد شد. می‌توان تصور کرد جست‌وجو از موقعیتی ناموجود پس از انتهای آرایه شروع می‌شود و به عقب می‌رود تا به آخرین موقعیت واقعی برسد و سپس اعضای آرایه را بررسی کند.

### مقدار بازگشتی

اندیس آخرین حضور `searchElement` در آرایه؛ اگر پیدا نشود `-1`.

## توضیحات

متد `lastIndexOf()` مقدار `searchElement` را با اعضای آرایه با استفاده از [برابری سخت‌گیرانه](/en-US/docs/Web/JavaScript/Reference/Operators/Strict_equality) (همان الگوریتم عملگر `===`) مقایسه می‌کند. مقدارهای [`NaN`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/NaN) هرگز برابر در نظر گرفته نمی‌شوند؛ بنابراین اگر `searchElement` برابر `NaN` باشد، `lastIndexOf()` همیشه `-1` برمی‌گرداند.

متد `lastIndexOf()` خانه‌های خالی در [آرایه‌های تنک](/en-US/docs/Web/JavaScript/Guide/Indexed_collections#sparse_arrays) را نادیده می‌گیرد.

متد `lastIndexOf()` [عمومی](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#generic_array_methods) است و فقط انتظار دارد مقدار `this` ویژگی `length` و ویژگی‌هایی با کلیدهای عدد صحیح داشته باشد.

## مثال‌ها

### استفاده از lastIndexOf()

مثال زیر از `lastIndexOf()` برای پیدا کردن مقدارها در آرایه استفاده می‌کند.

```js
const numbers = [2, 5, 9, 2];
numbers.lastIndexOf(2); // 3
numbers.lastIndexOf(7); // -1
numbers.lastIndexOf(2, 3); // 3
numbers.lastIndexOf(2, 2); // 0
numbers.lastIndexOf(2, -2); // 0
numbers.lastIndexOf(2, -1); // 3
```

نمی‌توان از `lastIndexOf()` برای جست‌وجوی `NaN` استفاده کرد.

```js
const array = [NaN];
array.lastIndexOf(NaN); // -1
```

### یافتن همهٔ موارد حضور یک عضو

مثال زیر با استفاده از `lastIndexOf` همهٔ اندیس‌های یک عضو را در آرایه پیدا می‌کند و هر اندیس را با {{jsxref("Array/push", "push()")}} به آرایه‌ای دیگر اضافه می‌کند.

```js
const indices = [];
const array = ["a", "b", "a", "c", "a", "d"];
const element = "a";
let idx = array.lastIndexOf(element);
while (idx !== -1) {
  indices.push(idx);
  idx = idx > 0 ? array.lastIndexOf(element, idx - 1) : -1;
}

console.log(indices);
// [4, 2, 0]
```

توجه کنید که باید حالت `idx === 0` را جداگانه مدیریت کنیم؛ زیرا اگر عضو، نخستین عضو آرایه باشد، صرف‌نظر از مقدار `fromIndex` پیدا می‌شود. این رفتار با متد {{jsxref("Array/indexOf", "indexOf()")}} متفاوت است.

### استفاده از lastIndexOf() on sparse arrays

نمی‌توان با `lastIndexOf()` خانه‌های خالی آرایه‌های تنک را جست‌وجو کرد.

```js
console.log([1, , 3].lastIndexOf(undefined)); // -1
```

### فراخوانی lastIndexOf() روی اشیایی غیر از آرایه

متد `lastIndexOf()` ویژگی `length` مقدار `this` را می‌خواند و سپس به ویژگی‌هایی دسترسی پیدا می‌کند که کلیدشان عدد صحیح نامنفی و کوچک‌تر از `length` باشد.

```js
const arrayLike = {
  length: 3,
  0: 2,
  1: 3,
  2: 2,
  3: 5, // ignored by lastIndexOf() since length is 3
};
console.log(Array.prototype.lastIndexOf.call(arrayLike, 2));
// 2
console.log(Array.prototype.lastIndexOf.call(arrayLike, 5));
// -1
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Polyfill of `Array.prototype.lastIndexOf` in `core-js`](https://github.com/zloirock/core-js#ecmascript-array)
- [es-shims polyfill of `Array.prototype.lastIndexOf`](https://www.npmjs.com/package/array.prototype.lastindexof)
- [Indexed collections](/en-US/docs/Web/JavaScript/Guide/Indexed_collections) guide
- {{jsxref("Array")}}
- {{jsxref("Array.prototype.findIndex()")}}
- {{jsxref("Array.prototype.findLastIndex()")}}
- {{jsxref("Array.prototype.indexOf()")}}
- {{jsxref("TypedArray.prototype.lastIndexOf()")}}
- {{jsxref("String.prototype.lastIndexOf()")}}
