---
title: "Response: bytes() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Response/bytes"
---

---
title: "Response: bytes() method"
short-title: bytes()
slug: Web/API/Response/bytes
page-type: web-api-instance-method
browser-compat: api.Response.bytes
---

{{APIRef("Fetch API")}}{{AvailableInWorkers}}

متد **`bytes()`** از رابط {{domxref("Response")}} جریان پاسخ را تا انتها می‌خواند و یک Promise برمی‌گرداند که با یک {{jsxref("Uint8Array")}} تکمیل می‌شود.

## نحو

```js-nolint
bytes()
```

### پارامترها

این متد پارامتری نمی‌گیرد.

### مقدار بازگشتی

یک Promise که با یک {{jsxref("Uint8Array")}} تکمیل می‌شود.

### خطاها

- `AbortError` {{domxref("DOMException")}}
  - : اگر درخواست لغو شده باشد، این خطا رخ می‌دهد. [توضیحات بیشتر](/en-US/docs/Web/API/Fetch_API/Using_Fetch#canceling_a_request)
- {{jsxref("TypeError")}}
  - : اگر بدنهٔ پاسخ قبلاً خوانده شده یا قفل شده باشد، یا هنگام رمزگشایی محتوای بدنه خطایی رخ دهد (برای مثال، سربرگ {{httpheader("Content-Encoding")}} نادرست باشد).
- {{jsxref("RangeError")}}
  - : اگر هنگام ایجاد `ArrayBuffer` مربوطه مشکلی رخ دهد، مثلاً اندازهٔ داده بیش از حد بزرگ باشد.

## مثال‌ها

### دریافت و رمزگشایی یک فایل

کد زیر یک فایل متنی را دریافت می‌کند، بدنهٔ آن را به‌صورت {{jsxref("Uint8Array")}} برمی‌گرداند و سپس آن را به رشته تبدیل می‌کند.

```js
const response = await fetch("https://www.example.com/textfile.txt");
const textFile = await response.bytes();
const string = new TextDecoder().decode(textFile);
console.log(string);
```

### تشخیص امضای فایل تصویر

در این مثال از `bytes()` برای خواندن بایت‌های ابتدایی چند تصویر و تشخیص نوع فایل استفاده می‌کنیم.

#### HTML

ابتدا یک عنصر {{htmlelement("select")}} برای انتخاب نوع فایل تعریف می‌کنیم. مقدار هر گزینه، نشانی فایل مربوطه در Wikimedia Commons است.

```html
<label for="file-select">Choose a file:</label>

<select name="Files" id="file-select">
  <option value="">--Select an image type--</option>
  <option
    value="https://upload.wikimedia.org/wikipedia/commons/7/70/Example.png">
    PNG
  </option>
  <option
    value="https://upload.wikimedia.org/wikipedia/commons/a/a9/Example.jpg">
    JPG
  </option>
  <option
    value="https://upload.wikimedia.org/wikipedia/commons/8/8f/Example.gif">
    GIF89a
  </option>
</select>
```

```html hidden
<pre id="log"></pre>
```

```css hidden
#log {
  height: 100px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

#### JavaScript

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

ابتدا بررسی می‌کنیم که آیا متد `bytes()` پشتیبانی می‌شود یا نه. در صورت پشتیبانی، برای رویداد [`change`](/en-US/docs/Web/API/HTMLElement/change_event) عنصر انتخاب، شنونده‌ای اضافه می‌کنیم. با تغییر گزینه، نشانی فایل تصویر به تابع `checkSignature()` فرستاده می‌شود؛ در غیر این صورت، پیام مناسبی ثبت می‌شود.

```js
if ("bytes" in Response.prototype) {
  const selectFileElement = document.getElementById("file-select");
  selectFileElement.addEventListener("change", (event) => {
    try {
      checkSignature(event.target.value);
    } catch (e) {
      log(e);
    }
  });
} else {
  log("Response.bytes() not supported");
}
```

تابع `checkSignature()` فایل را از نشانی مشخص‌شده دریافت می‌کند و با `response.bytes()` محتوای آن را به آرایه‌ای از بایت‌ها تبدیل می‌کند. سپس بایت‌های ابتدایی با امضای شناخته‌شدهٔ چند قالب تصویر مقایسه می‌شوند و نام فایل و نوع آن در خروجی ثبت می‌شود.

```js
async function checkSignature(url) {
  if (url === "") return;
  log(`File: ${url}`);
  const response = await fetch(url);
  const image = await response.bytes();

  // امضاهای فایل از: https://en.wikipedia.org/wiki/List_of_file_signatures
  const jpgSignature = [0xff, 0xd8, 0xff, 0xe0];
  const pngSignature = [0x89, 0x50, 0x4e, 0x47, 0x0d, 0x0a, 0x1a, 0x0a];
  const gif89aSignature = [0x47, 0x49, 0x46, 0x38, 0x39, 0x61];

  if (
    image
      .slice(0, jpgSignature.length)
      .every((byte, index) => byte === jpgSignature[index])
  ) {
    log(`JPG signature: FF D8 FF E0`);
  } else if (
    image
      .slice(0, pngSignature.length)
      .every((byte, index) => byte === pngSignature[index])
  ) {
    log(`PNG signature: 89 50 4E 47 0D 0A 1A 0A`);
  } else if (
    image
      .slice(0, gif89aSignature.length)
      .every((byte, index) => byte === gif89aSignature[index])
  ) {
    log(`GIF (GIF89a) signature: 47 49 46 38 39 61`);
  } else {
    log("Unknown format");
  }
}
```

#### نتیجه

با انتخاب نوع تصویر از فهرست، خروجی باید نام فایل و نوع تشخیص‌داده‌شده بر اساس امضای آن را نمایش دهد.

{{EmbedLiveSample("Getting an image file signature", "100", "200px")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [رابط Service Worker](/en-US/docs/Web/API/Service_Worker_API)
- [کنترل دسترسی بین‌مبدأ HTTP (CORS)](/en-US/docs/Web/HTTP/Guides/CORS)
- [HTTP](/en-US/docs/Web/HTTP)
