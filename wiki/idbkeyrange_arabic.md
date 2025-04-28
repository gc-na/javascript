<!--
Meta Description: # IDBKeyRange في JavaScript: دليل شامل ## ملخص `IDBKeyRange` هو كائن في JavaScript يُستخدم مع واجهة IndexedDB لتسهيل عمليات البحث عن البيانات ضمن نطاق...
Meta Keywords: idbkeyrange, let, استخدام, لتحديد, request
-->

# IDBKeyRange في JavaScript: دليل شامل

## ملخص
`IDBKeyRange` هو كائن في JavaScript يُستخدم مع واجهة IndexedDB لتسهيل عمليات البحث عن البيانات ضمن نطاق محدد. يسمح لك بتحديد مفاتيح البحث ضمن قاعدة بيانات IndexedDB بطريقة مرنة وفعالة.

## الوثائق
يهدف `IDBKeyRange` إلى توفير واجهة سهلة لتحديد نطاق من المفاتيح التي يمكن استخدامها في عمليات قراءة البيانات من IndexedDB. يتم استخدامه في الدوال مثل `openCursor()` و `getAll()` لتصفية النتائج بناءً على القيم المحددة.

### الاستخدام
لإنشاء `IDBKeyRange`، يمكن استخدام الميثودات التالية:
- `IDBKeyRange.only(value)`: تُستخدم لتحديد نطاق يتضمن قيمة واحدة فقط.
- `IDBKeyRange.lowerBound(lower, open)`: تُستخدم لتحديد حد أدنى للنطاق، مع خيار لتحديد ما إذا كان هذا الحد مفتوحًا أم لا.
- `IDBKeyRange.upperBound(upper, open)`: تُستخدم لتحديد حد أعلى للنطاق، مع خيار لتحديد ما إذا كان هذا الحد مفتوحًا أم لا.
- `IDBKeyRange.bound(lower, upper, lowerOpen, upperOpen)`: تُستخدم لتحديد نطاق من حدين، مع خيارات لتحديد ما إذا كانت الحدود مفتوحة.

### تفاصيل الاستخدام
عند استخدام `IDBKeyRange`، تأكد من استخدام القيم الصحيحة التي تتناسب مع نوع البيانات المخزنة في قاعدة البيانات. من المهم أيضًا معالجة الاستثناءات التي قد تحدث عند استخدام المفاتيح غير الصحيحة.

## أمثلة
### مثال 1: استخدام `IDBKeyRange.only()`
```javascript
let request = indexedDB.open("MyDatabase");

request.onsuccess = function(event) {
    let db = event.target.result;
    let transaction = db.transaction(["MyStore"], "readonly");
    let objectStore = transaction.objectStore("MyStore");
    
    let keyRange = IDBKeyRange.only("myKey");
    let request = objectStore.getAll(keyRange);

    request.onsuccess = function(event) {
        console.log(event.target.result);
    };
};
```

### مثال 2: استخدام `IDBKeyRange.lowerBound()`
```javascript
let keyRange = IDBKeyRange.lowerBound(100);
let request = objectStore.openCursor(keyRange);

request.onsuccess = function(event) {
    let cursor = event.target.result;
    if (cursor) {
        console.log(cursor.value);
        cursor.continue();
    }
};
```

### مثال 3: استخدام `IDBKeyRange.bound()`
```javascript
let keyRange = IDBKeyRange.bound(10, 20);
let request = objectStore.openCursor(keyRange);

request.onsuccess = function(event) {
    let cursor = event.target.result;
    if (cursor) {
        console.log(cursor.value);
        cursor.continue();
    }
};
```

## الشرح
- **المشاكل الشائعة:** تأكد من أن المفاتيح المستخدمة تتناسب مع نوع البيانات في المخزن. استخدام مفاتيح غير صحيحة أو عدم توافق الأنواع قد يؤدي إلى أخطاء في التنفيذ.
- **نقاط يجب الانتباه إليها:** عند استخدام `lowerOpen` و `upperOpen`، تأكد من فهم كيفية تأثيرها على النتائج المسترجعة، حيث أن القيم المفتوحة ستستبعد الحدود المحددة.

## ملخص بجملة واحدة
`IDBKeyRange` هو كائن حيوي في JavaScript يُستخدم مع IndexedDB لتمكين عمليات البحث ضمن نطاقات محددة من المفاتيح بطريقة مرنة وفعالة.