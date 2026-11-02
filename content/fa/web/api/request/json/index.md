---
title: "Request: json() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Request/json"
---

---
title: "Request: json() method"
short-title: json()
slug: Web/API/Request/json
page-type: web-api-instance-method
browser-compat: api.Request.json
---

{{APIRef("Fetch API")}}{{AvailableInWorkers}}

متد **`json()`** از رابط {{domxref("Request")}} بدنهٔ درخواست را می‌خواند و یک Promise برمی‌گرداند که با نتیجهٔ تجزیهٔ متن بدنه به‌عنوان {{JSxRef("JSON")}} تکمیل می‌شود.

با اینکه نام متد `json()` است، نتیجهٔ آن JSON خام نیست؛ بلکه مقدار جاوااسکریپتی حاصل از تجزیهٔ JSON است.

## نحو

```js-nolint
json()
```

### پارامترها

این متد پارامتری نمی‌گیرد.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با مقداری جاوااسکریپتی تکمیل می‌شود. این مقدار می‌تواند هر چیزی باشد که JSON نمایش می‌دهد؛ مانند شیء، آرایه، رشته یا عدد.

### خطاها

- {{jsxref("TypeError")}}
  - : در هر یک از شرایط زیر رخ می‌دهد:
    - بدنهٔ درخواست قبلاً خوانده شده یا قفل شده باشد ([توضیحات بیشتر](/en-US/docs/Web/API/Fetch_API/Using_Fetch#locked-and-disturbed-streams)).
    - هنگام رمزگشایی محتوای بدنه خطایی رخ دهد؛ برای مثال، مقدار سربرگ {{httpheader("Content-Encoding")}} نادرست باشد.
- {{jsxref("SyntaxError")}}
  - : اگر نتوان بدنهٔ درخواست را به‌عنوان JSON تجزیه کرد.

## مثال

```js
const obj = { hello: "world" };

const request = new Request("/myEndpoint", {
  method: "POST",
  body: JSON.stringify(obj),
});

request.json().then((data) => {
  // داده‌های ارسال‌شده در درخواست را پردازش کنید
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("Response.json()")}}
