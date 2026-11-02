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

متد **`textStream()`** از رابط {{domxref("Response")}} یک {{domxref("ReadableStream")}} برمی‌گرداند که می‌توان از آن برای خواندن محتوای بدنهٔ پاسخ به‌صورت بخش‌های متنی با رمزگذاری UTF-8 استفاده کرد.

این روش نسبت به عبور دادن جریان بایتی {{domxref("Response.body")}} از طریق {{domxref("TextDecoderStream")}} راه ساده‌تری برای خواندن تدریجی بدنهٔ پاسخ فراهم می‌کند.

> [!NOTE]
> اگر بدنهٔ یک پاسخ تهی باشد، برای مثال در پاسخ با وضعیت {{httpstatus(204)}}، متد `textStream()` یک جریان معتبر اما خالی برمی‌گرداند.

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
  - : اگر بدنهٔ پاسخ قبلاً خوانده شده یا قفل شده باشد، این خطا رخ می‌دهد. [اطلاعات بیشتر](/en-US/docs/Web/API/Fetch_API/Using_Fetch#locked_and_disturbed_streams)

## مثال‌ها

### خواندن بدنهٔ پاسخ به‌صورت جریان متنی

در این مثال، یک URL را با {{domxref("fetch()")}} دریافت می‌کنیم، جریان قابل‌خواندن بدنهٔ پاسخ را با `textStream()` به دست می‌آوریم و سپس متن را با خواننده‌ای که از طریق {{domxref("ReadableStream.getReader()")}} ساخته شده است، می‌خوانیم.

```js
const pElem = document.querySelector("p");

async function streamResponseText(url) {
  const response = await fetch(url);
  const textStream = response.textStream();
  // به‌جای آن می‌توان از این روش استفاده کرد:
  // const textStream = response.body.pipeThrough(new TextDecoderStream());

  const reader = textStream.getReader();

  while (true) {
    const { value, done } = await reader.read();
    if (done) break;
    pElem.textContent += value;
  }
}

streamResponseText("https://www.example.com");
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("ReadableStream")}}
- {{domxref("ReadableStream.getReader()")}}
- {{domxref("Request.body")}}
- {{domxref("Request.textStream()")}}
