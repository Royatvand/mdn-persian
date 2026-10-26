---
title: "Response: textStream() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Response/textStream"
---

---
title: "Response: textStream() method"
short-title: textStream()
slug: Web/API/Response/textStream
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.Response.textStream
---

{{APIRef("Fetch API")}}{{AvailableInWorkers}}{{SeeCompatTable}}

متد **`textStream()`** از رابط {{domxref("Response")}} یک {{domxref("ReadableStream")}} برمی‌گرداند که برای خواندن بدنهٔ پاسخ به‌صورت بخش‌های متنی با رمزگذاری UTF-8 به کار می‌رود.

این متد امکان پردازش تدریجی متن پاسخ را فراهم می‌کند؛ بنابراین لازم نیست پیش از دسترسی به متن، تمام بدنهٔ پاسخ خوانده شود.

## نحو

```js-nolint
textStream()
```

### پارامترها

این متد پارامتری نمی‌گیرد.

### مقدار بازگشتی

یک {{domxref("ReadableStream")}} که متن پاسخ را به‌صورت بخش‌های متوالی در اختیار می‌گذارد.

### خطاها

- {{jsxref("TypeError")}}
  - : اگر بدنهٔ پاسخ قبلاً خوانده شده یا قفل شده باشد، این خطا رخ می‌دهد.

## مثال‌ها

### خواندن پاسخ به‌صورت جریان متنی

در این مثال، متن پاسخ را به‌تدریج می‌خوانیم و هر بخش دریافت‌شده را به عنصر صفحه اضافه می‌کنیم.

```js
const output = document.querySelector("pre");

async function readResponseText(url) {
  const response = await fetch(url);
  const reader = response.textStream().getReader();

  while (true) {
    const { value, done } = await reader.read();
    if (done) break;
    output.textContent += value;
  }
}

readResponseText("https://example.com");
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("Request.textStream()")}}
- {{domxref("Response.body")}}
- {{domxref("ReadableStream.getReader()")}}
