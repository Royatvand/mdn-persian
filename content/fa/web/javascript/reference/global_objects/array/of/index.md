---
title: "Array.of()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/of"
---

---
title: Array.of()
short-title: of()
slug: Web/JavaScript/Reference/Global_Objects/Array/of
page-type: javascript-static-method
browser-compat: javascript.builtins.Array.of
sidebar: jsref
---

متد ایستای **`Array.of()`** با تعداد متغیری از آرگومان‌ها، یک نمونهٔ جدید از `Array` می‌سازد؛ تعداد و نوع آرگومان‌ها در این رفتار تفاوتی ایجاد نمی‌کند.

{{InteractiveExample("JavaScript Demo: Array.of()", "shorter")}}

```js interactive-example
console.log(Array.of("foo", 2, "bar", true));
// Expected output: Array ["foo", 2, "bar", true]

console.log(Array.of());
// Expected output: Array []
```

## نحو

```js-nolint
Array.of()
Array.of(element1)
Array.of(element1, element2)
Array.of(element1, element2, /* …, */ elementN)
```

### پارامترها

- `element1`, …, `elementN`
  - : عناصری که برای ساخت آرایه استفاده می‌شوند.

### مقدار بازگشتی

A new {{jsxref("Array")}} instance.

## توضیحات

تفاوت `Array.of()` با سازندهٔ [`Array()`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Array) در نحوهٔ برخورد با یک آرگومان است: `Array.of(7)` آرایه‌ای با یک عضو به مقدار `7` می‌سازد، اما `Array(7)` آرایه‌ای خالی با ویژگی `length` برابر ۷ ایجاد می‌کند. این یعنی آرایه هفت خانهٔ خالی دارد، نه خانه‌هایی که مقدار واقعی {{jsxref("undefined")}} داشته باشند.

```js
Array.of(7); // [7]
Array(7); // array of 7 empty slots

Array.of(1, 2, 3); // [1, 2, 3]
Array(1, 2, 3); // [1, 2, 3]
```

متد `Array.of()` یک متد کارخانه‌ای عمومی است. برای مثال، اگر زیرکلاسی از `Array` این متد را به ارث ببرد، فراخوانی آن نمونه‌ای از همان زیرکلاس می‌سازد، نه از `Array`. مقدار `this` می‌تواند هر تابع سازنده‌ای باشد که طول آرایهٔ جدید را به‌عنوان آرگومان می‌پذیرد؛ سازنده با تعداد آرگومان‌های ارسال‌شده به `of()` فراخوانی می‌شود. پس از اختصاص همهٔ عناصر، مقدار نهایی `length` دوباره تنظیم می‌شود. اگر `this` تابع سازنده نباشد، از سازندهٔ معمولی `Array` استفاده می‌شود.

## مثال‌ها

### استفاده از Array.of()

```js
Array.of(1); // [1]
Array.of(1, 2, 3); // [1, 2, 3]
Array.of(undefined); // [undefined]
```

### فراخوانی of() روی سازنده‌هایی غیر از Array

متد `of()` را می‌توان روی هر تابع سازنده‌ای فراخوانی کرد که آرگومانی نشان‌دهندهٔ طول آرایهٔ جدید می‌پذیرد.

```js
function NotArray(len) {
  console.log("NotArray called with length", len);
}

console.log(Array.of.call(NotArray, 1, 2, 3));
// NotArray called with length 3
// NotArray { '0': 1, '1': 2, '2': 3, length: 3 }

console.log(Array.of.call(Object)); // [Number: 0] { length: 0 }
```

اگر مقدار `this` سازنده نباشد، یک شیء معمولی `Array` برگردانده می‌شود.

```js
console.log(Array.of.call({}, 1)); // [ 1 ]
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Polyfill of `Array.of` in `core-js`](https://github.com/zloirock/core-js#ecmascript-array)
- [es-shims polyfill of `Array.of`](https://www.npmjs.com/package/array.of)
- [Indexed collections](/en-US/docs/Web/JavaScript/Guide/Indexed_collections) guide
- {{jsxref("Array")}}
- {{jsxref("Array/Array", "Array()")}}
- {{jsxref("Array.from()")}}
- {{jsxref("TypedArray.of()")}}
