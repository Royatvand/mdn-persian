---
title: "Response: json() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Response/json"
---

---
title: "Response: json() method"
short-title: json()
slug: Web/API/Response/json
page-type: web-api-instance-method
browser-compat: api.Response.json
---

{{APIRef("Fetch API")}}{{AvailableInWorkers}}

متد **`json()`** از رابط {{DOMxRef("Response")}} جریان پاسخ را تا انتها می‌خواند و یک Promise برمی‌گرداند که با نتیجهٔ تجزیهٔ متن بدنه به‌عنوان {{JSxRef("JSON")}} تکمیل می‌شود.

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

- `AbortError` {{domxref("DOMException")}}
  - : اگر درخواست لغو شده باشد، این خطا رخ می‌دهد. [توضیحات بیشتر](/en-US/docs/Web/API/Fetch_API/Using_Fetch#canceling_a_request)
- {{jsxref("TypeError")}}
  - : اگر بدنهٔ پاسخ قبلاً خوانده شده یا قفل شده باشد، یا هنگام رمزگشایی محتوای بدنه خطایی رخ دهد؛ برای مثال، سربرگ {{httpheader("Content-Encoding")}} نادرست باشد.
- {{jsxref("SyntaxError")}}
  - : اگر نتوان بدنهٔ پاسخ را به‌عنوان JSON تجزیه کرد.

## مثال

در [نمونهٔ دریافت JSON](https://github.com/mdn/dom-examples/tree/main/fetch/fetch-json) می‌بینیم که چگونه با سازندهٔ {{DOMxRef("Request.Request", "Request()")}} درخواست جدیدی ساخته و یک فایل `.json` دریافت کنیم. پس از موفقیت درخواست، داده‌ها را با `json()` می‌خوانیم و تجزیه می‌کنیم؛ سپس مقادیر شیءهای حاصل را در عناصر فهرست قرار می‌دهیم تا اطلاعات محصولات نمایش داده شوند.

```js
const myList = document.querySelector("ul");
const myRequest = new Request("products.json");

fetch(myRequest)
  .then((response) => response.json())
  .then((data) => {
    for (const product of data.products) {
      const listItem = document.createElement("li");
      listItem.appendChild(document.createElement("strong")).textContent =
        product.Name;
      listItem.append(` can be found in ${product.Location}. Cost: `);
      listItem.appendChild(document.createElement("strong")).textContent =
        `£${product.Price}`;
      myList.appendChild(listItem);
    }
  })
  .catch(console.error);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [رابط Service Worker](/en-US/docs/Web/API/Service_Worker_API)
- [اشتراک‌گذاری منابع بین‌مبدأ (CORS)](/en-US/docs/Web/HTTP/Guides/CORS)
- [HTTP](/en-US/docs/Web/HTTP)
