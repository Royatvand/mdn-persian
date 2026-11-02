---
title: "Response: blob() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Response/blob"
---

---
title: "Response: blob() method"
short-title: blob()
slug: Web/API/Response/blob
page-type: web-api-instance-method
browser-compat: api.Response.blob
---

{{APIRef("Fetch API")}}{{AvailableInWorkers}}

متد **`blob()`** از رابط {{domxref("Response")}} جریان پاسخ را تا انتها می‌خواند و یک Promise برمی‌گرداند که با یک شیء {{domxref("Blob")}} تکمیل می‌شود.

## نحو

```js-nolint
blob()
```

### پارامترها

این متد پارامتری نمی‌گیرد.

> [!NOTE]
> اگر مقدار {{domxref("Response.type")}} پاسخ برابر `"opaque"` باشد، شیء {{domxref("Blob")}} حاصل دارای {{domxref("Blob.size")}} برابر `0` و {{domxref("Blob.type")}} برابر رشتهٔ خالی `""` خواهد بود. در این حالت برای متدهایی مانند {{domxref("URL.createObjectURL_static", "URL.createObjectURL()")}} کاربردی نیست.

### مقدار بازگشتی

یک Promise که با شیء {{domxref("Blob")}} تکمیل می‌شود. دادهٔ این شیء از بایت‌های بدنه تشکیل شده و نوع رسانهٔ آن از مقدار سربرگ `Content-Type` پاسخ گرفته می‌شود.

### خطاها

- `AbortError` {{domxref("DOMException")}}
  - : اگر درخواست لغو شده باشد، این خطا رخ می‌دهد. [توضیحات بیشتر](/en-US/docs/Web/API/Fetch_API/Using_Fetch#canceling_a_request)
- {{jsxref("TypeError")}}
  - : در هر یک از شرایط زیر رخ می‌دهد:
    - بدنهٔ پاسخ قبلاً خوانده شده یا قفل شده باشد ([توضیحات بیشتر](/en-US/docs/Web/API/Fetch_API/Using_Fetch#locked-and-disturbed-streams)).
    - هنگام رمزگشایی محتوای بدنه خطایی رخ دهد؛ برای مثال، مقدار سربرگ {{httpheader("Content-Encoding")}} نادرست باشد.

## مثال

در [نمونهٔ دریافت درخواست](https://github.com/mdn/dom-examples/tree/main/fetch/fetch-request) می‌بینیم که چگونه با سازندهٔ {{domxref("Request.Request","Request()")}} درخواست جدیدی ایجاد کرده و یک تصویر JPG دریافت کنیم. پس از موفقیت درخواست، با `blob()` یک {{domxref("Blob")}} از پاسخ می‌خوانیم، برای آن یک نشانی شیء با {{domxref("URL.createObjectURL_static", "URL.createObjectURL()")}} می‌سازیم و آن نشانی را به‌عنوان منبع عنصر {{htmlelement("img")}} قرار می‌دهیم.

```js
const myImage = document.querySelector("img");

const myRequest = new Request("flowers.jpg");

fetch(myRequest)
  .then((response) => response.blob())
  .then((myBlob) => {
    const objectURL = URL.createObjectURL(myBlob);
    myImage.src = objectURL;
  });
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [رابط Service Worker](/en-US/docs/Web/API/Service_Worker_API)
- [کنترل دسترسی بین‌مبدأ HTTP (CORS)](/en-US/docs/Web/HTTP/Guides/CORS)
- [HTTP](/en-US/docs/Web/HTTP)
