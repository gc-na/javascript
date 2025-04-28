<!--
Meta Description: # encodeURIComponent في جافا سكريبت: الدليل الكامل ## ملخص `encodeURIComponent` هي دالة في جافا سكريبت تُستخدم لترميز مكونات URI (معرف الموارد الموحد)...
Meta Keywords: encodeuricomponent, uri, ستخدم, javascript, مكونات
-->

# encodeURIComponent في جافا سكريبت: الدليل الكامل

## ملخص
`encodeURIComponent` هي دالة في جافا سكريبت تُستخدم لترميز مكونات URI (معرف الموارد الموحد) لضمان أن تكون البيانات المُرسلة عبر الشبكة آمنة وصحيحة.

## الوثائق
### الغرض
تُستخدم دالة `encodeURIComponent` لتحويل سلسلة نصية إلى شكل مُرمز بحيث يمكن استخدامها ضمن URI. تُعتبر هذه الدالة ضرورية عند إرسال البيانات مثل المعلمات في عنوان URL، حيث تُستخدم لتجنب أي تضارب مع رموز خاصة.

### الاستخدام
```javascript
encodeURIComponent(string)
```
- **string**: سلسلة نصية تحتاج إلى الترميز.

### التفاصيل
- تُرجع الدالة قيمة نصية مُرمزة تُستخدم في URI.
- تُشير الرموز مثل `!`, `*`, `'`, `(`, `)`, `;`, `:`, `@`, `&`, `=`, `+`, `$`, `,`, `/`, `?`, `#`, `[`, `]` إلى مكونات خاصة في URI، وعند استخدامها يجب ترميزها لتجنب أي تداخل.

## أمثلة
### مثال 1: ترميز نص بسيط
```javascript
let encoded = encodeURIComponent("Hello World!");
console.log(encoded); // "Hello%20World%21"
```

### مثال 2: ترميز عنوان URL مع معلمات
```javascript
let url = "https://example.com/?search=" + encodeURIComponent("JavaScript & HTML");
console.log(url); // "https://example.com/?search=JavaScript%20%26%20HTML"
```

### مثال 3: ترميز نص يحتوي على رموز خاصة
```javascript
let specialChars = encodeURIComponent("! * ' ( ) ; : @ & = + $ , / ? # [ ]");
console.log(specialChars); // "%21%20%2A%20%27%20%28%20%29%20%3B%20%3A%20%40%20%26%20%3D%20%2B%20%24%20%2C%20%2F%20%3F%20%23%20%5B%20%5D"
```

## الشرح
### أخطاء شائعة
- **عدم استخدام الدالة بشكل صحيح**: يجب استخدام `encodeURIComponent` لكل مكون من مكونات URI وليس للعنوان الكامل.
- **خلط بين `encodeURIComponent` و `encodeURI`**: `encodeURI` تُستخدم لترميز URI بالكامل، بينما `encodeURIComponent` تُستخدم لترميز مكونات URI بشكل فردي.

### ملاحظات إضافية
- تأكد من استخدام `decodeURIComponent` عند الحاجة لفك ترميز السلاسل المُرمزة.
- استخدام `encodeURIComponent` يُساهم في تحسين أمان البيانات المُرسلة عبر الشبكة، ويجنب الأخطاء الناتجة عن الرموز غير المرغوب فيها.

## ملخص جملة واحدة
`encodeURIComponent` هي دالة في جافا سكريبت تُستخدم لترميز مكونات URI لضمان سلامة البيانات المُرسلة عبر الشبكة.