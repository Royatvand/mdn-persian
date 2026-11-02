---
title: "Array.prototype.findIndex()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex"
---

---
title: Array.prototype.findIndex()
short-title: findIndex()
slug: Web/JavaScript/Reference/Global_Objects/Array/findIndex
page-type: javascript-instance-method
browser-compat: javascript.builtins.Array.findIndex
sidebar: jsref
---

متد **`findIndex()`** در نمونه‌های {{jsxref("Array")}} اندیس نخستین عضوی را برمی‌گرداند که تابع آزمون داده‌شده را برآورده کند. اگر هیچ عضوی شرط را برآورده نکند، `-1` برگردانده می‌شود.

همچنین متد {{jsxref("Array/find", "find()")}} را ببینید که به‌جای اندیس، خودِ نخستین عضو منطبق با تابع آزمون را برمی‌گرداند.

{{InteractiveExample("JavaScript Demo: Array.prototype.findIndex()", "shorter")}}

```js interactive-example
const array = [5, 12, 8, 130, 44];

const isLargeNumber = (element) => element > 13;

console.log(array.findIndex(isLargeNumber));
// Expected output: 3
```

## نحو

```js-nolint
findIndex(callbackFn)
findIndex(callbackFn, thisArg)
```

### پارامترها

- `callbackFn`
  - : تابعی که برای هر عضو آرایه اجرا می‌شود. اگر عضو موردنظر پیدا شد باید مقداری [truthy](/en-US/docs/Glossary/Truthy) و در غیر این صورت مقداری [falsy](/en-US/docs/Glossary/Falsy) برگرداند. تابع با آرگومان‌های زیر فراخوانی می‌شود:
    - `element`
      - : عضو فعلی آرایه که در حال پردازش است.
    - `index`
      - : اندیس عضو فعلی آرایه.
    - `array`
      - : آرایه‌ای که `findIndex()` روی آن فراخوانی شده است.
- `thisArg` {{optional_inline}}
  - : مقداری که هنگام اجرای `callbackFn` به‌عنوان `this` استفاده می‌شود. بخش [متدهای تکرارشونده](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#iterative_methods) را ببینید.

### مقدار بازگشتی

اندیس نخستین عضو آرایه که آزمون را می‌گذراند؛ در غیر این صورت `-1`.

## توضیحات

`findIndex()` یک [متد تکرارشونده](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#iterative_methods) است. تابع `callbackFn` را به‌ترتیب اندیس‌های صعودی برای هر عضو اجرا می‌کند تا زمانی که مقدار [truthy](/en-US/docs/Glossary/Truthy) برگرداند. سپس اندیس آن عضو را برمی‌گرداند و پیمایش متوقف می‌شود. اگر `callbackFn` هیچ‌وقت مقدار truthy برنگرداند، نتیجه `-1` خواهد بود. برای آشنایی کلی با این رفتار، بخش [متدهای تکرارشونده](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#iterative_methods) را بخوانید.

`callbackFn` برای _تمام_ اندیس‌های آرایه اجرا می‌شود، نه فقط اندیس‌هایی که مقدار دارند. خانه‌های خالی در [آرایه‌های تنک](/en-US/docs/Web/JavaScript/Guide/Indexed_collections#sparse_arrays) مانند `undefined` رفتار می‌کنند.

متد `findIndex()` [عمومی](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#generic_array_methods) است و فقط انتظار دارد مقدار `this` ویژگی `length` و ویژگی‌هایی با کلیدهای عدد صحیح داشته باشد.

## مثال‌ها

### یافتن اندیس نخستین عدد اول در آرایه

مثال زیر اندیس نخستین عدد اول در آرایه را برمی‌گرداند؛ اگر عدد اولی وجود نداشته باشد، `-1` برمی‌گرداند.

```js
function isPrime(n) {
  if (n < 2) {
    return false;
  }
  if (n % 2 === 0) {
    return n === 2;
  }
  for (let factor = 3; factor * factor <= n; factor += 2) {
    if (n % factor === 0) {
      return false;
    }
  }
  return true;
}

console.log([4, 6, 8, 9, 12].findIndex(isPrime)); // -1, not found
console.log([4, 6, 7, 9, 12].findIndex(isPrime)); // 2 (array[2] is 7)
```

> [!NOTE]
> پیاده‌سازی `isPrime()` فقط برای نمایش مثال است. در برنامهٔ واقعی بهتر است از الگوریتمی با ذخیره‌سازی نتایج محاسبات، مانند [غربال اراتستن](https://en.wikipedia.org/wiki/Sieve_of_Eratosthenes)، استفاده کنید تا محاسبات تکراری کاهش یابد.

### استفاده از آرگومان سوم callbackFn

آرگومان `array` زمانی مفید است که بخواهید به عضو دیگری از آرایه دسترسی داشته باشید، به‌ویژه اگر متغیری برای ارجاع به آرایه ندارید. مثال زیر ابتدا با `filter()` مقادیر مثبت را جدا می‌کند و سپس با `findIndex()` نخستین عضوی را می‌یابد که از همسایه‌هایش کوچک‌تر است.

```js
const numbers = [3, -1, 1, 4, 1, 5, 9, 2, 6];
const firstTrough = numbers
  .filter((num) => num > 0)
  .findIndex((num, idx, arr) => {
    // Without the arr argument, there's no way to easily access the
    // intermediate array without saving it to a variable.
    if (idx > 0 && num >= arr[idx - 1]) return false;
    if (idx < arr.length - 1 && num >= arr[idx + 1]) return false;
    return true;
  });
console.log(firstTrough); // 1
```

### استفاده از findIndex() روی آرایه‌های تنک

می‌توانید در آرایه‌ای تنک به‌دنبال `undefined` بگردید و اندیس یک خانهٔ خالی را پیدا کنید.

```js
console.log([1, , 3].findIndex((x) => x === undefined)); // 1
```

### فراخوانی findIndex() روی اشیایی غیر از آرایه

متد `findIndex()` ویژگی `length` مقدار `this` را می‌خواند و سپس به هر ویژگی‌ای دسترسی پیدا می‌کند که کلید آن عدد صحیح نامنفی و کوچک‌تر از `length` باشد.

```js
const arrayLike = {
  length: 3,
  "-1": 0.1, // ignored by findIndex() since -1 < 0
  0: 2,
  1: 7.3,
  2: 4,
};
console.log(
  Array.prototype.findIndex.call(arrayLike, (x) => !Number.isInteger(x)),
); // 1
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Polyfill of `Array.prototype.findIndex` in `core-js`](https://github.com/zloirock/core-js#ecmascript-array)
- [es-shims polyfill of `Array.prototype.findIndex`](https://www.npmjs.com/package/array.prototype.findindex)
- [Indexed collections](/en-US/docs/Web/JavaScript/Guide/Indexed_collections) guide
- {{jsxref("Array")}}
- {{jsxref("Array.prototype.find()")}}
- {{jsxref("Array.prototype.findLast()")}}
- {{jsxref("Array.prototype.findLastIndex()")}}
- {{jsxref("Array.prototype.indexOf()")}}
- {{jsxref("Array.prototype.lastIndexOf()")}}
- {{jsxref("TypedArray.prototype.findIndex()")}}
