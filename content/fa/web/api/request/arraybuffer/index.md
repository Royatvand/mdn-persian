---
title: "Request: arrayBuffer() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Request/arrayBuffer"
---

---
title: "Request: arrayBuffer() method"
short-title: arrayBuffer()
slug: Web/API/Request/arrayBuffer
page-type: web-api-instance-method
browser-compat: api.Request.arrayBuffer
---

{{APIRef("Fetch API")}}{{AvailableInWorkers}}

متد **`arrayBuffer()`** از رابط {{domxref("Request")}} بدنهٔ درخواست را می‌خواند و یک Promise برمی‌گرداند که با یک {{jsxref("ArrayBuffer")}} تکمیل می‌شود.

## نحو

```js-nolint
arrayBuffer()
```

### پارامترها

این متد پارامتری نمی‌گیرد.

### مقدار بازگشتی

یک Promise که با یک {{jsxref("ArrayBuffer")}} تکمیل می‌شود.

### خطاها

- {{jsxref("TypeError")}}
  - : در هر یک از شرایط زیر رخ می‌دهد:
    - بدنهٔ درخواست قبلاً خوانده شده یا قفل شده باشد ([توضیحات بیشتر](/en-US/docs/Web/API/Fetch_API/Using_Fetch#locked_and_disturbed_streams)).
    - هنگام رمزگشایی محتوای بدنه خطایی رخ دهد؛ برای مثال، مقدار سربرگ {{httpheader("Content-Encoding")}} نادرست باشد.
- {{jsxref("RangeError")}}
  - : اگر هنگام ایجاد `ArrayBuffer` مربوطه مشکلی رخ دهد، مثلاً اندازهٔ داده بیش از حد بزرگ باشد.

## مثال

```js
const myArray = new Uint8Array(10);

const request = new Request("/myEndpoint", {
  method: "POST",
  body: myArray,
});

request.arrayBuffer().then((buffer) => {
  // با بافر ارسال‌شده در درخواست کاری انجام دهید
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("Response.arrayBuffer()")}}
