---
title: "Request: clone() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Request/clone"
---

---
title: "Request: clone() method"
short-title: clone()
slug: Web/API/Request/clone
page-type: web-api-instance-method
browser-compat: api.Request.clone
---

{{APIRef("Fetch API")}}{{AvailableInWorkers}}

متد **`clone()`** از رابط {{domxref("Request")}} یک کپی از شیء فعلی `Request` ایجاد می‌کند.

مانند API زیرین {{domxref("ReadableStream.tee")}}، بدنهٔ {{domxref("Request.body", "body")}} در درخواست کپی‌شده، فشار برگشتی (backpressure) را با سرعت مصرف‌کنندهٔ سریع‌تر از میان دو مصرف‌کننده هماهنگ می‌کند. داده‌هایی که مصرف‌کنندهٔ کندتر هنوز نخوانده است، بدون محدودیت یا فشار برگشتی در صف داخلی نگه داشته می‌شوند. هنگام ساختن یک `Request` از جریان و سپس کپی‌کردن آن با `clone()` مراقب این موضوع باشید.

اگر بدنهٔ درخواست قبلاً استفاده شده باشد، `clone()` خطای {{jsxref("TypeError")}} ایجاد می‌کند. دلیل اصلی وجود این متد، امکان استفادهٔ چندباره از بدنه‌هایی است که فقط یک بار قابل مصرف‌اند.

اگر قصد دارید درخواست را تغییر دهید، ممکن است استفاده از سازندهٔ {{domxref("Request")}} مناسب‌تر باشد.

## نحو

```js-nolint
clone()
```

### پارامترها

این متد پارامتری نمی‌گیرد.

### مقدار بازگشتی

یک شیء {{domxref("Request")}} که کپی دقیقی از درخواستی است که متد `clone()` روی آن فراخوانی شده است.

## مثال

در نمونهٔ زیر با سازندهٔ {{domxref("Request.Request", "Request()")}} درخواستی برای یک فایل تصویری در همان پوشهٔ اسکریپت ایجاد می‌کنیم و سپس آن را کپی می‌کنیم.

```js
const myRequest = new Request("flowers.jpg");
const newRequest = myRequest.clone(); // اکنون کپی درخواست در newRequest ذخیره شده است
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [رابط Service Worker](/en-US/docs/Web/API/Service_Worker_API)
- [کنترل دسترسی بین‌مبدأ HTTP (CORS)](/en-US/docs/Web/HTTP/Guides/CORS)
- [HTTP](/en-US/docs/Web/HTTP)
