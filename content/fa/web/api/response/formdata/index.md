---
title: "Response: formData() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Response/formData"
---

---
title: "Response: formData() method"
short-title: formData()
slug: Web/API/Response/formData
page-type: web-api-instance-method
browser-compat: api.Response.formData
---

{{APIRef("Fetch API")}}{{AvailableInWorkers}}

متد **`formData()`** از رابط {{domxref("Response")}} جریان پاسخ را تا انتها می‌خواند و یک Promise برمی‌گرداند که با شیء {{domxref("FormData")}} تکمیل می‌شود.

> [!NOTE]
> این متد بیشتر در [Service Workerها](/en-US/docs/Web/API/Service_Worker_API) کاربرد دارد. برای مثال، اگر کاربر فرمی را ارسال کند و یک Service Worker درخواست را رهگیری کند، می‌توان با فراخوانی `formData()` یک نگاشت کلید-مقدار به دست آورد، برخی فیلدها را تغییر داد و سپس فرم را برای سرور فرستاد یا به‌صورت محلی استفاده کرد.

## نحو

```js-nolint
formData()
```

### پارامترها

این متد پارامتری نمی‌گیرد.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با شیء {{domxref("FormData")}} تکمیل می‌شود.

### خطاها

- `AbortError` {{domxref("DOMException")}}
  - : اگر درخواست لغو شده باشد، این خطا رخ می‌دهد. [توضیحات بیشتر](/en-US/docs/Web/API/Fetch_API/Using_Fetch#canceling_a_request)
- {{jsxref("TypeError")}}
  - : در هر یک از شرایط زیر رخ می‌دهد:
    - بدنهٔ پاسخ قبلاً خوانده شده یا قفل شده باشد ([توضیحات بیشتر](/en-US/docs/Web/API/Fetch_API/Using_Fetch#locked-and-disturbed-streams)).
    - هنگام رمزگشایی محتوای بدنه خطایی رخ دهد؛ برای مثال، مقدار سربرگ {{httpheader("Content-Encoding")}} نادرست باشد.
    - نوع {{glossary("MIME")}} بدنه از سربرگ {{httpheader("Content-Type")}} پاسخ قابل تشخیص نباشد یا با `application/x-www-form-urlencoded` و `multipart/form-data` مطابقت نداشته باشد.
    - نتوان بدنه را به‌عنوان شیء `FormData` تجزیه کرد.

## مثال‌ها

این بخش در مستندات اصلی هنوز مثالی ارائه نمی‌کند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [رابط Service Worker](/en-US/docs/Web/API/Service_Worker_API)
- [کنترل دسترسی بین‌مبدأ HTTP (CORS)](/en-US/docs/Web/HTTP/Guides/CORS)
- [HTTP](/en-US/docs/Web/HTTP)
