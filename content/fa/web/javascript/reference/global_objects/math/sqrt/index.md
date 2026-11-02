---
title: "Math.sqrt()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/sqrt"
---

---
title: Math.sqrt()
short-title: sqrt()
slug: Web/JavaScript/Reference/Global_Objects/Math/sqrt
page-type: javascript-static-method
browser-compat: javascript.builtins.Math.sqrt
sidebar: jsref
---

متد ایستای **`Math.sqrt()`** جذر یک عدد را برمی‌گرداند؛ یعنی

<!-- prettier-ignore-start -->
<math display="block">
  <semantics><mrow><mo>∀</mo><mi>x</mi><mo>≥</mo><mn>0</mn><mo>,</mo><mspace width="0.2777777777777778em"></mspace><mrow><mo lspace="0em" rspace="0.16666666666666666em">𝙼𝚊𝚝𝚑.𝚜𝚚𝚛𝚝</mo><mo stretchy="false">(</mo><mi>𝚡</mi><mo stretchy="false">)</mo></mrow><mo>=</mo><msqrt><mi>x</mi></msqrt><mo>=</mo><mtext>the unique&nbsp;</mtext><mi>y</mi><mo>≥</mo><mn>0</mn><mtext>&nbsp;such that&nbsp;</mtext><msup><mi>y</mi><mn>2</mn></msup><mo>=</mo><mi>x</mi></mrow><annotation encoding="TeX">\forall x \geq 0,\;\mathtt{\operatorname{Math.sqrt}(x)} = \sqrt{x} = \text{the unique } y \geq 0 \text{ such that } y^2 = x</annotation></semantics>
</math>
<!-- prettier-ignore-end -->

{{InteractiveExample("JavaScript Demo: Math.sqrt()")}}

```js interactive-example
function calcHypotenuse(a, b) {
  return Math.sqrt(a * a + b * b);
}

console.log(calcHypotenuse(3, 4));
// Expected output: 5

console.log(calcHypotenuse(5, 12));
// Expected output: 13

console.log(calcHypotenuse(0, 0));
// Expected output: 0
```

## نحو

```js-nolint
Math.sqrt(x)
```

### پارامترها

- `x`
  - : عددی بزرگ‌تر یا مساوی ۰.

### مقدار بازگشتی

جذر `x`، یعنی عددی نامنفی. اگر `x < 0` باشد، {{jsxref("NaN")}} برمی‌گرداند.

## توضیحات

چون `sqrt()` متدی ایستا از `Math` است، همیشه آن را به‌شکل `Math.sqrt()` به کار ببرید؛ `Math` سازنده نیست و از آن نمونه ساخته نمی‌شود.

## مثال‌ها

### استفاده از Math.sqrt()

```js
Math.sqrt(-1); // NaN
Math.sqrt(-0); // -0
Math.sqrt(0); // 0
Math.sqrt(1); // 1
Math.sqrt(2); // 1.414213562373095
Math.sqrt(9); // 3
Math.sqrt(Infinity); // Infinity
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{jsxref("Math.cbrt()")}}
- {{jsxref("Math.exp()")}}
- {{jsxref("Math.log()")}}
- {{jsxref("Math.pow()")}}
