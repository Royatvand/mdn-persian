---
title: "Promise.reject()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/reject"
---

---
title: Promise.reject()
short-title: reject()
slug: Web/JavaScript/Reference/Global_Objects/Promise/reject
page-type: javascript-static-method
browser-compat: javascript.builtins.Promise.reject
sidebar: jsref
---

متد ایستای **`Promise.reject()`** یک شیء `Promise` برمی‌گرداند که به‌دلیل مشخص‌شده رد شده است.

{{InteractiveExample("JavaScript Demo: Promise.reject()")}}

```js interactive-example
function resolved(result) {
  console.log("Resolved");
}

function rejected(result) {
  console.error(result);
}

Promise.reject(new Error("fail")).then(resolved, rejected);
// Expected output: Error: fail
```

## نحو

```js-nolint
Promise.reject(reason)
```

### پارامترها

- `reason`
  - : دلیل رد شدن این `Promise`.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با دلیل داده‌شده رد می‌شود.

## توضیحات

تابع ایستای `Promise.reject()` یک Promise ردشده برمی‌گرداند. برای اشکال‌زدایی و گرفتن انتخابی خطاها، بهتر است `reason` نمونه‌ای از {{jsxref("Error")}} باشد.

`Promise.reject()` متدی عمومی است و از زیرکلاس‌سازی پشتیبانی می‌کند؛ بنابراین می‌توان آن را روی زیرکلاس‌های `Promise` فراخوانی کرد و نتیجه از نوع همان زیرکلاس خواهد بود. سازندهٔ زیرکلاس باید امضایی مانند سازندهٔ [`Promise()`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/Promise) داشته باشد و تابع `executor`ای بپذیرد که callbackهای `resolve` و `reject` به آن ارسال می‌شوند. در اصل، `Promise.reject()` شکل کوتاه‌شدهٔ `new Promise((resolve, reject) => reject(reason))` است.

برخلاف {{jsxref("Promise.resolve()")}}، متد `Promise.reject()` همیشه `reason` را در یک شیء `Promise` جدید قرار می‌دهد؛ حتی اگر خود `reason` از قبل Promise باشد.

## مثال‌ها

### استفاده از متد ایستای Promise.reject()

```js
Promise.reject(new Error("fail")).then(
  () => {
    // not called
  },
  (error) => {
    console.error(error); // Stacktrace
  },
);
```

### رد کردن با یک Promise

برخلاف {{jsxref("Promise.resolve")}}، متد `Promise.reject()` نمونه‌های موجود `Promise` را دوباره استفاده نمی‌کند؛ همیشه نمونه‌ای جدید برمی‌گرداند که `reason` را در خود نگه می‌دارد.

```js
const p = Promise.resolve(1);
const rejected = Promise.reject(p);
console.log(rejected === p); // false
rejected.catch((v) => {
  console.log(v === p); // true
});
```

### فراخوانی reject() روی سازنده‌ای غیر از Promise

`Promise.reject()` متدی عمومی است و می‌توان آن را روی هر سازنده‌ای با امضایی مشابه سازندهٔ `Promise()` فراخوانی کرد. برای نمونه، می‌توان از سازنده‌ای استفاده کرد که `console.log` را به‌عنوان تابع `reject` به آن می‌دهد:

```js
class NotPromise {
  constructor(executor) {
    // The "resolve" and "reject" functions behave nothing like the
    // native promise's, but Promise.reject() calls them in the same way.
    executor(
      (value) => console.log("Resolved", value),
      (reason) => console.log("Rejected", reason),
    );
  }
}

Promise.reject.call(NotPromise, "foo"); // Logs "Rejected foo"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{jsxref("Promise")}}
