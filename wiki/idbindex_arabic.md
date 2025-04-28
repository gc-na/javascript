<!--
Meta Description: # IDBIndex في JavaScript: دليل شامل ## ملخص `IDBIndex` هو واجهة برمجية في JavaScript تسمح بالوصول إلى الفهارس في قواعد بيانات IndexedDB. تستخدم هذه ال...
Meta Keywords: البيانات, الفهرس, الفهارس, إنشاء, let
-->

# IDBIndex في JavaScript: دليل شامل

## ملخص
`IDBIndex` هو واجهة برمجية في JavaScript تسمح بالوصول إلى الفهارس في قواعد بيانات IndexedDB. تستخدم هذه الواجهة لتحسين أداء استعلامات البيانات من خلال توفير وسيلة للبحث عن البيانات بشكل أسرع وأكثر كفاءة.

## الوثائق
### الغرض
`IDBIndex` تستخدم لتمكين الوصول إلى البيانات المخزنة في IndexedDB بطريقة منظمة وفعالة. يتم إنشاء الفهارس على الحقول المحددة في كائنات البيانات لتحسين سرعة البحث.

### الاستخدام
لإنشاء فهرس، يجب أولاً إنشاء قاعدة بيانات (Database) ثم إضافة كائن مخزن (Object Store) مع الفهارس. يمكن استخدام `IDBIndex` للبحث عن البيانات في الكائنات المخزنة. 

### التفاصيل
- **إنشاء الفهرس**: يتم إنشاء الفهرس عند إنشاء كائن مخزن باستخدام `createIndex`، حيث يمكن تحديد اسم الفهرس، واسم الخاصية التي سيتم الفهرسة عليها، وما إذا كان الفهرس فريدًا.
- **البحث باستخدام الفهرس**: يمكن استخدام الفهارس للبحث عن البيانات باستخدام `IDBObjectStore.index()` للحصول على الفهرس المحدد، ثم استخدام `get` أو `getAll` لاسترجاع البيانات.

## الأمثلة
### إنشاء قاعدة بيانات وفهرس
```javascript
let request = indexedDB.open("MyDatabase", 1);

request.onupgradeneeded = function(event) {
    let db = event.target.result;
    let objectStore = db.createObjectStore("MyObjectStore", { keyPath: "id" });
    objectStore.createIndex("nameIndex", "name", { unique: false });
};
```

### استخدام الفهرس للبحث عن البيانات
```javascript
let transaction = db.transaction("MyObjectStore", "readonly");
let objectStore = transaction.objectStore("MyObjectStore");
let index = objectStore.index("nameIndex");

let request = index.get("John Doe");
request.onsuccess = function(event) {
    console.log(event.target.result);
};
```

## الشرح
### الأخطاء الشائعة
- **عدم وجود الفهرس**: إذا حاولت الوصول إلى فهرس غير موجود، ستواجه خطأ. تأكد من أن الفهرس قد تم إنشاؤه بشكل صحيح.
- **المشكلات في التوافق**: بعض المتصفحات قد لا تدعم جميع ميزات IndexedDB. تحقق دائمًا من دعم المتصفح للميزات التي تستخدمها.

### ملاحظات إضافية
- يمكن أن يكون إنشاء الفهارس غير فعال في بعض الحالات. إذا كانت البيانات تتغير بشكل متكرر، قد يكون من الأفضل تجنب الفهارس.
- تأكد من تعيين خاصية `unique` بشكل صحيح بناءً على متطلبات تطبيقك.

## ملخص من سطر واحد
`IDBIndex` هي واجهة برمجية في JavaScript تُستخدم للوصول بشكل فعال إلى البيانات المخزنة في IndexedDB عن طريق الفهارس.