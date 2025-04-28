<!--
Meta Description: # IDBRequest في جافا سكريبت: كل ما تحتاج لمعرفته ## ملخص `IDBRequest` هو كائن يستخدم في واجهة برمجة التطبيقات لـ IndexedDB في جافا سكريبت، حيث يتمثل د...
Meta Keywords: البيانات, قاعدة, let, function, indexeddb
-->

# IDBRequest في جافا سكريبت: كل ما تحتاج لمعرفته

## ملخص
`IDBRequest` هو كائن يستخدم في واجهة برمجة التطبيقات لـ IndexedDB في جافا سكريبت، حيث يتمثل دوره في إدارة عمليات القراءة والكتابة في قاعدة البيانات غير العلائقية.

## الوثائق
`IDBRequest` يمثل طلبًا يتم إرساله إلى قاعدة بيانات IndexedDB. يمكن أن يكون هذا الطلب خاصًا بعمليات مثل القراءة أو الكتابة أو حذف البيانات. يتم إنشاء طلب جديد عند تنفيذ العمليات على كائنات مخزن البيانات.

### الغرض
تستخدم `IDBRequest` لتنفيذ العمليات غير المتزامنة على قاعدة بيانات IndexedDB، مما يسمح للمطورين بالتفاعل مع البيانات بطريقة فعالة ودون حظر واجهة المستخدم.

### الاستخدام
عند إجراء عملية على قاعدة بيانات IndexedDB، يتم إنشاء كائن `IDBRequest` تلقائيًا. يمكنك استخدامه للاستماع إلى أحداث النجاح والفشل المتعلقة بالعملية.

### الخصائص والأحداث
- **الخصائص**:
  - `result`: تحتوي على النتيجة عند نجاح الطلب.
  - `error`: تحتوي على معلومات حول الخطأ في حال فشل الطلب.
  - `source`: تشير إلى الكائن الذي تم إجراء الطلب عليه (مثل مخزن البيانات).

- **الأحداث**:
  - `onsuccess`: يتم استدعاؤه عند نجاح الطلب.
  - `onerror`: يتم استدعاؤه عند فشل الطلب.

## الأمثلة
### مثال 1: إنشاء قاعدة بيانات وطلب بيانات
```javascript
let request = indexedDB.open("MyDatabase", 1);

request.onupgradeneeded = function(event) {
    let db = event.target.result;
    db.createObjectStore("MyStore", { keyPath: "id" });
};

request.onsuccess = function(event) {
    let db = event.target.result;
    let transaction = db.transaction("MyStore", "readwrite");
    let store = transaction.objectStore("MyStore");
    let addRequest = store.add({ id: 1, name: "John Doe" });

    addRequest.onsuccess = function() {
        console.log("تمت إضافة البيانات بنجاح");
    };

    addRequest.onerror = function() {
        console.log("فشل إضافة البيانات");
    };
};

request.onerror = function() {
    console.log("فشل فتح قاعدة البيانات");
};
```

### مثال 2: قراءة بيانات من قاعدة البيانات
```javascript
let readRequest = indexedDB.open("MyDatabase");

readRequest.onsuccess = function(event) {
    let db = event.target.result;
    let transaction = db.transaction("MyStore", "readonly");
    let store = transaction.objectStore("MyStore");
    let getRequest = store.get(1);

    getRequest.onsuccess = function() {
        console.log("البيانات: ", getRequest.result);
    };

    getRequest.onerror = function() {
        console.log("فشل في قراءة البيانات");
    };
};
```

## الشرح
### المشاكل الشائعة
1. **الأخطاء في فتح قاعدة البيانات**: تأكد من أن اسم قاعدة البيانات والإصدار صحيحين عند فتح قاعدة البيانات.
2. **التعامل مع الأحداث**: يجب التأكد من التعامل مع أحداث النجاح والفشل بشكل صحيح لضمان استجابة التطبيق بشكل مناسب.
3. **تداخل الطلبات**: إذا كان لديك طلبات متعددة على نفس قاعدة البيانات، تأكد من إدارة المعاملات بشكل سليم لتفادي تعارض البيانات.

## ملخص بجملة واحدة
`IDBRequest` هو كائن أساسي في IndexedDB لجافا سكريبت، يتيح إجراء عمليات غير متزامنة لقراءة وكتابة البيانات في قاعدة بيانات غير علائقية.