<!--
Meta Description: # IDBTransaction في JavaScript: كل ما تحتاج معرفته ## ملخص IDBTransaction هو واجهة في JavaScript تُستخدم لإدارة العمليات على قواعد بيانات IndexedDB، م...
Meta Keywords: البيانات, المعاملات, transaction, idbtransaction, على
-->

# IDBTransaction في JavaScript: كل ما تحتاج معرفته

## ملخص
IDBTransaction هو واجهة في JavaScript تُستخدم لإدارة العمليات على قواعد بيانات IndexedDB، مما يسمح بتنفيذ العمليات المتزامنة وغير المتزامنة بشكل آمن.

## الوثائق
IDBTransaction هو جزء من واجهة IndexedDB في JavaScript، ويُستخدم لإنشاء معاملة على قاعدة بيانات IndexedDB. تُعتبر المعاملات طريقة لضمان سلامة البيانات أثناء تنفيذ عمليات القراءة والكتابة. 

### الغرض
تهدف IDBTransaction إلى تقديم طريقة آمنة لتنفيذ العمليات المتعددة على قواعد البيانات، حيث تضمن أن العمليات إما أن تُنفذ بالكامل أو لا تُنفذ على الإطلاق، مما يحافظ على تكامل البيانات.

### الاستخدام
لإنشاء معاملة، يجب أولاً فتح اتصال بقاعدة البيانات باستخدام `indexedDB.open()`. بعد ذلك، يمكنك استخدام `transaction()` لإنشاء معاملة جديدة. يمكن أن تشمل المعاملات عمليات القراءة والكتابة على الكائنات المختلفة في قاعدة البيانات.

### التفاصيل
- **المستويات**: يمكن أن تكون المعاملات من نوع "readwrite" (للكتابة) أو "readonly" (للقراءة فقط).
- **التأثير**: إذا فشلت المعاملة، يتم التراجع عن جميع العمليات التي تم تنفيذها.
- **الأحداث**: توفر IDBTransaction مجموعة من الأحداث مثل `complete` و`error` و`abort`، والتي يمكن استخدامها لمعالجة نتائج المعاملات.

## أمثلة

### مثال بسيط لإنشاء معاملة
```javascript
const request = indexedDB.open('MyDatabase', 1);

request.onsuccess = function(event) {
    const db = event.target.result;
    const transaction = db.transaction(['MyObjectStore'], 'readwrite');
    const objectStore = transaction.objectStore('MyObjectStore');
    
    const requestAdd = objectStore.add({ id: 1, name: 'Sample Item' });
    
    requestAdd.onsuccess = function() {
        console.log('Item added successfully!');
    };
    
    transaction.oncomplete = function() {
        console.log('Transaction completed successfully.');
    };
    
    transaction.onerror = function(event) {
        console.log('Transaction failed: ', event.target.error);
    };
};
```

## الشرح
### مشكلات شائعة
- **فشل المعاملة**: قد تفشل المعاملة إذا كانت هناك مشكلات في الاتصال بقاعدة البيانات أو إذا كانت البيانات غير صحيحة.
- **انتظار المعاملات**: في حالة وجود معاملات متعددة، يجب إدارة التزامن بشكل صحيح لتجنب تعارضات البيانات.

### ملاحظات إضافية
- تأكد من فتح قاعدة البيانات قبل إنشاء المعاملات.
- استخدم الأحداث المتاحة في IDBTransaction لمعالجة نتائج المعاملات بشكل صحيح.

## ملخص من جملة واحدة
IDBTransaction في JavaScript هي واجهة تُستخدم لإدارة المعاملات على قواعد بيانات IndexedDB، مما يضمن تنفيذ العمليات بشكل آمن وموثوق.