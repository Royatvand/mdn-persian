---
title: "Response: text() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Response/text"
---

---
title: "Response: text() method"
short-title: text()
slug: Web/API/Response/text
page-type: web-api-instance-method
browser-compat: api.Response.text
---

{{APIRef("Fetch API")}}{{AvailableInWorkers}}

متد **`text()`** از رابط {{domxref("Response")}} جریان بدنهٔ پاسخ را تا انتها می‌خواند و یک Promise برمی‌گرداند که با یک {{jsxref("String", "رشته")}} تکمیل می‌شود. محتوای پاسخ همیشه با رمزگذاری UTF-8 رمزگشایی می‌شود.

## نحو

```js-nolint
text()
```

### پارامترها

این متد پارامتری نمی‌گیرد.

### مقدار بازگشتی

یک Promise که با یک رشته تکمیل می‌شود.

### خطاها

- `AbortError` {{domxref("DOMException")}}
  - : اگر درخواست لغو شده باشد، این خطا رخ می‌دهد. [اطلاعات بیشتر](/en-US/docs/Web/API/Fetch_API/Using_Fetch#canceling_a_request)
- {{jsxref("TypeError")}}
  - : در هر یک از شرایط زیر رخ می‌دهد:
    - بدنهٔ پاسخ قبلاً خوانده شده یا قفل شده باشد ([توضیحات بیشتر](/en-US/docs/Web/API/Fetch_API/Using_Fetch#locked_and_disturbed_streams)).
    - هنگام رمزگشایی محتوای بدنه خطایی رخ دهد؛ برای مثال، مقدار سربرگ {{httpheader("Content-Encoding")}} نادرست باشد.

## مثال

در [نمونهٔ دریافت متن](https://github.com/mdn/dom-examples/tree/main/fetch/fetch-text) می‌بینیم که چگونه محتوای یک فایل متنی را دریافت کرده و در عنصر `article` نمایش دهیم. ابتدا برای پیوندهای صفحه شنوندهٔ رویداد کلیک تنظیم می‌کنیم. هنگام کلیک، تابع `getData()` شناسهٔ صفحه را دریافت می‌کند، یک درخواست می‌سازد و فایل متنی مربوط را دریافت می‌کند. پس از موفقیت درخواست، با استفاده از `text()` متن پاسخ خوانده شده و در عنصر `article` قرار می‌گیرد.

```js
const myArticle = document.querySelector("article");
const myLinks = document.querySelectorAll("ul a");

for (const link of myLinks) {
  link.onclick = (e) => {
    e.preventDefault();
    const linkData = e.target.getAttribute("data-page");
    getData(linkData);
  };
}

function getData(pageId) {
  console.log(pageId);
  const myRequest = new Request(`${pageId}.txt`);
  fetch(myRequest)
    .then((response) => {
      if (!response.ok) {
        throw new Error(`HTTP error, status = ${response.status}`);
      }
      return response.text();
    })
    .then((text) => {
      myArticle.innerText = text;
    })
    .catch((error) => {
      myArticle.innerText = `Error: ${error.message}`;
    });
}
```

برای اجرای زندهٔ نمونه می‌توانید از [نسخهٔ قابل اجرا](https://mdn.github.io/dom-examples/fetch/fetch-text/) استفاده کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [رابط برنامه‌نویسی Service Worker](/en-US/docs/Web/API/Service_Worker_API)
- [کنترل دسترسی HTTP (CORS)](/en-US/docs/Web/HTTP/Guides/CORS)
- [HTTP](/en-US/docs/Web/HTTP)
