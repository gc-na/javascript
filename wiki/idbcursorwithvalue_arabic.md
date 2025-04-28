<!--
Meta Description: # IDBCursorWithValue في جافا سكريبت: دليل شامل ## ملخص IDBCursorWithValue هو واجهة في واجهة برمجة تطبيقات IndexedDB في جافا سكريبت، والتي تُستخدم للتن...
Meta Keywords: cursor, let, إلى, event, idbcursorwithvalue
-->

# IDBCursorWithValue في جافا سكريبت: دليل شامل

## ملخص
IDBCursorWithValue هو واجهة في واجهة برمجة تطبيقات IndexedDB في جافا سكريبت، والتي تُستخدم للتنقل عبر نتائج الاستعلامات في قاعدة بيانات IndexedDB واسترجاع القيم المرتبطة بالمؤشر.

## الوثائق
### الغرض
IDBCursorWithValue يُستخدم لتوفير واجهة مريحة للتنقل عبر كائنات قاعدة البيانات واسترجاع القيم المرتبطة بكل عنصر دون الحاجة إلى استدعاء استعلامات إضافية. يُعتبر هذا مفيدًا عندما تحتاج إلى الوصول إلى البيانات المرتبطة بمؤشر معين أثناء التنقل عبر النتائج.

### الاستخدام
يمكنك استخدام IDBCursorWithValue لإنشاء مؤشر على كائن التخزين (Object Store) في IndexedDB. يتم إنشاؤه عادةً باستخدام دالة `openCursor()`، والتي يمكن أن تأخذ مجموعة من المعايير مثل نطاق البحث (range) أو نوع المؤشر.

### التفاصيل
- **الخصائص:**
  - `value`: تُرجع القيمة الحالية للمؤشر.
  
- **الطرق:**
  - `.continue()`: يستمر في المؤشر إلى العنصر التالي.
  - `.update()`: يُستخدم لتحديث القيمة المرتبطة بالمؤشر.
  - `.delete()`: يُستخدم لحذف العنصر الحالي من التخزين.

## الأمثلة
### مثال أساسي
```javascript
let request = indexedDB.open("MyDatabase");

request.onsuccess = function(event) {
    let db = event.target.result;
    let transaction = db.transaction("MyObjectStore", "readonly");
    let objectStore = transaction.objectStore("MyObjectStore");
    let cursorRequest = objectStore.openCursor();

    cursorRequest.onsuccess = function(event) {
        let cursor = event.target.result;
        if (cursor) {
            console.log("Key: " + cursor.key + ", Value: " + cursor.value);
            cursor.continue();
        } else {
            console.log("No more entries!");
        }
    };
};
```

### مثال مع IDBCursorWithValue
```javascript
let request = indexedDB.open("MyDatabase");

request.onsuccess = function(event) {
    let db = event.target.result;
    let transaction = db.transaction("MyObjectStore", "readonly");
    let objectStore = transaction.objectStore("MyObjectStore");
    let cursorRequest = objectStore.openCursor();

    cursorRequest.onsuccess = function(event) {
        let cursor = event.target.result;
        if (cursor) {
            console.log("Key: " + cursor.key + ", Value: " + cursor.value);
            cursor.continue();
        } else {
            console.log("End of cursor!");
        }
    };
};
```

## الشرح
### الأخطاء الشائعة
- **عدم التحقق من وجود قيم:** يجب التأكد من أن `cursor` ليس فارغًا قبل محاولة الوصول إلى خصائصه. إذا كان `cursor` فارغًا، سيؤدي ذلك إلى أخطاء في التنفيذ.
  
- **تداخل العمليات:** في حالة وجود عمليات متعددة على نفس قاعدة البيانات، يجب التأكد من أن المعاملات لا تتداخل، حيث يمكن أن تؤدي إلى سلوك غير متوقع.

### ملاحظات إضافية
IDBCursorWithValue يُعتبر أداة قوية للتنقل في البيانات، لكنه يحتاج إلى إدارة دقيقة للمؤشرات والمعاملات لتجنب الأخطاء.

## ملخص بسط
IDBCursorWithValue يسمح بالتنقل السلس عبر نتائج IndexedDB واسترجاع القيم المرتبطة بكل عنصر بشكل فعال.