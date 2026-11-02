---
title: "Promise.resolve()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/resolve"
---

---
title: Promise.resolve()
short-title: resolve()
slug: Web/JavaScript/Reference/Global_Objects/Promise/resolve
page-type: javascript-static-method
browser-compat: javascript.builtins.Promise.resolve
sidebar: jsref
---

متد ایستای **`Promise.resolve()`** مقدار داده‌شده را به یک {{jsxref("Promise")}} تبدیل و آن را resolve می‌کند. اگر مقدار خود Promise باشد، همان Promise برگردانده می‌شود؛ اگر [thenable](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise#thenables) باشد، `Promise.resolve()` متد `then()` آن را با دو callback آماده‌شده فراخوانی می‌کند؛ در غیر این صورت Promise برگشتی با همان مقدار fulfilled می‌شود.

این تابع لایه‌های تو‌در‌توی اشیای شبیه Promise را به یک لایه تبدیل می‌کند؛ برای مثال، اگر Promise با Promise دیگری تکمیل شود، نتیجه در نهایت Promiseای خواهد بود که با مقداری غیر thenable تکمیل می‌شود.

{{InteractiveExample("JavaScript Demo: Promise.resolve()")}}

```js interactive-example
const promise1 = Promise.resolve(123);

promise1.then((value) => {
  console.log(value);
  // Expected output: 123
});
```

## نحو

```js-nolint
Promise.resolve(value)
```

### پارامترها

- `value`
  - : مقداری که باید توسط این `Promise` resolve شود. این مقدار می‌تواند خود یک `Promise` یا thenable نیز باشد.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با مقدار داده‌شده resolve می‌شود؛ اگر مقدار ورودی شیء Promise باشد، همان Promise برگردانده می‌شود. Promiseای که resolve شده، می‌تواند در هر یک از وضعیت‌های fulfilled، rejected یا pending باشد. برای مثال، resolve کردن یک Promise ردشده همچنان به Promise ردشده منجر می‌شود.

## توضیحات

`Promise.resolve()` یک Promise را _resolve_ می‌کند؛ این با fulfilled یا rejected شدن آن یکسان نیست. برای تعریف این اصطلاحات، توضیحات [Promise](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise#description) را ببینید. به‌طور خلاصه، `Promise.resolve()` پرامیزی برمی‌گرداند که وضعیت نهایی آن به Promise دیگر، شیء thenable یا مقدار دیگری بستگی دارد.

> [!NOTE]
> اگر ارزیابی عبارت `value` ممکن است به‌صورت هم‌زمان خطا پرتاب کند، `Promise.resolve()` آن خطا را نمی‌گیرد و در Promise ردشده قرار نمی‌دهد. در این حالت استفاده از {{jsxref("Promise/try", "Promise.try(() => value)")}} را در نظر بگیرید.

`Promise.resolve()` عمومی است و از زیرکلاس‌سازی پشتیبانی می‌کند؛ بنابراین می‌توان آن را روی زیرکلاس‌های `Promise` فراخوانی کرد و نتیجه از نوع همان زیرکلاس خواهد بود. برای این کار، سازندهٔ زیرکلاس باید امضایی مشابه سازندهٔ [`Promise()`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/Promise) داشته باشد و یک تابع `executor` بپذیرد که callbackهای `resolve` و `reject` به آن داده می‌شوند.

`Promise.resolve()` با نمونه‌های بومی `Promise` رفتار ویژه‌ای دارد. اگر `value` از نوع `Promise` باشد و `value.constructor === Promise`، همان `value` مستقیماً برگردانده می‌شود و نمونهٔ جدیدی ساخته نمی‌شود. در غیر این صورت، `Promise.resolve()` تقریباً شکل کوتاه‌شدهٔ `new Promise((resolve) => resolve(value))` است.

بخش اصلی منطق resolve در واقع توسط [تابع `resolve`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/Promise#the_resolve_function) پیاده‌سازی می‌شود که سازندهٔ `Promise()` آن را ارسال می‌کند. خلاصهٔ رفتار:

- اگر مقدار ورودی [thenable](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise#thenables) نباشد، Promise برگشتی از همان ابتدا با آن مقدار fulfilled است.
- اگر thenable داده شود، Promise برگشتی با فراخوانی متد `then` و ارسال دو تابع resolveکننده، وضعیت آن را می‌پذیرد. (اما چون Promiseهای بومی بدون ساخت wrapper از `Promise.resolve()` عبور می‌کنند، متد `then` روی آن‌ها فراخوانی نمی‌شود.) اگر تابع `resolve` thenable دیگری دریافت کند، آن را نیز resolve می‌کند؛ بنابراین مقدار نهایی Promise دیگر thenable نخواهد بود.

## مثال‌ها

### استفاده از متد ایستای Promise.resolve

```js
Promise.resolve("Success").then(
  (value) => {
    console.log(value); // "Success"
  },
  (reason) => {
    // not called
  },
);
```

### resolve کردن یک آرایه

```js
const p = Promise.resolve([1, 2, 3]);
p.then((v) => {
  console.log(v[0]); // 1
});
```

### resolve کردن یک Promise دیگر

`Promise.resolve()` نمونه‌های موجود `Promise` را دوباره استفاده می‌کند. اگر Promise بومی را resolve کند، همان نمونه را بدون ساخت wrapper برمی‌گرداند.

```js
const original = Promise.resolve(33);
const cast = Promise.resolve(original);
cast.then((value) => {
  console.log(`value: ${value}`);
});
console.log(`original === cast ? ${original === cast}`);

// Logs, in order:
// original === cast ? true
// value: 33
```

ترتیب معکوس خروجی‌ها به این دلیل است که handlerهای `then` به‌صورت ناهمگام فراخوانی می‌شوند. برای اطلاعات بیشتر، مرجع {{jsxref("Promise/then", "then()")}} را ببینید.

### resolve کردن thenableها و پرتاب خطا

```js
// Resolving a thenable object
const p1 = Promise.resolve({
  then(onFulfill, onReject) {
    onFulfill("fulfilled!");
  },
});
console.log(p1 instanceof Promise); // true, object casted to a Promise

p1.then(
  (v) => {
    console.log(v); // "fulfilled!"
  },
  (e) => {
    // not called
  },
);

// Thenable throws
// Promise rejects
const p2 = Promise.resolve({
  then() {
    throw new TypeError("Throwing");
  },
});
p2.then(
  (v) => {
    // not called
  },
  (e) => {
    console.error(e); // TypeError: Throwing
  },
);

// Thenable throws after callback
// Promise resolves
const p3 = Promise.resolve({
  then(onFulfilled) {
    onFulfilled("Resolving");
    throw new TypeError("Throwing");
  },
});
p3.then(
  (v) => {
    console.log(v); // "Resolving"
  },
  (e) => {
    // not called
  },
);
```

thenableهای تو‌در‌تو به‌صورت عمیق در یک Promise واحد ادغام می‌شوند.

```js
const thenable = {
  then(onFulfilled, onRejected) {
    onFulfilled({
      // The thenable is fulfilled with another thenable
      then(onFulfilled, onRejected) {
        onFulfilled(42);
      },
    });
  },
};

Promise.resolve(thenable).then((v) => {
  console.log(v); // 42
});
```

> [!WARNING]
> روی thenableای که خودش را resolve می‌کند، `Promise.resolve()` را فراخوانی نکنید. این کار به بازگشت بی‌نهایت منجر می‌شود، زیرا تلاش می‌کند Promiseای با تو‌در‌تویی بی‌نهایت را تخت کند.

```js example-bad
const thenable = {
  then(onFulfilled, onRejected) {
    onFulfilled(thenable);
  },
};

Promise.resolve(thenable); // Will lead to infinite recursion.
```

### فراخوانی resolve() روی سازنده‌ای غیر از Promise

`Promise.resolve()` متدی عمومی است و می‌توان آن را روی هر سازنده‌ای فراخوانی کرد که امضایی مشابه سازندهٔ `Promise()` داشته باشد. برای مثال، می‌توان آن را روی سازنده‌ای اجرا کرد که `console.log` را به‌عنوان تابع `resolve` دریافت می‌کند:

```js
class NotPromise {
  constructor(executor) {
    // The "resolve" and "reject" functions behave nothing like the
    // native promise's, but Promise.resolve() calls them in the same way.
    executor(
      (value) => console.log("Resolved", value),
      (reason) => console.log("Rejected", reason),
    );
  }
}

Promise.resolve.call(NotPromise, "foo"); // Logs "Resolved foo"
```

قابلیت تخت‌کردن thenableهای تو‌در‌تو در تابع `resolve` سازندهٔ `Promise()` پیاده‌سازی شده است؛ بنابراین اگر این متد را روی سازندهٔ دیگری فراخوانی کنید، بسته به پیاده‌سازی تابع `resolve` آن سازنده، ممکن است thenableهای تو‌در‌تو تخت نشوند.

```js
const thenable = {
  then(onFulfilled, onRejected) {
    onFulfilled({
      // The thenable is fulfilled with another thenable
      then(onFulfilled, onRejected) {
        onFulfilled(42);
      },
    });
  },
};

Promise.resolve.call(NotPromise, thenable); // Logs "Resolved { then: [Function: then] }"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{jsxref("Promise")}}
