---
title: "Date.now()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/now"
---

---
title: Date.now()
short-title: now()
slug: Web/JavaScript/Reference/Global_Objects/Date/now
page-type: javascript-static-method
browser-compat: javascript.builtins.Date.now
sidebar: jsref
---

متد ایستای **`Date.now()`** تعداد میلی‌ثانیه‌های سپری‌شده از [مبدأ زمان](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date#the_epoch_timestamps_and_invalid_date) را برمی‌گرداند؛ این مبدأ نیمه‌شب آغاز روز ۱ ژانویهٔ ۱۹۷۰ به‌وقت UTC است.

{{InteractiveExample("JavaScript Demo: Date.now()")}}

```js interactive-example
// This example takes 2 seconds to run
const start = Date.now();

console.log("starting timer...");
// Expected output: "starting timer..."

setTimeout(() => {
  const ms = Date.now() - start;

  console.log(`seconds elapsed = ${Math.floor(ms / 1000)}`);
  // Expected output: "seconds elapsed = 2"
}, 2000);
```

## نحو

```js-nolint
Date.now()
```

### پارامترها

این متد پارامتری نمی‌گیرد.

### مقدار بازگشتی

عددی که [مهر زمانی](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date#the_epoch_timestamps_and_invalid_date) زمان فعلی را برحسب میلی‌ثانیه نشان می‌دهد.

## توضیحات

### کاهش دقت زمان

برای محافظت در برابر حملات زمان‌سنجی و [اثر انگشت‌گیری](/en-US/docs/Glossary/Fingerprinting)، ممکن است دقت `Date.now()` بر اساس تنظیمات مرورگر گرد شود. در Firefox، گزینهٔ `privacy.reduceTimerPrecision` به‌طور پیش‌فرض فعال است و دقت را به ۲ میلی‌ثانیه محدود می‌کند. با فعال‌کردن `privacy.resistFingerprinting`، دقت به ۱۰۰ میلی‌ثانیه یا مقدار `privacy.resistFingerprinting.reduceTimerPrecision.microseconds` (هرکدام بزرگ‌تر باشد) کاهش می‌یابد.

برای مثال، با کاهش دقت، نتیجهٔ `Date.now()` همیشه مضربی از ۲ خواهد بود؛ و با فعال بودن `privacy.resistFingerprinting`، مضربی از ۱۰۰ یا مقدار `privacy.resistFingerprinting.reduceTimerPrecision.microseconds` خواهد بود.

```js
// reduced time precision (2ms) in Firefox 60
Date.now();
// Might be:
// 1519211809934
// 1519211810362
// 1519211811670
// …

// reduced time precision with `privacy.resistFingerprinting` enabled
Date.now();
// Might be:
// 1519129853500
// 1519129858900
// 1519129864400
// …
```

## مثال‌ها

### اندازه‌گیری زمان سپری‌شده

می‌توانید با `Date.now()` زمان فعلی را برحسب میلی‌ثانیه بگیرید و با کم‌کردن زمان قبلی، مدت سپری‌شده بین دو فراخوانی را محاسبه کنید.

```js
const start = Date.now();
doSomeLongRunningProcess();
console.log(`Time elapsed: ${Date.now() - start} ms`);
```

برای سناریوهای پیچیده‌تر، بهتر است از [Performance API](/en-US/docs/Web/API/Performance_API/High_precision_timing) استفاده کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Polyfill of `Date.now` in `core-js`](https://github.com/zloirock/core-js#ecmascript-date)
- {{domxref("Performance.now()")}}
- {{domxref("console/time_static", "console.time()")}}
- {{domxref("console/timeEnd_static", "console.timeEnd()")}}
