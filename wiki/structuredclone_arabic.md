<!--
Meta Description: # النسخة المهيكلة في JavaScript: فهم واستخدام structuredClone ## ملخص `structuredClone` هي دالة في JavaScript تُستخدم لإنشاء نسخ عميقة من الكائنات وال...
Meta Keywords: structuredclone, نسخ, clone, javascript, const
-->

# النسخة المهيكلة في JavaScript: فهم واستخدام structuredClone

## ملخص
`structuredClone` هي دالة في JavaScript تُستخدم لإنشاء نسخ عميقة من الكائنات والبيانات، مما يسمح بنسخ البيانات المعقدة بطريقة موثوقة وفعالة.

## الوثائق
### الغرض
تُستخدم دالة `structuredClone` لإنشاء نسخ عميقة من الكائنات، مما يعني أنها تُعيد كائنًا جديدًا يحتوي على نفس البيانات، مع عدم مشاركة أي مراجع مع الكائن الأصلي.

### الاستخدام
يمكن استخدام `structuredClone` مع أي نوع من البيانات، بما في ذلك الكائنات، المصفوفات، التواريخ، وغيرها من الأنواع القابلة للتكرار. 

### الصياغة
```javascript
const clone = structuredClone(value);
```

- **value**: الكائن أو القيمة التي تريد إنشاء نسخة مهيكلة منها.
- **clone**: النسخة العميقة الناتجة.

### التفاصيل
- تدعم `structuredClone` الكائنات المتداخلة، مما يعني أنه يمكنها نسخ الكائنات المعقدة بسهولة.
- يمكن استخدامها مع بيانات مثل `Map`, `Set`, و`ArrayBuffer`.
- لا تدعم `structuredClone` بعض الأنواع مثل الدوال (functions) و`undefined`.

## أمثلة
### مثال 1: نسخ كائن بسيط
```javascript
const original = { name: "Ali", age: 30 };
const clone = structuredClone(original);
console.log(clone); // { name: "Ali", age: 30 }
```

### مثال 2: نسخ كائن مع مصفوفة
```javascript
const original = { name: "Sara", hobbies: ["reading", "traveling"] };
const clone = structuredClone(original);
console.log(clone.hobbies); // ["reading", "traveling"]
```

### مثال 3: نسخ كائن متداخل
```javascript
const original = { name: "Omar", address: { city: "Cairo", zip: 12345 } };
const clone = structuredClone(original);
console.log(clone.address.city); // "Cairo"
```

## الشرح
### المخاطر الشائعة
- **عدم دعم الدوال**: إذا حاولت نسخ كائن يحتوي على دوال، فإن `structuredClone` ستقوم بتجاهلها، مما قد يؤدي إلى فقدان بعض الوظائف.
- **التعامل مع `undefined`**: إذا كانت القيم تحتوي على `undefined`، سيتم استبدالها بـ `undefined` في النسخة المهيكلة.
- **تأثيرات سلبية على الأداء**: النسخ العميق يمكن أن يكون مكلفًا من حيث الأداء إذا كان الكائن كبيرًا جدًا.

### ملاحظات إضافية
- تعتبر `structuredClone` جزءًا من مواصفات ECMAScript الحديثة، لذا تأكد من أن بيئة التنفيذ تدعمها.
- استخدم `structuredClone` بدلاً من طرق النسخ التقليدية مثل `Object.assign` أو استخدام الجملة `JSON.stringify` و`JSON.parse` للحصول على نسخ عميقة موثوقة.

## ملخص جملة واحدة
تُستخدم دالة `structuredClone` في JavaScript لإنشاء نسخ عميقة من الكائنات، مما يتيح التعامل مع البيانات المعقدة بشكل موثوق وفعال.