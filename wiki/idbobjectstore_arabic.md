<!--
Meta Description: # IDBObjectStore في JavaScript: دليلك الشامل لتخزين البيانات ## ملخص IDBObjectStore هو واجهة في قاعدة بيانات IndexedDB في JavaScript، تُستخدم لتخزين ك...
Meta Keywords: let, idbobjectstore, request, البيانات, objectstore
-->

# IDBObjectStore في JavaScript: دليلك الشامل لتخزين البيانات

## ملخص 
IDBObjectStore هو واجهة في قاعدة بيانات IndexedDB في JavaScript، تُستخدم لتخزين كائنات البيانات بشكل منظم، مما يتيح للمطورين إمكانية البحث عن البيانات واسترجاعها بطريقة فعالة وسريعة.

## الوثائق
### الغرض
IDBObjectStore هو جزء أساسي من واجهة برمجة التطبيقات IndexedDB، والتي تُستخدم لتخزين البيانات في المتصفح. تتيح لك هذه الواجهة تخزين الكائنات بطرق مرنة، مما يجعلها مثالية لتطبيقات الويب التي تحتاج إلى تخزين بيانات محلية.

### الاستخدام
لإنشاء IDBObjectStore، يجب أولاً فتح قاعدة بيانات باستخدام `indexedDB.open()`. بعد ذلك، يمكنك إنشاء كائن التخزين باستخدام `createObjectStore()` داخل حدث `onupgradeneeded`. يُمكنك تحديد خيارات مثل المفتاح الأساسي وقدرات التخزين.

### التفاصيل
- **التخزين**: يدعم IDBObjectStore تخزين الكائنات بخصائص متعددة، مما يسهل استرجاع البيانات.
- **المفاتيح**: يمكن استخدام مفاتيح طبيعية أو توليد مفاتيح تلقائياً.
- **عمليات CRUD**: يدعم IDBObjectStore العمليات الأساسية للإنشاء، القراءة، التحديث، والحذف.
  
## الأمثلة
### إنشاء قاعدة بيانات وكائن تخزين
```javascript
let request = indexedDB.open("myDatabase", 1);

request.onupgradeneeded = function(event) {
    let db = event.target.result;
    let objectStore = db.createObjectStore("myObjectStore", { keyPath: "id" });
};

request.onsuccess = function(event) {
    let db = event.target.result;
    console.log("Database opened successfully");
};
```

### إضافة كائن إلى الكائن التخزين
```javascript
let transaction = db.transaction(["myObjectStore"], "readwrite");
let objectStore = transaction.objectStore("myObjectStore");

let data = { id: 1, name: "John Doe" };
let request = objectStore.add(data);

request.onsuccess = function() {
    console.log("Data added successfully");
};
```

### استرجاع كائن من الكائن التخزين
```javascript
let transaction = db.transaction(["myObjectStore"]);
let objectStore = transaction.objectStore("myObjectStore");

let request = objectStore.get(1);
request.onsuccess = function() {
    console.log("Data retrieved:", request.result);
};
```

## الشرح
### الأخطاء الشائعة
- **عدم وجود قاعدة بيانات**: تأكد من أنك قد أنشأت قاعدة البيانات قبل محاولة إنشاء كائن التخزين.
- **إعدادات المفتاح**: يجب أن يكون لديك مفتاح أساسي لكل كائن، وإلا سيفشل الطلب.
- **التعامل مع الأخطاء**: تأكد من إضافة معالجات للأخطاء باستخدام `onerror` لمعرفة ما إذا حدث شيء غير متوقع.

### ملاحظات إضافية
- IDBObjectStore لا يدعم العمليات المتزامنة. تأكد من استخدام المعاملات بشكل صحيح لتفادي أي مشاكل.
- قد تكون عمليات القراءة والكتابة بطيئة في بعض الحالات، لذا يُفضل التعامل مع البيانات بشكل غير متزامن.

## ملخص في جملة واحدة
IDBObjectStore في JavaScript هو واجهة تخزين قوية تسمح بتخزين الكائنات واسترجاعها بكفاءة في تطبيقات الويب.