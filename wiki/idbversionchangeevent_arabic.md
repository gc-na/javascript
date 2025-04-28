<!--
Meta Description: # IDBVersionChangeEvent في JavaScript: حدث تغير إصدار قاعدة البيانات ## ملخص IDBVersionChangeEvent هو حدث يُستخدم في واجهة برمجة التطبيقات IndexedDB ف...
Meta Keywords: البيانات, قاعدة, الإصدار, event, idbversionchangeevent
-->

# IDBVersionChangeEvent في JavaScript: حدث تغير إصدار قاعدة البيانات

## ملخص
IDBVersionChangeEvent هو حدث يُستخدم في واجهة برمجة التطبيقات IndexedDB في JavaScript، ويُشير إلى تغيير في إصدار قاعدة البيانات. يُعتبر هذا الحدث مهمًا عند التعامل مع التغييرات في هيكل قاعدة البيانات.

## الوثائق
يُستخدم IDBVersionChangeEvent للإشارة إلى أن إصدار قاعدة البيانات قد تغير. يحدث هذا الحدث عندما يتم فتح قاعدة بيانات موجودة بإصدار أعلى من الإصدار الحالي. يمكن أن يحدث أيضًا عند استدعاء `IDBOpenDBRequest` مع إصدار جديد.

### الغرض
يهدف IDBVersionChangeEvent إلى إعلام التطبيقات بأن قاعدة البيانات بحاجة إلى التحديث أو التغيير. يُعطي المطورين الفرصة للتعامل مع التغييرات المطلوبة في قاعدة البيانات.

### الاستخدام
للاستفادة من IDBVersionChangeEvent، يجب على المطورين الاستماع لهذا الحدث عند فتح قاعدة البيانات. يمكن استخدامه لتحديث الجداول أو إضافة متطلبات جديدة.

### التفاصيل
- **النوع**: IDBVersionChangeEvent
- **الخصائص**:
  - `oldVersion`: الرقم الإصدار السابق لقاعدة البيانات.
  - `newVersion`: الرقم الإصدار الجديد لقاعدة البيانات.

## الأمثلة

### مثال 1: التعامل مع حدث تغيير الإصدار
```javascript
const request = indexedDB.open("MyDatabase", 2);

request.onupgradeneeded = function(event) {
    const db = event.target.result;
    const oldVersion = event.oldVersion;
    const newVersion = event.newVersion;

    console.log(`تغيير من الإصدار ${oldVersion} إلى ${newVersion}`);
    
    // هنا يمكنك إضافة الجداول الجديدة أو تعديل الهيكل
    if (oldVersion < 2) {
        db.createObjectStore("newStore", { keyPath: "id" });
    }
};
```

### مثال 2: تسجيل حدث تغيير الإصدار
```javascript
const request = indexedDB.open("MyDatabase", 3);

request.onsuccess = function(event) {
    const db = event.target.result;
    console.log("تم فتح قاعدة البيانات بنجاح.");
};

request.onupgradeneeded = function(event) {
    const db = event.target.result;
    console.log(`تغيير الإصدار: ${event.oldVersion} إلى ${event.newVersion}`);
};
```

## الشرح
عند التعامل مع IDBVersionChangeEvent، يجب أن تكون على دراية ببعض النقاط التي قد تسبب مشاكل:
- **عدم التوافق**: إذا كنت تستخدم إصدارًا قديمًا من قاعدة البيانات، قد تواجه مشاكل في التوافق مع المتصفحات الحديثة.
- **عدم معالجة البيانات**: يجب التأكد من معالجة البيانات بشكل صحيح عند تغيير الإصدار، حيث يمكن أن تؤدي التغييرات غير المدروسة إلى فقدان البيانات.
- **تعدد النوافذ**: إذا كان هناك نوافذ متعددة تتعامل مع نفس قاعدة البيانات، قد يحدث تعارض في الإصدار.

## ملخص جملة واحدة
IDBVersionChangeEvent في JavaScript يُستخدم للإشارة إلى تغييرات الإصدار في قاعدة البيانات، مما يتيح للمطورين تحديث الهيكل عند الحاجة.