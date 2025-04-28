<!--
Meta Description: # IDBOpenDBRequest في جافا سكريبت: كل ما تحتاج لمعرفته ## ملخص IDBOpenDBRequest هو كائن يُستخدم في واجهة برمجة التطبيقات IndexedDB في جافا سكريبت، حيث...
Meta Keywords: قاعدة, البيانات, indexeddb, فتح, request
-->

# IDBOpenDBRequest في جافا سكريبت: كل ما تحتاج لمعرفته

## ملخص
IDBOpenDBRequest هو كائن يُستخدم في واجهة برمجة التطبيقات IndexedDB في جافا سكريبت، حيث يُعتبر وسيلة لفتح قواعد بيانات IndexedDB والتعامل معها بشكل غير متزامن.

## الوثائق
IDBOpenDBRequest هو كائن يُنشأ عند محاولة فتح قاعدة بيانات باستخدام الدالة `indexedDB.open()`. يُستخدم هذا الكائن للتحكم في حالة فتح قاعدة البيانات، وتلقي ردود الفعل حول نجاح العملية أو فشلها.

### الغرض
يهدف IDBOpenDBRequest إلى تسهيل عملية فتح قواعد البيانات من خلال تقديم واجهة غير متزامنة تسمح للمطورين بالتعامل مع البيانات بشكل متزامن.

### الاستخدام
لفتح قاعدة بيانات، يمكنك استخدام الكود التالي:

```javascript
let request = indexedDB.open("اسم_القاعدة", رقم_الإصدار);
```

### التفاصيل
- **الخصائص**:
  - `result`: تحتوي على قاعدة البيانات المفتوحة إذا كانت العملية ناجحة.
  - `error`: تحتوي على الخطأ إذا فشلت العملية.
  
- **الأحداث**:
  - `onsuccess`: يتم استدعاؤه عند نجاح فتح قاعدة البيانات.
  - `onerror`: يتم استدعاؤه عند فشل العملية.

## أمثلة
### مثال أساسي لفتح قاعدة بيانات
```javascript
let request = indexedDB.open("مكتبة", 1);

request.onsuccess = function(event) {
  let db = event.target.result;
  console.log("قاعدة البيانات مفتوحة:", db);
};

request.onerror = function(event) {
  console.error("فشل في فتح قاعدة البيانات:", event.target.error);
};
```

### مثال مع ترقية قاعدة البيانات
```javascript
let request = indexedDB.open("مكتبة", 2);

request.onupgradeneeded = function(event) {
  let db = event.target.result;
  let objectStore = db.createObjectStore("كتب", { keyPath: "id" });
};

request.onsuccess = function(event) {
  console.log("قاعدة البيانات تم ترقيتها بنجاح");
};
```

## الشرح
- **المشاكل الشائعة**:
  - تأكد من أن اسم قاعدة البيانات ورقم الإصدار صحيحين، لأن الأخطاء في هذه القيم قد تؤدي إلى فشل فتح قاعدة البيانات.
  - تحقق من دعم المستعرض لـ IndexedDB، حيث قد لا تدعم بعض المتصفحات القديمة هذه الواجهة.

- **نصائح إضافية**:
  - يجب عليك دائمًا التعامل مع الأحداث `onsuccess` و `onerror` لضمان معالجة الأخطاء بشكل صحيح.
  - يمكن استخدام `onupgradeneeded` لإنشاء أو ترقية المخازن عند فتح قاعدة البيانات.

## ملخص جملة واحدة
IDBOpenDBRequest هو كائن في جافا سكريبت يُستخدم لفتح قواعد بيانات IndexedDB بشكل غير متزامن والتعامل مع نتائج العملية.