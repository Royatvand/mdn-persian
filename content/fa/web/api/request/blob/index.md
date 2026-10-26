---
title: "Request: blob() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Request/blob"
---

---
title: "Request: blob() method"
short-title: blob()
slug: Web/API/Request/blob
page-type: web-api-instance-method
browser-compat: api.Request.blob
---

{{APIRef("Fetch API")}}{{AvailableInWorkers}}

متد **`blob()`** از رابط {{domxref("Request")}} بدنهٔ درخواست را می‌خواند و یک Promise برمی‌گرداند که با یک شیء {{domxref("Blob")}} تکمیل می‌شود.

## نحو

```js-nolint
blob()
```

### پارامترها

این متد پارامتری نمی‌گیرد.

### مقدار بازگشتی

یک Promise که با شیء {{domxref("Blob")}} تکمیل می‌شود. دادهٔ این شیء از بایت‌های بدنه تشکیل شده و نوع رسانهٔ آن از مقدار سربرگ `Content-Type` درخواست گرفته می‌شود.

### خطاها

- {{jsxref("TypeError")}}
  - : در هر یک از شرایط زیر رخ می‌دهد:
    - بدنهٔ درخواست قبلاً خوانده شده یا قفل شده باشد ([توضیحات بیشتر](/en-US/docs/Web/API/Fetch_API/Using_Fetch#locked_and_disturbed_streams)).
    - هنگام رمزگشایی محتوای بدنه خطایی رخ دهد؛ برای مثال، مقدار سربرگ {{httpheader("Content-Encoding")}} نادرست باشد.

## مثال

```js
const obj = { hello: "world" };
const myBlob = new Blob([JSON.stringify(obj, null, 2)], {
  type: "application/json",
});

const request = new Request("/myEndpoint", {
  method: "POST",
  body: myBlob,
});

request.blob().then((myBlob) => {
  // با Blob ارسال‌شده در درخواست کاری انجام دهید
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("Response.blob()")}}
