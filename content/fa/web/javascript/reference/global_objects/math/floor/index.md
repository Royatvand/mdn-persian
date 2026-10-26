---
title: "Math.floor()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/floor"
---

---
title: Math.floor()
short-title: floor()
slug: Web/JavaScript/Reference/Global_Objects/Math/floor
page-type: javascript-static-method
browser-compat: javascript.builtins.Math.floor
sidebar: jsref
---

متد ایستای **`Math.floor()`** همیشه عدد را به سمت پایین گرد می‌کند و بزرگ‌ترین عدد صحیح کوچک‌تر یا مساوی عدد ورودی را برمی‌گرداند.

{{InteractiveExample("JavaScript Demo: Math.floor()")}}

```js interactive-example
console.log(Math.floor(5.95));
// Expected output: 5

console.log(Math.floor(5.05));
// Expected output: 5

console.log(Math.floor(5));
// Expected output: 5

console.log(Math.floor(-5.05));
// Expected output: -6
```

## نحو

```js-nolint
Math.floor(x)
```

### پارامترها

- `x`
  - : یک عدد.

### مقدار بازگشتی

بزرگ‌ترین عدد صحیح کوچک‌تر یا مساوی `x`؛ این مقدار با [`-Math.ceil(-x)`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/ceil) برابر است.

## توضیحات

چون `floor()` متدی ایستا از `Math` است، همیشه آن را به‌شکل `Math.floor()` به کار ببرید؛ `Math` سازنده نیست و از آن نمونه ساخته نمی‌شود.

## مثال‌ها

### استفاده از Math.floor()

```js
Math.floor(-Infinity); // -Infinity
Math.floor(-45.95); // -46
Math.floor(-45.05); // -46
Math.floor(-0); // -0
Math.floor(0); // 0
Math.floor(4); // 4
Math.floor(45.05); // 45
Math.floor(45.95); // 45
Math.floor(Infinity); // Infinity
```

### تنظیم اعشار

در این مثال متدی به نام `decimalAdjust()` پیاده‌سازی می‌کنیم که نسخهٔ گسترش‌یافته‌ای از `Math.floor()`، {{jsxref("Math.ceil()")}} و {{jsxref("Math.round()")}} است. این سه تابع مقدار را در مرتبهٔ یکان تنظیم می‌کنند؛ اما `decimalAdjust` پارامتر `exp` می‌گیرد تا مشخص کند عدد در چه مرتبه‌ای تنظیم شود. برای مثال، `-1` یعنی یک رقم پس از ممیز باقی بماند (مانند «× 10<sup>-1</sup>»). پارامتر `type` نیز روش تنظیم را از میان `round`، `floor` یا `ceil` انتخاب می‌کند.

این متد عدد را در توان مناسبی از ۱۰ ضرب می‌کند، حاصل را به نزدیک‌ترین عدد صحیح گرد می‌کند و سپس بر همان توان ۱۰ تقسیم می‌کند. برای حفظ دقت، از متد [`toString()`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toString) استفاده می‌کند که عددهای بسیار بزرگ یا کوچک را با نماد علمی (مانند `6.02e23`) نمایش می‌دهد.

```js
/**
 * Adjusts a number to the specified digit.
 *
 * @param {"round" | "floor" | "ceil"} type The type of adjustment.
 * @param {number} value The number.
 * @param {number} exp The exponent (the 10 logarithm of the adjustment base).
 * @returns {number} The adjusted value.
 */
function decimalAdjust(type, value, exp) {
  type = String(type);
  if (!["round", "floor", "ceil"].includes(type)) {
    throw new TypeError(
      "The type of decimal adjustment must be one of 'round', 'floor', or 'ceil'.",
    );
  }
  exp = Number(exp);
  value = Number(value);
  if (exp % 1 !== 0 || Number.isNaN(value)) {
    return NaN;
  } else if (exp === 0) {
    return Math[type](value);
  }
  const [magnitude, exponent = 0] = value.toString().split("e");
  const adjustedValue = Math[type](`${magnitude}e${exponent - exp}`);
  // Shift back
  const [newMagnitude, newExponent = 0] = adjustedValue.toString().split("e");
  return Number(`${newMagnitude}e${Number(newExponent) + exp}`);
}

// Decimal round
const round10 = (value, exp) => decimalAdjust("round", value, exp);
// Decimal floor
const floor10 = (value, exp) => decimalAdjust("floor", value, exp);
// Decimal ceil
const ceil10 = (value, exp) => decimalAdjust("ceil", value, exp);

// Round
round10(55.55, -1); // 55.6
round10(55.549, -1); // 55.5
round10(55, 1); // 60
round10(54.9, 1); // 50
round10(-55.55, -1); // -55.5
round10(-55.551, -1); // -55.6
round10(-55, 1); // -50
round10(-55.1, 1); // -60
// Floor
floor10(55.59, -1); // 55.5
floor10(59, 1); // 50
floor10(-55.51, -1); // -55.6
floor10(-51, 1); // -60
// Ceil
ceil10(55.51, -1); // 55.6
ceil10(51, 1); // 60
ceil10(-55.59, -1); // -55.5
ceil10(-59, 1); // -50
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{jsxref("Math.abs()")}}
- {{jsxref("Math.ceil()")}}
- {{jsxref("Math.round()")}}
- {{jsxref("Math.sign()")}}
- {{jsxref("Math.trunc()")}}
