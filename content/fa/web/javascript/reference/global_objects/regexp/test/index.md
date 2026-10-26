---
title: "RegExp.prototype.test()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/test"
---

---
title: RegExp.prototype.test()
short-title: test()
slug: Web/JavaScript/Reference/Global_Objects/RegExp/test
page-type: javascript-instance-method
browser-compat: javascript.builtins.RegExp.test
sidebar: jsref
---

متد **`test()`** در نمونه‌های {{jsxref("RegExp")}} بررسی می‌کند که آیا عبارت باقاعده با رشتهٔ مشخص‌شده تطبیق دارد یا نه. در صورت تطبیق `true` و در غیر این صورت `false` برمی‌گرداند.

اشیای {{jsxref("RegExp")}} در جاوااسکریپت، وقتی پرچم {{jsxref("RegExp/global", "global")}} یا {{jsxref("RegExp/sticky", "sticky")}} داشته باشند (مثلاً `/foo/g` یا `/foo/y`)، **دارای وضعیت** هستند. آن‌ها اندیس {{jsxref("RegExp/lastIndex", "lastIndex")}} تطبیق قبلی را نگه می‌دارند. به کمک این ویژگی می‌توان از `test()` برای پیمایش چند تطبیق در یک رشته (همراه با گروه‌های ثبت‌شده) استفاده کرد.

{{InteractiveExample("JavaScript Demo: RegExp.prototype.test()", "taller")}}

```js interactive-example
const str = "table football";

const regex = /fo+/;
const globalRegex = /fo+/g;

console.log(regex.test(str));
// Expected output: true

console.log(globalRegex.lastIndex);
// Expected output: 0

console.log(globalRegex.test(str));
// Expected output: true

console.log(globalRegex.lastIndex);
// Expected output: 9

console.log(globalRegex.test(str));
// Expected output: false
```

## نحو

```js-nolint
test(str)
```

### پارامترها

- `str`
  - : رشته‌ای که عبارت باقاعده باید با آن تطبیق داده شود. همهٔ مقدارها به رشته [تبدیل](/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#string_coercion) می‌شوند؛ بنابراین حذف آرگومان یا ارسال `undefined` باعث می‌شود `test()` به‌دنبال رشتهٔ `"undefined"` بگردد که معمولاً مطلوب نیست.

### مقدار بازگشتی

اگر عبارت باقاعده با رشتهٔ `str` تطبیق داشته باشد، `true` و در غیر این صورت `false`.

## توضیحات

هرگاه بخواهید بدانید الگویی در رشته وجود دارد یا نه، از `test()` استفاده کنید. این متد مقدار بولی برمی‌گرداند؛ برخلاف {{jsxref("String.prototype.search()")}} که اندیس تطبیق یا در صورت پیدا نشدن `-1` را برمی‌گرداند.

برای دریافت اطلاعات بیشتر (با اجرای کندتر)، از متد {{jsxref("RegExp/exec", "exec()")}} استفاده کنید. این متد مشابه {{jsxref("String.prototype.match()")}} است.

همانند `exec()`، اگر `test()` چند بار روی یک نمونهٔ عبارت باقاعدهٔ سراسری فراخوانی شود، جست‌وجو پس از تطبیق قبلی ادامه پیدا می‌کند.

## مثال‌ها

### استفاده از test()

این مثال بررسی می‌کند که آیا رشته با `"hello"` آغاز می‌شود یا نه و نتیجه‌ای بولی برمی‌گرداند.

```js
const str = "hello world!";
const result = /^hello/.test(str);

console.log(result); // true
```

مثال زیر پیامی متناسب با موفقیت یا شکست آزمون در کنسول چاپ می‌کند:

```js
function testInput(re, str) {
  const midString = re.test(str) ? "contains" : "does not contain";
  console.log(`${str} ${midString} ${re.source}`);
}
```

### استفاده از test() on a regex with the "global" flag

وقتی عبارت باقاعده دارای [پرچم global](/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/global) باشد، `test()` مقدار {{jsxref("RegExp/lastIndex", "lastIndex")}} آن را جلو می‌برد. (متد {{jsxref("RegExp.prototype.exec()")}} نیز ویژگی `lastIndex` را تغییر می‌دهد.)

فراخوانی‌های بعدی `test(str)` جست‌وجو در `str` را از `lastIndex` ادامه می‌دهند. هر بار که `test()` مقدار `true` برگرداند، مقدار `lastIndex` افزایش می‌یابد.

> [!NOTE]
> As long as `test()` returns `true`,
> `lastIndex` will _not_ reset—even when testing a different string!

وقتی `test()` مقدار `false` برگرداند، ویژگی `lastIndex` عبارت باقاعدهٔ فراخوانی‌شده به `0` بازنشانی می‌شود.

مثال زیر این رفتار را نشان می‌دهد:

```js
const regex = /foo/g; // the "global" flag is set

// regex.lastIndex is at 0
regex.test("foo"); // true

// regex.lastIndex is now at 3
regex.test("foo"); // false

// regex.lastIndex is at 0
regex.test("barfoo"); // true

// regex.lastIndex is at 6
regex.test("foobar"); // false

// regex.lastIndex is at 0
regex.test("foobarfoo"); // true

// regex.lastIndex is at 3
regex.test("foobarfoo"); // true

// regex.lastIndex is at 9
regex.test("foobarfoo"); // false

// regex.lastIndex is at 0
// (...and so on)
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Regular expressions](/en-US/docs/Web/JavaScript/Guide/Regular_expressions) guide
- {{jsxref("RegExp")}}
