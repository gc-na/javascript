<!--
Meta Description: # IDBDatabase في JavaScript: الدليل الشامل ## ملخص `IDBDatabase` هو واجهة برمجة التطبيقات (API) المستخدمة للتفاعل مع قواعد بيانات IndexedDB في JavaScr...
Meta Keywords: البيانات, قاعدة, let, event, indexeddb
-->

# IDBDatabase في JavaScript: الدليل الشامل

## ملخص
`IDBDatabase` هو واجهة برمجة التطبيقات (API) المستخدمة للتفاعل مع قواعد بيانات IndexedDB في JavaScript، مما يتيح تخزين البيانات بشكل غير متزامن داخل متصفح المستخدم.

## الوثائق
### الغرض
`IDBDatabase` تمثل قاعدة بيانات في IndexedDB وتوفر وسائل لتخزين واسترجاع البيانات بشكل فعال. يسمح للمطورين بإنشاء قواعد بيانات محلية، مما يسهل إدارة البيانات بشكل غير متزامن.

### الاستخدام
يتم إنشاء كائن `IDBDatabase` عند فتح قاعدة بيانات باستخدام `indexedDB.open()`. يمكن استخدامه لتنفيذ عمليات مثل إنشاء المخازن (object stores) والكتابة والقراءة من قاعدة البيانات.

### التفاصيل
- **الخصائص**:
  - `name`: اسم قاعدة البيانات.
  - `version`: رقم إصدار قاعدة البيانات.
  
- **الطرق**:
  - `transaction()`: لإنشاء معاملة جديدة.
  - `close()`: لإغلاق قاعدة البيانات.

## الأمثلة
### مثال 1: إنشاء قاعدة بيانات بسيطة
```javascript
let request = indexedDB.open("MyDatabase", 1);

request.onupgradeneeded = function(event) {
    let db = event.target.result;
    db.createObjectStore("myStore", { keyPath: "id" });
};

request.onsuccess = function(event) {
    let db = event.target.result;
    console.log("Database opened successfully", db);
};

request.onerror = function(event) {
    console.error("Database error: ", event.target.errorCode);
};
```

### مثال 2: إضافة بيانات إلى المخزن
```javascript
let dbRequest = indexedDB.open("MyDatabase", 1);

dbRequest.onsuccess = function(event) {
    let db = event.target.result;
    let transaction = db.transaction("myStore", "readwrite");
    let store = transaction.objectStore("myStore");

    let data = { id: 1, name: "John Doe" };
    let addRequest = store.add(data);

    addRequest.onsuccess = function() {
        console.log("Data added successfully");
    };

    addRequest.onerror = function() {
        console.error("Error adding data: ", addRequest.error);
    };
};
```

## الشرح
### pitfalls
- **إصدار قاعدة البيانات**: عند تعديل بنية قاعدة البيانات، يجب زيادة الرقم الإصدار. إذا لم يتم ذلك، فلن تُنفذ عمليات `onupgradeneeded`.
- **المعاملات**: تأكد من استخدام المعاملات بشكل صحيح، حيث أن عدم استخدامها قد يؤدي إلى فقدان البيانات أو عدم تنفيذ العمليات.

### ملاحظات إضافية
- توفر `IDBDatabase` واجهات غير متزامنة، لذا تأكد من التعامل مع الوعود (Promises) بشكل صحيح لتجنب المشاكل.
- تأكد من أن المتصفح يدعم IndexedDB، حيث أن بعض المتصفحات القديمة قد لا تدعمه.

## ملخص من جملة واحدة
`IDBDatabase` هو واجهة في JavaScript تسمح بالتفاعل مع قواعد البيانات المحلية باستخدام IndexedDB لتخزين البيانات بشكل غير متزامن.