---
title: "Array.prototype.some()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some"
---

---
title: Array.prototype.some()
short-title: some()
slug: Web/JavaScript/Reference/Global_Objects/Array/some
page-type: javascript-instance-method
browser-compat: javascript.builtins.Array.some
sidebar: jsref
---

متد **`some()`** در نمونه‌های {{jsxref("Array")}} اگر عضوی پیدا کند که تابع آزمون داده‌شده را برآورده کند، `true` برمی‌گرداند؛ در غیر این صورت `false`.

{{InteractiveExample("JavaScript Demo: Array.prototype.some()")}}

```js interactive-example
const array = [1, 2, 3, 4, 5];

// Checks whether an element is even
const even = (element) => element % 2 === 0;

console.log(array.some(even));
// Expected output: true
```

## نحو

```js-nolint
some(callbackFn)
some(callbackFn, thisArg)
```

### پارامترها

- `callbackFn`
  - : تابعی که برای هر عضو آرایه اجرا می‌شود. اگر عضو آزمون را بگذراند باید مقدار [truthy](/en-US/docs/Glossary/Truthy) و در غیر این صورت مقدار [falsy](/en-US/docs/Glossary/Falsy) برگرداند. تابع با آرگومان‌های زیر فراخوانی می‌شود:
    - `element`
      - : عضو فعلی آرایه که در حال پردازش است.
    - `index`
      - : اندیس عضو فعلی آرایه.
    - `array`
      - : آرایه‌ای که `some()` روی آن فراخوانی شده است.
- `thisArg` {{optional_inline}}
  - : مقداری که هنگام اجرای `callbackFn` به‌عنوان `this` استفاده می‌شود. بخش [متدهای تکرارشونده](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#iterative_methods) را ببینید.

### مقدار بازگشتی

اگر `callbackFn` برای یکی از اعضای آرایه مقدار {{Glossary("truthy")}} برنگرداند، نتیجه `false` است؛ به‌محض پیدا شدن چنین مقداری، `true` برگردانده می‌شود.

## توضیحات

متد `some()` یک [متد تکرارشونده](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#iterative_methods) است. تابع `callbackFn` را برای هر عضو اجرا می‌کند تا زمانی که مقدار [truthy](/en-US/docs/Glossary/Truthy) برگرداند. اگر چنین عضوی پیدا شود، `some()` بلافاصله `true` برمی‌گرداند و پیمایش را متوقف می‌کند. اگر برای همهٔ اعضا مقدار [falsy](/en-US/docs/Glossary/Falsy) برگردد، نتیجه `false` خواهد بود. برای اطلاعات کلی دربارهٔ این متدها، بخش [متدهای تکرارشونده](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#iterative_methods) را بخوانید.

`some()` مانند کمیت‌گذار «وجود دارد» در ریاضیات عمل می‌کند. به‌ویژه، برای آرایهٔ خالی و هر شرطی `false` برمی‌گرداند.

`callbackFn` فقط برای اندیس‌هایی اجرا می‌شود که مقدار دارند؛ برای خانه‌های خالی در [آرایه‌های تنک](/en-US/docs/Web/JavaScript/Guide/Indexed_collections#sparse_arrays) فراخوانی نمی‌شود.

`some()` آرایه‌ای را که روی آن فراخوانی شده تغییر نمی‌دهد، اما تابع `callbackFn` می‌تواند این کار را انجام دهد. بااین‌حال، طول آرایه _پیش از_ نخستین فراخوانی `callbackFn` ذخیره می‌شود؛ بنابراین:

- `callbackFn` اعضایی را که پس از شروع فراخوانی `some()` و فراتر از طول اولیهٔ آرایه اضافه شده‌اند، بررسی نمی‌کند.
- تغییر اندیس‌هایی که قبلاً بررسی شده‌اند باعث فراخوانی دوبارهٔ `callbackFn` برای آن‌ها نمی‌شود.
- اگر `callbackFn` عضو موجودی را که هنوز بررسی نشده تغییر دهد، هنگام رسیدن نوبت آن عضو، مقدار جدید به تابع داده می‌شود. اعضای [حذف‌شده](/en-US/docs/Web/JavaScript/Reference/Operators/delete) بررسی نمی‌شوند.

> [!WARNING]
> تغییر هم‌زمان آرایه به روش‌های بالا اغلب کدی دشوارفهم ایجاد می‌کند و معمولاً باید از آن پرهیز کرد، مگر در موارد خاص.

متد `some()` [عمومی](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#generic_array_methods) است و فقط انتظار دارد مقدار `this` ویژگی `length` و ویژگی‌هایی با کلیدهای عدد صحیح داشته باشد.

## مثال‌ها

### بررسی مقدار اعضای آرایه

مثال زیر بررسی می‌کند که آیا عضوی از آرایه بزرگ‌تر از ۱۰ است یا نه.

```js
function isBiggerThan10(element, index, array) {
  return element > 10;
}

[2, 5, 8, 1, 4].some(isBiggerThan10); // false
[12, 5, 8, 1, 4].some(isBiggerThan10); // true
```

### بررسی اعضای آرایه با تابع پیکانی

[توابع پیکانی](/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions) برای همین آزمون، نحوی کوتاه‌تر فراهم می‌کنند.

```js
[2, 5, 8, 1, 4].some((x) => x > 10); // false
[12, 5, 8, 1, 4].some((x) => x > 10); // true
```

### بررسی وجود یک مقدار در آرایه

برای شبیه‌سازی رفتار متد `includes()`، تابع سفارشی زیر اگر مقدار در آرایه وجود داشته باشد `true` برمی‌گرداند:

```js
const fruits = ["apple", "banana", "mango", "guava"];

function checkAvailability(arr, val) {
  return arr.some((arrVal) => val === arrVal);
}

checkAvailability(fruits, "grapefruit"); // false
checkAvailability(fruits, "banana"); // true
```

### تبدیل هر مقدار به Boolean

```js
const TRUTHY_VALUES = [true, "true", 1];

function getBoolean(value) {
  if (typeof value === "string") {
    value = value.toLowerCase().trim();
  }

  return TRUTHY_VALUES.some((t) => t === value);
}

getBoolean(false); // false
getBoolean("false"); // false
getBoolean(1); // true
getBoolean("true"); // true
```

### استفاده از آرگومان سوم callbackFn

آرگومان `array` وقتی مفید است که بخواهید به عضو دیگری از آرایه دسترسی داشته باشید، به‌خصوص اگر متغیری برای ارجاع به آرایه نداشته باشید. مثال زیر ابتدا با `filter()` مقادیر مثبت را جدا می‌کند و سپس با `some()` بررسی می‌کند که آیا آرایه به‌طور صعودیِ سخت‌گیرانه مرتب است یا نه.

```js
const numbers = [3, -1, 1, 4, 1, 5];
const isIncreasing = !numbers
  .filter((num) => num > 0)
  .some((num, idx, arr) => {
    // Without the arr argument, there's no way to easily access the
    // intermediate array without saving it to a variable.
    if (idx === 0) return false;
    return num <= arr[idx - 1];
  });
console.log(isIncreasing); // false
```

### استفاده از some() روی آرایه‌های تنک

`some()` تابع شرط را برای خانه‌های خالی اجرا نمی‌کند.

```js
console.log([1, , 3].some((x) => x === undefined)); // false
console.log([1, , 1].some((x) => x !== 1)); // false
console.log([1, undefined, 1].some((x) => x !== 1)); // true
```

### فراخوانی some() روی اشیایی غیر از آرایه

متد `some()` ویژگی `length` مقدار `this` را می‌خواند و سپس به ویژگی‌هایی دسترسی پیدا می‌کند که کلیدشان عدد صحیح نامنفی و کوچک‌تر از `length` است؛ این کار تا بررسی همهٔ آن‌ها یا بازگشت `true` از `callbackFn` ادامه می‌یابد.

```js
const arrayLike = {
  length: 3,
  0: "a",
  1: "b",
  2: "c",
  3: 3, // ignored by some() since length is 3
};
console.log(Array.prototype.some.call(arrayLike, (x) => typeof x === "number"));
// false
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Polyfill of `Array.prototype.some` in `core-js`](https://github.com/zloirock/core-js#ecmascript-array)
- [es-shims polyfill of `Array.prototype.some`](https://www.npmjs.com/package/array.prototype.some)
- [Indexed collections](/en-US/docs/Web/JavaScript/Guide/Indexed_collections) guide
- {{jsxref("Array")}}
- {{jsxref("Array.prototype.every()")}}
- {{jsxref("Array.prototype.forEach()")}}
- {{jsxref("Array.prototype.find()")}}
- {{jsxref("Array.prototype.includes()")}}
- {{jsxref("TypedArray.prototype.some()")}}
