---
title: "Response: arrayBuffer() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Response/arrayBuffer"
---

---
title: "Response: arrayBuffer() method"
short-title: arrayBuffer()
slug: Web/API/Response/arrayBuffer
page-type: web-api-instance-method
browser-compat: api.Response.arrayBuffer
---

{{APIRef("Fetch API")}}{{AvailableInWorkers}}

متد **`arrayBuffer()`** از رابط {{domxref("Response")}} جریان پاسخ را تا انتها می‌خواند و یک Promise برمی‌گرداند که با یک {{jsxref("ArrayBuffer")}} تکمیل می‌شود.

## نحو

```js-nolint
arrayBuffer()
```

### پارامترها

این متد پارامتری نمی‌گیرد.

### مقدار بازگشتی

یک Promise که با یک {{jsxref("ArrayBuffer")}} تکمیل می‌شود.

### خطاها

- `AbortError` {{domxref("DOMException")}}
  - : اگر درخواست لغو شده باشد، این خطا رخ می‌دهد. [توضیحات بیشتر](/en-US/docs/Web/API/Fetch_API/Using_Fetch#canceling_a_request)
- {{jsxref("TypeError")}}
  - : در هر یک از شرایط زیر رخ می‌دهد:
    - بدنهٔ پاسخ قبلاً خوانده شده یا قفل شده باشد ([توضیحات بیشتر](/en-US/docs/Web/API/Fetch_API/Using_Fetch#locked-and-disturbed-streams)).
    - هنگام رمزگشایی محتوای بدنه خطایی رخ دهد؛ برای مثال، مقدار سربرگ {{httpheader("Content-Encoding")}} نادرست باشد.
- {{jsxref("RangeError")}}
  - : اگر هنگام ایجاد `ArrayBuffer` مربوطه مشکلی رخ دهد، مثلاً اندازهٔ داده بیش از حد بزرگ باشد.

## مثال‌ها

### پخش موسیقی

در [نمونهٔ زندهٔ دریافت ArrayBuffer](https://github.com/mdn/dom-examples/tree/main/fetch/fetch-array-buffer) یک دکمهٔ پخش وجود دارد. با فشردن آن، تابع `getData()` اجرا می‌شود. توجه کنید که پیش از پخش، کل فایل صوتی دانلود می‌شود. اگر می‌خواهید فایل OGG هنگام دانلود پخش شود، می‌توانید از {{domxref("HTMLAudioElement")}} استفاده کنید:

```js
new Audio("music.ogg").play();
```

در تابع `getData()` با سازندهٔ {{domxref("Request.Request","Request()")}} درخواست جدیدی می‌سازیم و فایل موسیقی OGG را دریافت می‌کنیم. سپس با {{domxref("BaseAudioContext/createBufferSource", "AudioContext.createBufferSource")}} منبع بافر صوتی می‌سازیم. پس از موفقیت درخواست، با `arrayBuffer()` یک {{jsxref("ArrayBuffer")}} از پاسخ می‌خوانیم، دادهٔ صوتی را با {{domxref("BaseAudioContext/decodeAudioData", "AudioContext.decodeAudioData()")}} رمزگشایی می‌کنیم، دادهٔ رمزگشایی‌شده را در بافر منبع قرار می‌دهیم و منبع را به {{domxref("BaseAudioContext/destination", "AudioContext.destination")}} متصل می‌کنیم.

پس از پایان اجرای `getData()`، پخش صدا با `start(0)` آغاز می‌شود و دکمهٔ پخش غیرفعال می‌شود تا دوباره کلیک نشود و خطایی رخ ندهد.

```js
function getData() {
  const audioCtx = new AudioContext();

  return fetch("viper.ogg")
    .then((response) => {
      if (!response.ok) {
        throw new Error(`HTTP error, status = ${response.status}`);
      }
      return response.arrayBuffer();
    })
    .then((buffer) => audioCtx.decodeAudioData(buffer))
    .then((decodedData) => {
      const source = new AudioBufferSourceNode(audioCtx);
      source.buffer = decodedData;
      source.connect(audioCtx.destination);
      return source;
    });
}

// اتصال رویدادهای دکمه‌های توقف و پخش

play.onclick = () => {
  getData().then((source) => {
    source.start(0);
    play.setAttribute("disabled", "disabled");
  });
};
```

### خواندن فایل‌ها

سازندهٔ {{domxref("Response.Response","Response()")}} فایل‌های {{domxref("File")}} و {{domxref("Blob")}} را می‌پذیرد؛ بنابراین می‌توان از آن برای خواندن یک فایل در قالب‌های دیگر استفاده کرد.

```html
<input type="file" />
```

```js
function readFile(file) {
  return new Response(file).arrayBuffer();
}

document
  .querySelector("input[type=file]")
  .addEventListener("change", (event) => {
    const file = event.target.files[0];
    const buffer = readFile(file);
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
