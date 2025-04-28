<!--
Meta Description: # decodeURIComponent في جافا سكريبت: شرح شامل ## ملخص `decodeURIComponent` هي دالة في JavaScript تستخدم لفك تشفير سلسلة نصية مشفرة في صيغة URI، مما يس...
Meta Keywords: decodeuricomponent, تشفير, javascript, سلسلة, نصية
-->

# decodeURIComponent في جافا سكريبت: شرح شامل

## ملخص
`decodeURIComponent` هي دالة في JavaScript تستخدم لفك تشفير سلسلة نصية مشفرة في صيغة URI، مما يسمح بتحويل الرموز الخاصة إلى نص عادي.

## الوثائق
تعمل دالة `decodeURIComponent` على فك تشفير مكونات URI، وهي مفيدة بشكل خاص عند التعامل مع بيانات تم ترميزها باستخدام `encodeURIComponent`. الهدف من هذه الدالة هو تحويل الأحرف المشفرة مثل `%20` إلى مساحتها المعنية (space).

### الاستخدام
تستخدم الدالة بالطريقة التالية:

```javascript
decodeURIComponent(encodedURI);
```

- **المعلمة**: 
  - `encodedURI`: سلسلة نصية مشفرة باستخدام `encodeURIComponent`.

### التفاصيل
- **الإرجاع**: تعيد الدالة سلسلة نصية تم فك تشفيرها.
- **الاستثناءات**: في حال كانت السلسلة المدخلة تحتوي على رموز غير صالحة، ستظهر استثناءات (Errors) تُشير إلى أن السلسلة لا يمكن فك تشفيرها.

## الأمثلة

### مثال 1: فك تشفير نص مشفر
```javascript
const encodedStr = "Hello%20World%21";
const decodedStr = decodeURIComponent(encodedStr);
console.log(decodedStr); // يطبع: Hello World!
```

### مثال 2: فك تشفير عنوان URL
```javascript
const encodedURL = "https%3A%2F%2Fwww.example.com%2Fpage%3Fid%3D123";
const decodedURL = decodeURIComponent(encodedURL);
console.log(decodedURL); // يطبع: https://www.example.com/page?id=123
```

## الشرح
عند استخدام `decodeURIComponent`، يجب الحذر من بعض النقاط الشائعة:

- **الرموز غير الصالحة**: إذا كانت السلسلة تحتوي على رموز مشفرة بشكل خاطئ، قد يؤدي ذلك إلى ظهور استثناءات. تأكد من أن السلسلة قد تم ترميزها بشكل صحيح باستخدام `encodeURIComponent`.

- **الاستخدام في عناوين URL**: عند العمل مع عناوين URL، من الشائع استخدام `encodeURIComponent` لتشفير المكونات، مثل المعلمات. لذا فإن استخدام `decodeURIComponent` لفك تشفير هذه المعلمات يعد خطوة ضرورية.

## ملخص من جملة واحدة
تُستخدم دالة `decodeURIComponent` في JavaScript لفك تشفير سلسلة نصية مشفرة في صيغة URI، مما يسهل التعامل مع البيانات المدخلة.