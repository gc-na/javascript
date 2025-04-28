<!--
Meta Description: # encodeURI في JavaScript: كيفية استخدامه وفوائده ## ملخص `encodeURI` هو دالة في JavaScript تستخدم لترميز عنوان URL، مما يسمح بتمثيل الحروف الخاصة بطر...
Meta Keywords: encodeuri, url, عنوان, الحروف, javascript
-->

# encodeURI في JavaScript: كيفية استخدامه وفوائده

## ملخص
`encodeURI` هو دالة في JavaScript تستخدم لترميز عنوان URL، مما يسمح بتمثيل الحروف الخاصة بطريقة آمنة في عناوين الويب.

## الوثائق
تستخدم دالة `encodeURI` لترميز عنوان URL بالكامل، مما يعني أنها تتعامل مع الحروف الخاصة والمحمية في URLs. هذه الدالة لا تقوم بترميز الحروف التي لها معنى خاص في عنوان URL مثل `:`, `/`, `?`, `&`, و`=`.

### الاستخدام
```javascript
encodeURI(uri)
```

- **uri**: سلسلة نصية تمثل عنوان URL الذي ترغب في ترميزه.

### تفاصيل
- تعيد الدالة سلسلة نصية جديدة تمثل عنوان URL مع ترميز الحروف الخاصة.
- لا تقوم `encodeURI` بتغيير الحروف التي تعتبر جزءًا من بناء جملة URL.
- من الضروري استخدام `encodeURI` عند التعامل مع بيانات ديناميكية قد تحتوي على حروف خاصة لتفادي الأخطاء الناتجة عن عناوين غير صالحة.

## أمثلة
### المثال 1: ترميز عنوان URL بسيط
```javascript
let url = "https://www.example.com/تجربة";
let encodedUrl = encodeURI(url);
console.log(encodedUrl); // https://www.example.com/%D8%AA%D8%AC%D8%B1%D8%A8%D8%A9
```

### المثال 2: ترميز عنوان URL مع علامات استفهام
```javascript
let query = "name=علي&age=30";
let baseUrl = "https://www.example.com/search?";
let fullUrl = baseUrl + query;
let encodedFullUrl = encodeURI(fullUrl);
console.log(encodedFullUrl); // https://www.example.com/search?name=%D8%B9%D9%84%D9%8A&age=30
```

## الشرح
هناك بعض النقاط التي يجب أن تؤخذ بعين الاعتبار عند استخدام `encodeURI`:
- **عدم ترميز الحروف الخاصة**: `encodeURI` لا ترمز الحروف مثل `#` و`&` و`?`، لذا يجب التأكد من عدم استخدامها في سياق غير صحيح.
- **التمييز بين `encodeURI` و`encodeURIComponent`**: إذا كنت بحاجة لترميز جزء من عنوان URL (مثل قيمة استعلام)، استخدم `encodeURIComponent` بدلاً من `encodeURI`، حيث أن `encodeURIComponent` ترمز جميع الحروف الخاصة.

## ملخص جملة واحدة
`encodeURI` هي دالة JavaScript تستخدم لترميز عنوان URL بشكل آمن، مما يسمح بتجنب الأخطاء الناتجة عن الحروف الخاصة.