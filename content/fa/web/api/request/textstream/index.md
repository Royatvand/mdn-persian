---
title: "Request: textStream() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Request/textStream"
---

---
title: "Request: textStream() method"
short-title: textStream()
slug: Web/API/Request/textStream
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.Request.textStream
---

{{APIRef("Fetch API")}}{{AvailableInWorkers}}{{SeeCompatTable}}

متد **`textStream()`** از رابط {{domxref("Request")}} یک {{domxref("ReadableStream")}} برمی‌گرداند که می‌توان از آن برای خواندن محتوای بدنهٔ درخواست به‌صورت بخش‌های متنی با رمزگذاری UTF-8 استفاده کرد.

این روش نسبت به عبور دادن جریان بایتی {{domxref("Request.body")}} از طریق {{domxref("TextDecoderStream")}} راه ساده‌تری برای خواندن تدریجی بدنهٔ درخواست فراهم می‌کند.

> [!NOTE]
> اگر بدنهٔ یک درخواست تهی باشد، برای مثال در یک درخواست {{httpmethod("GET")}}، متد `textStream()` یک جریان معتبر اما خالی برمی‌گرداند.

## نحو

```js-nolint
textStream()
```

### پارامترها

این متد پارامتری نمی‌گیرد.

### مقدار بازگشتی

یک {{domxref("ReadableStream")}}.

### خطاها

- {{jsxref("TypeError")}}
  - : اگر بدنهٔ درخواست قبلاً خوانده شده یا قفل شده باشد، این خطا رخ می‌دهد. [اطلاعات بیشتر](/en-US/docs/Web/API/Fetch_API/Using_Fetch#locked_and_disturbed_streams)

## مثال‌ها

### خواندن بدنهٔ درخواست به‌صورت جریان متنی

در این مثال یک شیء `Request` می‌سازیم، جریان قابل‌خواندن بدنه را با `textStream()` دریافت می‌کنیم و سپس متن را با خواننده‌ای که از طریق {{domxref("ReadableStream.getReader()")}} ساخته شده است، می‌خوانیم.

```js
const pElem = document.querySelector("p");

const req = new Request("https://example.com", {
  method: "POST",
  body: '{"hello": "world"}',
});

async function streamRequestText(request) {
  const textStream = request.textStream();
  // به‌جای آن می‌توان از این روش استفاده کرد:
  // const textStream = request.body.pipeThrough(new TextDecoderStream());

  const reader = textStream.getReader();

  while (true) {
    const { value, done } = await reader.read();
    if (done) break;
    pElem.textContent += value;
  }
}

streamRequestText(req);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("ReadableStream")}}
- {{domxref("ReadableStream.getReader()")}}
- {{domxref("Response.body")}}
- {{domxref("Response.textStream()")}}
