<!--
Meta Description: # indexedDB في JavaScript: تخزين البيانات المحلية بشكل غير متزامن ## الملخص indexedDB هي واجهة برمجة تطبيقات (API) في JavaScript تتيح للمطورين تخزين ك...
Meta Keywords: البيانات, const, indexeddb, بيانات, request
-->

# indexedDB في JavaScript: تخزين البيانات المحلية بشكل غير متزامن

## الملخص
indexedDB هي واجهة برمجة تطبيقات (API) في JavaScript تتيح للمطورين تخزين كميات كبيرة من البيانات بشكل محلي في متصفح المستخدم، مما يسهل الوصول إليها بسرعة وفعالية.

## الوثائق
### الغرض
تُستخدم indexedDB لتخزين البيانات غير المتزامنة في شكل كائنات، مما يتيح للمستخدمين تخزين البيانات الكبيرة التي تحتاج إلى استرجاع سريع دون الحاجة إلى الاتصال بالإنترنت.

### الاستخدام
indexedDB تعمل بشكل غير متزامن، مما يعني أن جميع العمليات لا تعيق واجهة المستخدم. توفر واجهة برمجة التطبيقات هذه إمكانية إنشاء قواعد بيانات محلية، جداول، وإدخال بيانات في هذه الجداول. 

### التفاصيل
- **إنشاء قاعدة بيانات**: يمكنك إنشاء قاعدة بيانات جديدة باستخدام `indexedDB.open()`.
- **المعاملات**: يتم تنفيذ العمليات داخل معاملات (transactions) لضمان سلامة البيانات.
- **المؤشرات**: تدعم indexedDB إنشاء مؤشرات لتسهيل البحث عن البيانات.
- **التخزين**: يمكن تخزين كائنات JavaScript، مما يجعل من السهل التعامل مع البيانات المعقدة.

## الأمثلة
### إنشاء قاعدة بيانات
```javascript
const request = indexedDB.open("myDatabase", 1);

request.onupgradeneeded = function(event) {
    const db = event.target.result;
    const objectStore = db.createObjectStore("myObjectStore", { keyPath: "id" });
};

request.onsuccess = function(event) {
    const db = event.target.result;
    console.log("Database opened successfully");
};
```

### إضافة بيانات
```javascript
const addData = (db, data) => {
    const transaction = db.transaction(["myObjectStore"], "readwrite");
    const objectStore = transaction.objectStore("myObjectStore");
    const request = objectStore.add(data);

    request.onsuccess = function() {
        console.log("Data added successfully");
    };
};
```

### استرجاع بيانات
```javascript
const getData = (db, id) => {
    const transaction = db.transaction(["myObjectStore"]);
    const objectStore = transaction.objectStore("myObjectStore");
    const request = objectStore.get(id);

    request.onsuccess = function() {
        console.log("Data retrieved:", request.result);
    };
};
```

## الشرح
### الأخطاء الشائعة
- **إغلاق قاعدة البيانات**: تأكد من فتح قاعدة البيانات قبل إجراء العمليات عليها.
- **عدم وجود كائن**: إذا حاولت استرجاع كائن غير موجود، سيعيد `undefined`، لذا تحقق من وجود البيانات قبل استخدامها.
- **الإصدار**: إذا قمت بتحديث قاعدة البيانات، تأكد من التعامل مع حدث `onupgradeneeded` بشكل صحيح.

### ملاحظات إضافية
- **التوافق**: تأكد من أن المتصفح يدعم indexedDB، حيث أن بعض المتصفحات القديمة قد لا تدعم هذه الواجهة.
- **الأمان**: البيانات المخزنة في indexedDB ليست مشفرة بشكل افتراضي، لذا من المهم عدم تخزين بيانات حساسة.

## ملخص جملة واحدة
indexedDB هي واجهة برمجة تطبيقات في JavaScript تتيح تخزين البيانات محليًا بشكل غير متزامن، مما يوفر وصولاً سريعًا وفعالاً للبيانات.