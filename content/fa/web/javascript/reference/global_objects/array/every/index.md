---
title: "Array.prototype.every()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every"
---

---
title: Array.prototype.every()
short-title: every()
slug: Web/JavaScript/Reference/Global_Objects/Array/every
page-type: javascript-instance-method
browser-compat: javascript.builtins.Array.every
sidebar: jsref
---

متد **`every()`** در نمونه‌های {{jsxref("Array")}} اگر عضوی پیدا کند که تابع آزمون داده‌شده را برآورده نکند، `false` برمی‌گرداند؛ در غیر این صورت `true`.

{{InteractiveExample("JavaScript Demo: Array.prototype.every()", "shorter")}}

```js interactive-example
const isBelowThreshold = (currentValue) => currentValue < 40;

const array1 = [1, 30, 39, 29, 10, 13];

console.log(array1.every(isBelowThreshold));
// Expected output: true
```

## نحو

```js-nolint
every(callbackFn)
every(callbackFn, thisArg)
```

### پارامترها

- `callbackFn`
  - : تابعی که برای هر عضو آرایه اجرا می‌شود. اگر عضو آزمون را بگذراند باید مقدار [truthy](/en-US/docs/Glossary/Truthy) و در غیر این صورت مقدار [falsy](/en-US/docs/Glossary/Falsy) برگرداند. تابع با آرگومان‌های زیر فراخوانی می‌شود:
    - `element`
      - : عضو فعلی آرایه که در حال پردازش است.
    - `index`
      - : اندیس عضو فعلی آرایه.
    - `array`
      - : آرایه‌ای که `every()` روی آن فراخوانی شده است.
- `thisArg` {{optional_inline}}
  - : مقداری که هنگام اجرای `callbackFn` به‌عنوان `this` استفاده می‌شود. بخش [متدهای تکرارشونده](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#iterative_methods) را ببینید.

### مقدار بازگشتی

اگر `callbackFn` برای هیچ عضوی مقدار {{Glossary("falsy")}} برنگرداند، نتیجه `true` است؛ به‌محض دریافت چنین مقداری، `false` برگردانده می‌شود.

## توضیحات

متد `every()` یک [متد تکرارشونده](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#iterative_methods) است. تابع `callbackFn` را برای هر عضو اجرا می‌کند تا زمانی که مقدار [falsy](/en-US/docs/Glossary/Falsy) برگرداند. اگر چنین عضوی پیدا شود، `every()` فوراً `false` برمی‌گرداند و پیمایش را متوقف می‌کند. اگر تابع برای همهٔ اعضا مقدار [truthy](/en-US/docs/Glossary/Truthy) برگرداند، نتیجه `true` است. برای اطلاعات بیشتر، بخش [متدهای تکرارشونده](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#iterative_methods) را بخوانید.

`every` مانند کمیت‌گذار «برای همه» در ریاضیات عمل می‌کند. به‌ویژه، برای آرایهٔ خالی `true` برمی‌گرداند؛ زیرا از نظر منطقی، همهٔ اعضای [مجموعهٔ تهی](https://en.wikipedia.org/wiki/Empty_set#Properties) هر شرطی را برآورده می‌کنند.

`callbackFn` فقط برای اندیس‌هایی اجرا می‌شود که مقدار دارند و برای خانه‌های خالی در [آرایه‌های تنک](/en-US/docs/Web/JavaScript/Guide/Indexed_collections#sparse_arrays) فراخوانی نمی‌شود.

متد `every()` [عمومی](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#generic_array_methods) است و فقط انتظار دارد مقدار `this` ویژگی `length` و ویژگی‌هایی با کلید عدد صحیح داشته باشد.

## مثال‌ها

### بررسی مقدار همهٔ اعضای آرایه

مثال زیر بررسی می‌کند که آیا همهٔ اعضای آرایه بزرگ‌تر یا مساوی ۱۰ هستند یا نه.

```js
function isBigEnough(element, index, array) {
  return element >= 10;
}
[12, 5, 8, 130, 44].every(isBigEnough); // false
[12, 54, 18, 130, 44].every(isBigEnough); // true
```

### بررسی زیرمجموعه بودن یک آرایه نسبت به آرایهٔ دیگر

مثال زیر بررسی می‌کند که آیا همهٔ اعضای یک آرایه در آرایهٔ دیگری وجود دارند یا نه.

```js
const isSubset = (array1, array2) =>
  array2.every((element) => array1.includes(element));

console.log(isSubset([1, 2, 3, 4, 5, 6, 7], [5, 7, 6])); // true
console.log(isSubset([1, 2, 3, 4, 5, 6, 7], [5, 8, 7])); // false
```

### استفاده از آرگومان سوم callbackFn

آرگومان `array` زمانی مفید است که بخواهید به عضو دیگری از آرایه دسترسی پیدا کنید. مثال زیر ابتدا با `filter()` مقادیر مثبت را جدا می‌کند و سپس با `every()` بررسی می‌کند که آیا آرایه به‌صورت صعودیِ سخت‌گیرانه مرتب شده است یا نه.

```js
const numbers = [-2, 4, -8, 16, -32];
const isIncreasing = numbers
  .filter((num) => num > 0)
  .every((num, idx, arr) => {
    // Without the arr argument, there's no way to easily access the
    // intermediate array without saving it to a variable.
    if (idx === 0) return true;
    return num > arr[idx - 1];
  });
console.log(isIncreasing); // true
```

### استفاده از every() روی آرایه‌های تنک

`every()` تابع شرط را برای خانه‌های خالی اجرا نمی‌کند.

```js
console.log([1, , 3].every((x) => x !== undefined)); // true
console.log([2, , 2].every((x) => x === 2)); // true
```

### فراخوانی every() روی اشیایی غیر از آرایه

متد `every()` ویژگی `length` مقدار `this` را می‌خواند و سپس به ویژگی‌هایی دسترسی پیدا می‌کند که کلیدشان عدد صحیح نامنفی و کوچک‌تر از `length` باشد؛ این کار تا بررسی همهٔ آن‌ها یا بازگشت `false` از `callbackFn` ادامه می‌یابد.

```js
const arrayLike = {
  length: 3,
  0: "a",
  1: "b",
  2: "c",
  3: 345, // ignored by every() since length is 3
};
console.log(
  Array.prototype.every.call(arrayLike, (x) => typeof x === "string"),
); // true
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Polyfill of `Array.prototype.every` in `core-js`](https://github.com/zloirock/core-js#ecmascript-array)
- [es-shims polyfill of `Array.prototype.every`](https://www.npmjs.com/package/array.prototype.every)
- [Indexed collections](/en-US/docs/Web/JavaScript/Guide/Indexed_collections) guide
- {{jsxref("Array")}}
- {{jsxref("Array.prototype.forEach()")}}
- {{jsxref("Array.prototype.some()")}}
- {{jsxref("Array.prototype.find()")}}
- {{jsxref("TypedArray.prototype.every()")}}
