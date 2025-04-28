<!--
Meta Description: # decodeURI في JavaScript: فك تشفير URI بسهولة ## ملخص `decodeURI` هو دالة في JavaScript تُستخدم لفك تشفير سلسلة نصية تم ترميزها باستخدام `encodeURI`....
Meta Keywords: decodeuri, javascript, تشفير, uri, encodeduri
-->

# decodeURI في JavaScript: فك تشفير URI بسهولة

## ملخص
`decodeURI` هو دالة في JavaScript تُستخدم لفك تشفير سلسلة نصية تم ترميزها باستخدام `encodeURI`. تستخدم هذه الدالة لإعادة السلاسل النصية إلى حالتها الأصلية، مما يسهل التعامل مع العناوين والروابط.

## الوثائق
### الغرض
تُستخدم دالة `decodeURI` لفك تشفير النصوص التي تم ترميزها باستخدام `encodeURI`. تُعتبر هذه الدالة مفيدة للتعامل مع عناوين URL التي تحتوي على أحرف خاصة أو محجوزة.

### الاستخدام
```javascript
decodeURI(encodedURI);
```

#### المعاملات
- **encodedURI**: سلسلة نصية تم ترميزها، والتي تريد فك تشفيرها.

#### القيم المرجعة
تُرجع `decodeURI` سلسلة نصية تم فك تشفيرها.

### تفاصيل
- لا تقوم `decodeURI` بفك تشفير الأحرف الخاصة مثل `#`، `?`، و`&`، حيث تُعتبر هذه الأحرف مهمة في بنية URI.
- تُعتبر `decodeURIComponent` دالة مشابهة، ولكنها تُستخدم لفك تشفير الأجزاء الفردية من URI، بما في ذلك الأحرف المحجوزة.

## أمثلة
### مثال 1: فك تشفير URI بسيط
```javascript
let encodedURI = "https%3A%2F%2Fexample.com%2Fpage%3Fid%3D123";
let decodedURI = decodeURI(encodedURI);
console.log(decodedURI); // "https://example.com/page?id=123"
```

### مثال 2: استخدام الأحرف الخاصة
```javascript
let encodedURI = "Hello%20World%21";
let decodedURI = decodeURI(encodedURI);
console.log(decodedURI); // "Hello World!"
```

## الشرح
### الفخاخ الشائعة
- **عدم استخدام الدالة الصحيحة**: تأكد من أنك تستخدم `decodeURI` بدلاً من `decodeURIComponent` إذا كنت تعمل مع URI كامل.
- **إدخال بيانات غير صحيحة**: إذا كانت سلسلة الإدخال تحتوي على أحرف غير صحيحة، فقد تؤدي إلى استثناءات أو نتائج غير متوقعة. تأكد من أن السلسلة المدخلة تم ترميزها بشكل صحيح.

### ملاحظات إضافية
- تُعتبر `decodeURI` جزءًا أساسيًا من معالجة الروابط في JavaScript، خاصة عند التعامل مع استجابات الشبكة أو البيانات الواردة من المستخدمين.

## ملخص من سطر واحد
`decodeURI` هي دالة في JavaScript تُستخدم لفك تشفير URI تم ترميزها، مما يسهل التعامل مع الروابط وعناوين URL.