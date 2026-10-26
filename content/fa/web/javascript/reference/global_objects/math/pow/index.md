---
title: "Math.pow()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/pow"
---

---
title: Math.pow()
short-title: pow()
slug: Web/JavaScript/Reference/Global_Objects/Math/pow
page-type: javascript-static-method
browser-compat: javascript.builtins.Math.pow
sidebar: jsref
---

متد ایستای **`Math.pow()`** مقدار پایه را به توان مشخص‌شده می‌رساند؛ یعنی

<!-- prettier-ignore-start -->
<math display="block">
  <semantics><mrow><mrow><mo lspace="0em" rspace="0.16666666666666666em">𝙼𝚊𝚝𝚑.𝚙𝚘𝚠</mo><mo stretchy="false">(</mo><mi>𝚡</mi><mo>,</mo><mi>𝚢</mi><mo stretchy="false">)</mo></mrow><mo>=</mo><msup><mi>x</mi><mi>y</mi></msup></mrow><annotation encoding="TeX">\mathtt{\operatorname{Math.pow}(x, y)} = x^y</annotation></semantics>
</math>
<!-- prettier-ignore-end -->

{{InteractiveExample("JavaScript Demo: Math.pow()")}}

```js interactive-example
console.log(Math.pow(7, 3));
// Expected output: 343

console.log(Math.pow(4, 0.5));
// Expected output: 2

console.log(Math.pow(7, -2));
// Expected output: 0.02040816326530612
//                  (1/49)

console.log(Math.pow(-7, 0.5));
// Expected output: NaN
```

## نحو

```js-nolint
Math.pow(base, exponent)
```

### پارامترها

- `base`
  - : عدد پایه.
- `exponent`
  - : عدد توان.

### مقدار بازگشتی

عددی که برابر `base` به توان `exponent` است. در هر یک از حالت‌های زیر {{jsxref("NaN")}} برمی‌گرداند:

- مقدار `exponent` برابر `NaN` باشد.
- `base` برابر `NaN` باشد و `exponent` صفر نباشد.
- `base` برابر ±۱ و `exponent` برابر ±`Infinity` باشد.
- `base < 0` باشد و `exponent` عدد صحیح نباشد.

## توضیحات

`Math.pow()` معادل عملگر [`**`](/en-US/docs/Web/JavaScript/Reference/Operators/Exponentiation) است، با این تفاوت که `Math.pow()` فقط عدد می‌پذیرد.

`Math.pow(NaN, 0)` (و عبارت معادل `NaN ** 0`) تنها حالتی است که {{jsxref("NaN")}} در عملیات ریاضی انتشار پیدا نمی‌کند؛ با وجود `NaN` بودن عملوند، نتیجه `1` است. همچنین وقتی `base` برابر ۱ و `exponent` نامتناهی (±Infinity یا `NaN`) باشد، رفتار جاوااسکریپت با IEEE 754 متفاوت است: استاندارد IEEE 754 نتیجه را ۱ می‌داند، اما جاوااسکریپت برای حفظ سازگاری با رفتار قدیمی خود `NaN` برمی‌گرداند.

چون `pow()` متدی ایستا از `Math` است، آن را به‌شکل `Math.pow()` استفاده کنید؛ `Math` سازنده نیست و از آن نمونه ساخته نمی‌شود.

## مثال‌ها

### استفاده از Math.pow()

```js
// Basic cases
Math.pow(7, 2); // 49
Math.pow(7, 3); // 343
Math.pow(2, 10); // 1024

// Fractional exponents
Math.pow(4, 0.5); // 2 (square root of 4)
Math.pow(8, 1 / 3); // 2 (cube root of 8)
Math.pow(2, 0.5); // 1.4142135623730951 (square root of 2)
Math.pow(2, 1 / 3); // 1.2599210498948732 (cube root of 2)

// Signed exponents
Math.pow(7, -2); // 0.02040816326530612 (1/49)
Math.pow(8, -1 / 3); // 0.5

// Signed bases
Math.pow(-7, 2); // 49 (squares are positive)
Math.pow(-7, 3); // -343 (cubes can be negative)
Math.pow(-7, 0.5); // NaN (negative numbers don't have a real square root)
// Due to "even" and "odd" roots laying close to each other,
// and limits in the floating number precision,
// negative bases with fractional exponents always return NaN,
// even when the mathematical result is real
Math.pow(-7, 1 / 3); // NaN

// Zero and infinity
Math.pow(0, 0); // 1 (anything ** ±0 is 1)
Math.pow(Infinity, 0.1); // Infinity (positive exponent)
Math.pow(Infinity, -1); // 0 (negative exponent)
Math.pow(-Infinity, 1); // -Infinity (positive odd integer exponent)
Math.pow(-Infinity, 1.5); // Infinity (positive exponent)
Math.pow(-Infinity, -1); // -0 (negative odd integer exponent)
Math.pow(-Infinity, -1.5); // 0 (negative exponent)
Math.pow(0, 1); // 0 (positive exponent)
Math.pow(0, -1); // Infinity (negative exponent)
Math.pow(-0, 1); // -0 (positive odd integer exponent)
Math.pow(-0, 1.5); // 0 (positive exponent)
Math.pow(-0, -1); // -Infinity (negative odd integer exponent)
Math.pow(-0, -1.5); // Infinity (negative exponent)
Math.pow(0.9, Infinity); // 0
Math.pow(1, Infinity); // NaN
Math.pow(1.1, Infinity); // Infinity
Math.pow(0.9, -Infinity); // Infinity
Math.pow(1, -Infinity); // NaN
Math.pow(1.1, -Infinity); // 0

// NaN: only Math.pow(NaN, 0) does not result in NaN
Math.pow(NaN, 0); // 1
Math.pow(NaN, 1); // NaN
Math.pow(1, NaN); // NaN
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{jsxref("Math.cbrt()")}}
- {{jsxref("Math.exp()")}}
- {{jsxref("Math.log()")}}
- {{jsxref("Math.sqrt()")}}
- [Exponentiation (`**`)](/en-US/docs/Web/JavaScript/Reference/Operators/Exponentiation)
