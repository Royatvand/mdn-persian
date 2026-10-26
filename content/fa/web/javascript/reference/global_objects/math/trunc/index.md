---
title: "Math.trunc()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/trunc"
---

---
title: Math.trunc()
short-title: trunc()
slug: Web/JavaScript/Reference/Global_Objects/Math/trunc
page-type: javascript-static-method
browser-compat: javascript.builtins.Math.trunc
sidebar: jsref
---

متد ایستای **`Math.trunc()`** با حذف بخش اعشاری، قسمت صحیح یک عدد را برمی‌گرداند.

{{InteractiveExample("JavaScript Demo: Math.trunc()")}}

```js interactive-example
console.log(Math.trunc(13.37));
// Expected output: 13

console.log(Math.trunc(42.84));
// Expected output: 42

console.log(Math.trunc(0.123));
// Expected output: 0

console.log(Math.trunc(-0.123));
// Expected output: -0
```

## نحو

```js-nolint
Math.trunc(x)
```

### پارامترها

- `x`
  - : یک عدد.

### مقدار بازگشتی

قسمت صحیح `x`.

## توضیحات

رفتار `Math.trunc()` از سه متد دیگر `Math` یعنی {{jsxref("Math.floor()")}}، {{jsxref("Math.ceil()")}} و {{jsxref("Math.round()")}} ساده‌تر است: این متد، چه آرگومان مثبت باشد چه منفی، نقطهٔ اعشار و رقم‌های سمت راست آن را _قطع_ می‌کند.

چون `trunc()` متدی ایستا از `Math` است، همیشه آن را به‌شکل `Math.trunc()` به کار ببرید؛ `Math` سازنده نیست و از آن نمونه ساخته نمی‌شود.

## مثال‌ها

### استفاده از Math.trunc()

```js
Math.trunc(-Infinity); // -Infinity
Math.trunc("-1.123"); // -1
Math.trunc(-0.123); // -0
Math.trunc(-0); // -0
Math.trunc(0); // 0
Math.trunc(0.123); // 0
Math.trunc(13.37); // 13
Math.trunc(42.84); // 42
Math.trunc(Infinity); // Infinity
```

### استفاده از عملیات بیتی برای قطع بخش اعشاری

> [!WARNING]
> این روش به‌دلیل وجود حالت‌های مرزی مهم، جایگزین کامل (polyfill) برای `Math.trunc()` نیست.

عملیات بیتی عملوندها را به عدد صحیح ۳۲بیتی تبدیل می‌کنند؛ از این ویژگی برای قطع بخش اعشاری اعداد ممیز شناور استفاده شده است. روش‌های رایج عبارت‌اند از:

```js
const original = 3.14;
const truncated1 = ~~original; // Double negation
const truncated2 = original & -1; // Bitwise AND with -1
const truncated3 = original | 0; // Bitwise OR with 0
const truncated4 = original ^ 0; // Bitwise XOR with 0
const truncated5 = original >> 0; // Bitwise shifting by 0
```

توجه کنید که این کار در اصل `toInt32` است و با `Math.trunc` یکسان نیست. اگر مقدار در بازهٔ ‎-2<sup>31</sup> - 1 < `value` < 2<sup>31</sup> (یعنی ‎-2147483649 < `value` < 2147483648) نباشد، تبدیل سرریز می‌کند.

```js
const a = ~~2147483648; // -2147483648
const b = ~~-2147483649; // 2147483647
const c = ~~4294967296; // 0
```

فقط زمانی از `~~` به‌جای `Math.trunc()` استفاده کنید که مطمئن باشید ورودی در محدودهٔ اعداد صحیح ۳۲بیتی قرار دارد.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Polyfill of `Math.trunc` in `core-js`](https://github.com/zloirock/core-js#ecmascript-math)
- {{jsxref("Math.abs()")}}
- {{jsxref("Math.ceil()")}}
- {{jsxref("Math.floor()")}}
- {{jsxref("Math.round()")}}
- {{jsxref("Math.sign()")}}
