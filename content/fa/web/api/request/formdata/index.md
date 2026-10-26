---
title: "Request: formData() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Request/formData"
---

---
title: "Request: formData() method"
short-title: formData()
slug: Web/API/Request/formData
page-type: web-api-instance-method
browser-compat: api.Request.formData
---

{{APIRef("Fetch API")}}{{AvailableInWorkers}}

متد **`formData()`** از رابط {{domxref("Request")}} بدنهٔ درخواست را می‌خواند و یک Promise برمی‌گرداند که با یک شیء {{domxref("FormData")}} تکمیل می‌شود.

## نحو

```js-nolint
formData()
```

### پارامترها

این متد پارامتری نمی‌گیرد.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با شیء {{domxref("FormData")}} تکمیل می‌شود.

### خطاها

- {{jsxref("TypeError")}}
  - : در هر یک از شرایط زیر رخ می‌دهد:
    - بدنهٔ درخواست قبلاً خوانده شده یا قفل شده باشد ([توضیحات بیشتر](/en-US/docs/Web/API/Fetch_API/Using_Fetch#locked-and-disturbed-streams)).
    - هنگام رمزگشایی محتوای بدنه خطایی رخ دهد؛ برای مثال، مقدار سربرگ {{httpheader("Content-Encoding")}} نادرست باشد.
    - نوع {{glossary("MIME")}} بدنه از سربرگ‌های {{httpheader("Content-Type")}} درخواست قابل تشخیص نباشد یا با `application/x-www-form-urlencoded` و `multipart/form-data` مطابقت نداشته باشد.
    - نتوان بدنه را به‌عنوان شیء `FormData` تجزیه کرد.

## مثال

```js
const formData = new FormData();
const fileField = document.querySelector('input[type="file"]');

formData.append("username", "abc123");
formData.append("avatar", fileField.files[0]);

const request = new Request("/myEndpoint", {
  method: "POST",
  body: formData,
});

request.formData().then((data) => {
  // داده‌های فرم ارسال‌شده در درخواست را پردازش کنید
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("Response.formData()")}}
