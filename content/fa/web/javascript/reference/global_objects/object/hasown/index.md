---
title: "Object.hasOwn()"
source: "https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/hasOwn"
---

---
title: Object.hasOwn()
short-title: hasOwn()
slug: Web/JavaScript/Reference/Global_Objects/Object/hasOwn
page-type: javascript-static-method
browser-compat: javascript.builtins.Object.hasOwn
sidebar: jsref
---

متد ایستای **`Object.hasOwn()`** اگر شیء مشخص‌شده، ویژگی موردنظر را به‌صورت ویژگیِ مستقیم خود داشته باشد، `true` برمی‌گرداند. اگر ویژگی به ارث رسیده باشد یا وجود نداشته باشد، نتیجه `false` است.

> [!NOTE]
> `Object.hasOwn()` برای جایگزینی {{jsxref("Object.prototype.hasOwnProperty()")}} در نظر گرفته شده است.

{{InteractiveExample("JavaScript Demo: Object.hasOwn()")}}

```js interactive-example
const object = {
  prop: "exists",
};

console.log(Object.hasOwn(object, "prop"));
// Expected output: true

console.log(Object.hasOwn(object, "toString"));
// Expected output: false

console.log(Object.hasOwn(object, "undeclaredPropertyValue"));
// Expected output: false
```

## نحو

```js-nolint
Object.hasOwn(obj, prop)
```

### پارامترها

- `obj`
  - : نمونهٔ شیء جاوااسکریپتی که باید بررسی شود.
- `prop`
  - : نام {{jsxref("String")}} یا [Symbol](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol) ویژگی مورد بررسی.

### مقدار بازگشتی

اگر شیء ویژگی مشخص‌شده را مستقیماً تعریف کرده باشد، `true` و در غیر این صورت `false`.

## توضیحات

متد `Object.hasOwn()` اگر ویژگی مشخص‌شده مستقیماً متعلق به شیء باشد، `true` برمی‌گرداند؛ حتی اگر مقدار ویژگی `null` یا `undefined` باشد. اگر ویژگی به ارث رسیده باشد یا اصلاً تعریف نشده باشد، `false` برمی‌گرداند. برخلاف عملگر {{jsxref("Operators/in", "in")}}، این متد زنجیرهٔ prototype شیء را برای یافتن ویژگی بررسی نمی‌کند.

استفاده از این متد به {{jsxref("Object.prototype.hasOwnProperty()")}} ترجیح داده می‌شود؛ زیرا با [اشیای دارای prototype برابر null](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object#null-prototype_objects) و همچنین اشیایی که متد ارث‌بری‌شدهٔ `hasOwnProperty()` را بازنویسی کرده‌اند، کار می‌کند. هرچند می‌توان با فراخوانی `Object.prototype.hasOwnProperty.call(obj, prop)` این مشکلات را دور زد، `Object.hasOwn()` ساده‌تر و قابل‌فهم‌تر است.

## مثال‌ها

### بررسی وجود ویژگی با Object.hasOwn()

کد زیر نشان می‌دهد چگونه بررسی کنیم شیء `example` ویژگی‌ای به نام `prop` دارد یا نه.

```js
const example = {};
Object.hasOwn(example, "prop"); // false - 'prop' has not been defined

example.prop = "exists";
Object.hasOwn(example, "prop"); // true - 'prop' has been defined

example.prop = null;
Object.hasOwn(example, "prop"); // true - own property exists with value of null

example.prop = undefined;
Object.hasOwn(example, "prop"); // true - own property exists with value of undefined
```

### ویژگی‌های مستقیم در برابر ویژگی‌های ارث‌بری‌شده

نمونهٔ زیر تفاوت ویژگی‌های مستقیم و ویژگی‌های به‌ارث‌رسیده از زنجیرهٔ prototype را نشان می‌دهد:

```js
const example = {};
example.prop = "exists";

// `hasOwn` will only return true for direct properties:
Object.hasOwn(example, "prop"); // true
Object.hasOwn(example, "toString"); // false
Object.hasOwn(example, "hasOwnProperty"); // false

// The `in` operator will return true for direct or inherited properties:
"prop" in example; // true
"toString" in example; // true
"hasOwnProperty" in example; // true
```

### پیمایش ویژگی‌های یک شیء

برای پیمایش ویژگی‌های شمارش‌پذیر یک شیء، بهتر است از این روش استفاده کنید:

```js
const example = { foo: true, bar: true };
for (const name of Object.keys(example)) {
  // …
}
```

اما اگر لازم است از `for...in` استفاده کنید، می‌توانید با `Object.hasOwn()` ویژگی‌های ارث‌بری‌شده را نادیده بگیرید:

```js
const example = { foo: true, bar: true };
for (const name in example) {
  if (Object.hasOwn(example, name)) {
    // …
  }
}
```

### بررسی وجود یک اندیس در آرایه

عناصر {{jsxref("Array")}} به‌عنوان ویژگی‌های مستقیم تعریف می‌شوند؛ بنابراین می‌توانید با `hasOwn()` بررسی کنید که اندیس مشخصی وجود دارد یا نه:

```js
const fruits = ["Apple", "Banana", "Watermelon", "Orange"];
Object.hasOwn(fruits, 3); // true ('Orange')
Object.hasOwn(fruits, 4); // false - not defined
```

### موارد مشکل‌ساز برای hasOwnProperty()

این بخش نشان می‌دهد `Object.hasOwn()` تحت تأثیر مشکلات `hasOwnProperty()` قرار نمی‌گیرد. نخست اینکه می‌توان آن را برای اشیایی به کار برد که متد `hasOwnProperty()` را دوباره تعریف کرده‌اند. در مثال زیر، متد بازنویسی‌شده برای همهٔ ویژگی‌ها `false` می‌دهد، اما رفتار `Object.hasOwn()` تغییر نمی‌کند:

```js
const foo = {
  hasOwnProperty() {
    return false;
  },
  bar: "The dragons be out of office",
};

console.log(foo.hasOwnProperty("bar")); // false

console.log(Object.hasOwn(foo, "bar")); // true
```

همچنین می‌توان آن را با [اشیای دارای prototype برابر null](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object#null-prototype_objects) به کار برد. این اشیا از `Object.prototype` ارث‌بری نمی‌کنند، بنابراین متد `hasOwnProperty()` در دسترس نیست.

```js
const foo = Object.create(null);
foo.prop = "exists";

console.log(foo.hasOwnProperty("prop"));
// Uncaught TypeError: foo.hasOwnProperty is not a function

console.log(Object.hasOwn(foo, "prop")); // true
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Polyfill of `Object.hasOwn` in `core-js`](https://github.com/zloirock/core-js#ecmascript-object)
- [es-shims polyfill of `Object.hasOwn`](https://www.npmjs.com/package/object.hasown)
- {{jsxref("Object.prototype.hasOwnProperty()")}}
- [Enumerability and ownership of properties](/en-US/docs/Web/JavaScript/Guide/Enumerability_and_ownership_of_properties)
- {{jsxref("Object.getOwnPropertyNames()")}}
- {{jsxref("Statements/for...in", "for...in")}}
- {{jsxref("Operators/in", "in")}}
- [Inheritance and the prototype chain](/en-US/docs/Web/JavaScript/Guide/Inheritance_and_the_prototype_chain)
