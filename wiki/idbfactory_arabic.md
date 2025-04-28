<!--
Meta Description: # IDBFactory في JavaScript: دليلك الشامل ## ملخص IDBFactory هو واجهة برمجة تطبيقات JavaScript تُستخدم للوصول إلى قاعدة بيانات IndexedDB، مما يسمح بتخز...
Meta Keywords: event, بيانات, indexeddb, idbfactory, قاعدة
-->

# IDBFactory في JavaScript: دليلك الشامل

## ملخص
IDBFactory هو واجهة برمجة تطبيقات JavaScript تُستخدم للوصول إلى قاعدة بيانات IndexedDB، مما يسمح بتخزين البيانات في متصفح المستخدم بطريقة غير متزامنة. 

## الوثائق
تعتبر IDBFactory جزءًا من واجهة برمجة التطبيقات الخاصة بـ IndexedDB، وهي توفر وسائل لإنشاء قواعد بيانات، وفتح اتصالات بها، وفتح المعاملات. توفر IDBFactory وظائف متعددة، منها:

- **open()**: تُستخدم لفتح قاعدة بيانات موجودة أو لإنشاء واحدة جديدة إذا لم تكن موجودة. 
- **deleteDatabase()**: تُستخدم لحذف قاعدة بيانات بالكامل. 

### الاستخدام
لاستخدام IDBFactory، يجب عليك أولاً التحقق من دعم المتصفح لهذه الواجهة. إليك كيفية استخدام الدالة `open()`:

```javascript
let request = indexedDB.open("MyDatabase", 1);

request.onsuccess = function(event) {
    let db = event.target.result;
    console.log("Database opened successfully", db);
};

request.onerror = function(event) {
    console.error("Error opening database", event);
};
```

## الأمثلة
### مثال 1: فتح قاعدة بيانات
```javascript
let request = indexedDB.open("MyDatabase", 1);

request.onupgradeneeded = function(event) {
    let db = event.target.result;
    db.createObjectStore("MyStore", { keyPath: "id" });
};

request.onsuccess = function(event) {
    let db = event.target.result;
    console.log("Database opened successfully", db);
};

request.onerror = function(event) {
    console.error("Error opening database", event);
};
```

### مثال 2: حذف قاعدة بيانات
```javascript
let deleteRequest = indexedDB.deleteDatabase("MyDatabase");

deleteRequest.onsuccess = function(event) {
    console.log("Database deleted successfully");
};

deleteRequest.onerror = function(event) {
    console.error("Error deleting database", event);
};
```

## الشرح
عند العمل مع IDBFactory، يجب الانتباه إلى بعض النقاط المهمة:

- **التوافق**: تأكد من أن المتصفح يدعم IndexedDB. يمكنك استخدام `window.indexedDB` للتحقق من وجوده.
- **الإصدار**: عند فتح قاعدة بيانات، يجب عليك تحديد رقم الإصدار. إذا كان رقم الإصدار أعلى من الإصدار الحالي، سيتم استدعاء `onupgradeneeded` لتحديث هيكل قاعدة البيانات.
- **الأحداث**: تأكد من التعامل مع الأحداث `onsuccess` و `onerror` بشكل صحيح للتعامل مع نتائج العمليات.

## ملخص من سطر واحد
IDBFactory هي واجهة برمجة تطبيقات JavaScript تتيح للمطورين إدارة قواعد بيانات IndexedDB بسهولة وكفاءة.