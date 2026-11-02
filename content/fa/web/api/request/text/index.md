---
title: "Request: text() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Request/text"
---

---
title: "Request: text() method"
short-title: text()
slug: Web/API/Request/text
page-type: web-api-instance-method
browser-compat: api.Request.text
---

{{APIRef("Fetch API")}}{{AvailableInWorkers}}

متد **`text()`** از رابط {{domxref("Request")}} بدنهٔ درخواست را می‌خواند و یک Promise برمی‌گرداند که با یک {{jsxref("String", "رشته")}} تکمیل می‌شود. محتوای بدنه همیشه با رمزگذاری UTF-8 رمزگشایی می‌شود.

## نحو

```js-nolint
text()
```

### پارامترها

این متد پارامتری نمی‌گیرد.

### مقدار بازگشتی

یک Promise که با یک رشته تکمیل می‌شود.

### خطاها

- {{jsxref("TypeError")}}
  - : در هر یک از شرایط زیر رخ می‌دهد:
    - بدنهٔ درخواست قبلاً خوانده شده یا قفل شده باشد ([توضیحات بیشتر](/en-US/docs/Web/API/Fetch_API/Using_Fetch#locked_and_disturbed_streams)).
    - هنگام رمزگشایی محتوای بدنه خطایی رخ دهد؛ برای مثال، مقدار سربرگ {{httpheader("Content-Encoding")}} نادرست باشد.

## مثال

```js
const text = "Hello world";

const request = new Request("/myEndpoint", {
  method: "POST",
  body: text,
});

request.text().then((text) => {
  // متن ارسال‌شده در درخواست را پردازش کنید
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("Response.text()")}}
