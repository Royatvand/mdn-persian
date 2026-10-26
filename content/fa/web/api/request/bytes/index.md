---
title: "Request: bytes() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Request/bytes"
---

---
title: "Request: bytes() method"
short-title: bytes()
slug: Web/API/Request/bytes
page-type: web-api-instance-method
browser-compat: api.Request.bytes
---

{{APIRef("Fetch API")}}{{AvailableInWorkers}}

متد **`bytes()`** از رابط {{domxref("Request")}} بدنهٔ درخواست را می‌خواند و یک Promise برمی‌گرداند که با یک {{jsxref("Uint8Array")}} تکمیل می‌شود.

## نحو

```js-nolint
bytes()
```

### پارامترها

این متد پارامتری نمی‌گیرد.

### مقدار بازگشتی

یک Promise که با یک {{jsxref("Uint8Array")}} تکمیل می‌شود.

### خطاها

- {{jsxref("TypeError")}}
  - : در هر یک از شرایط زیر رخ می‌دهد:
    - بدنهٔ درخواست قبلاً خوانده شده یا قفل شده باشد ([توضیحات بیشتر](/en-US/docs/Web/API/Fetch_API/Using_Fetch#locked-and-disturbed-streams)).
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

request.bytes().then((buffer) => {
  // با بایت‌های ارسال‌شده در درخواست کاری انجام دهید
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("Response.arrayBuffer()")}}
