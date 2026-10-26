---
title: "Object.is()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/is"
---

---
title: Object.is()
short-title: is()
slug: Web/JavaScript/Reference/Global_Objects/Object/is
page-type: javascript-static-method
browser-compat: javascript.builtins.Object.is
sidebar: jsref
---

متد ایستای **`Object.is()`** مشخص می‌کند که آیا دو مقدار [از نظر مقدار یکسان‌اند](/en-US/docs/Web/JavaScript/Guide/Equality_comparisons_and_sameness#same-value_equality_using_object.is) یا نه.

{{InteractiveExample("JavaScript Demo: Object.is()")}}

```js interactive-example
console.log(Object.is("1", 1));
// Expected output: false

console.log(Object.is(NaN, NaN));
// Expected output: true

console.log(Object.is(-0, 0));
// Expected output: false

const obj = {};
console.log(Object.is(obj, {}));
// Expected output: false
```

## نحو

```js-nolint
Object.is(value1, value2)
```

### پارامترها

- `value1`
  - : نخستین مقداری که باید مقایسه شود.
- `value2`
  - : دومین مقداری که باید مقایسه شود.

### مقدار بازگشتی

مقدار بولی که نشان می‌دهد دو آرگومان از نظر مقدار یکسان هستند یا نه.

## توضیحات

`Object.is()` بررسی می‌کند که دو مقدار [از نظر مقدار یکسان‌اند](/en-US/docs/Web/JavaScript/Guide/Equality_comparisons_and_sameness#same-value_equality_using_object.is) یا نه. دو مقدار در شرایط زیر یکسان محسوب می‌شوند:

- هر دو {{jsxref("undefined")}} باشند
- هر دو [`null`](/en-US/docs/Web/JavaScript/Reference/Operators/null) باشند
- هر دو `true` یا هر دو `false` باشند
- هر دو رشته‌هایی با طول یکسان و نویسه‌های یکسان در ترتیب یکسان باشند
- هر دو به یک شیء واحد در حافظه ارجاع دهند
- هر دو [BigInt](/en-US/docs/Web/JavaScript/Reference/Global_Objects/BigInt) با مقدار عددی یکسان باشند
- هر دو [Symbol](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol) به مقدار نمادین یکسانی ارجاع دهند
- هر دو عدد باشند و
  - هر دو `+0` باشند
  - هر دو `-0` باشند
  - هر دو {{jsxref("NaN")}} باشند
  - یا هر دو ناصفر، غیر از {{jsxref("NaN")}} و دارای مقدار یکسان باشند

`Object.is()` معادل عملگر [`==`](/en-US/docs/Web/JavaScript/Reference/Operators/Equality) نیست. عملگر `==` پیش از بررسی برابری، در صورت متفاوت‌بودن نوع دو طرف، آن‌ها را تبدیل می‌کند (برای مثال `"" == false` برابر `true` می‌شود)، اما `Object.is()` هیچ‌یک را تبدیل نمی‌کند.

`Object.is()` همچنین با عملگر [`===`](/en-US/docs/Web/JavaScript/Reference/Operators/Strict_equality) _یکسان نیست_. تنها تفاوت آن‌ها در برخورد با صفرهای علامت‌دار و `NaN` است: عملگر `===` (و `==`) مقدارهای `-0` و `+0` را برابر می‌داند، اما `NaN` را حتی با خودش برابر نمی‌داند.

## مثال‌ها

### استفاده از Object.is()

```js
// Case 1: Evaluation result is the same as using ===
Object.is(25, 25); // true
Object.is("foo", "foo"); // true
Object.is("foo", "bar"); // false
Object.is(null, null); // true
Object.is(undefined, undefined); // true
Object.is(window, window); // true
Object.is([], []); // false
const foo = { a: 1 };
const bar = { a: 1 };
const sameFoo = foo;
Object.is(foo, foo); // true
Object.is(foo, bar); // false
Object.is(foo, sameFoo); // true

// Case 2: Signed zero
Object.is(0, -0); // false
Object.is(+0, -0); // false
Object.is(-0, -0); // true

// Case 3: NaN
Object.is(NaN, 0 / 0); // true
Object.is(NaN, Number.NaN); // true
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Polyfill of `Object.is` in `core-js`](https://github.com/zloirock/core-js#ecmascript-object)
- [es-shims polyfill of `Object.is`](https://www.npmjs.com/package/object.is)
- [Equality comparisons and sameness](/en-US/docs/Web/JavaScript/Guide/Equality_comparisons_and_sameness)
