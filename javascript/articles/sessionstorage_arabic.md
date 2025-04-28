<!--
Meta Description: # تخزين الجلسة (sessionStorage) في JavaScript: تخزين البيانات بسهولة ## نظرة عامة تعتبر خاصية `sessionStorage` في JavaScript وسيلة فعالة لتخزين البيان...
Meta Keywords: البيانات, sessionstorage, javascript, تخزين, json
-->

# تخزين الجلسة (sessionStorage) في JavaScript: تخزين البيانات بسهولة

## نظرة عامة
تعتبر خاصية `sessionStorage` في JavaScript وسيلة فعالة لتخزين البيانات في متصفح الويب خلال فترة جلسة المستخدم. يتم استخدام هذه الخاصية لتخزين البيانات المحلية التي تحتاج إلى البقاء متاحة أثناء تصفح المستخدم، ولكن لا تحتاج إلى أن تبقى بعد إغلاق نافذة المتصفح.

## الوثائق
### الغرض
تُستخدم `sessionStorage` لتخزين البيانات بشكل مؤقت في المتصفح. يتم حذف البيانات المخزنة في `sessionStorage` تلقائيًا عند إغلاق نافذة المتصفح. يمكن استخدامها لتخزين المعلومات مثل بيانات النموذج، إعدادات المستخدم، أو أي بيانات أخرى ترغب في الاحتفاظ بها مؤقتًا.

### الاستخدام
يمكن الوصول إلى `sessionStorage` من خلال كائن `window`، ويمكن استخدامه لتخزين واسترجاع البيانات باستخدام دوال `setItem` و`getItem` و`removeItem` و`clear`.

#### طريقة الاستخدام:
- **تخزين البيانات**: 
  ```javascript
  sessionStorage.setItem('key', 'value');
  ```

- **استرجاع البيانات**:
  ```javascript
  let value = sessionStorage.getItem('key');
  ```

- **حذف البيانات**:
  ```javascript
  sessionStorage.removeItem('key');
  ```

- **مسح جميع البيانات**:
  ```javascript
  sessionStorage.clear();
  ```

### التفاصيل
- **السعة**: `sessionStorage` تسمح بتخزين البيانات حتى 5-10 ميجابايت، حسب المتصفح.
- **البيانات**: يمكن أن تكون البيانات المخزنة نصية فقط، لذا يجب تحويل الكائنات إلى JSON باستخدام `JSON.stringify()` عند التخزين واسترجاعها باستخدام `JSON.parse()` عند الاسترجاع.
- **النطاق**: البيانات المخزنة في `sessionStorage` تظل متاحة فقط في نفس النطاق (domain) ونفس الجلسة، مما يعني أنها غير متاحة عبر نوافذ أو تبويبات مختلفة.

## أمثلة
### مثال 1: تخزين واسترجاع نص
```javascript
// تخزين البيانات
sessionStorage.setItem('username', 'أحمد');

// استرجاع البيانات
let username = sessionStorage.getItem('username');
console.log(username); // يطبع: أحمد
```

### مثال 2: تخزين كائن باستخدام JSON
```javascript
// كائن البيانات
let user = { name: 'أحمد', age: 25 };

// تخزين البيانات
sessionStorage.setItem('user', JSON.stringify(user));

// استرجاع البيانات
let retrievedUser = JSON.parse(sessionStorage.getItem('user'));
console.log(retrievedUser.name); // يطبع: أحمد
```

### مثال 3: حذف البيانات
```javascript
// حذف البيانات
sessionStorage.removeItem('username');
```

## الشرح
### الأخطاء الشائعة
- **تخزين الكائنات مباشرة**: لا يمكنك تخزين كائنات JavaScript مباشرةً في `sessionStorage`. يجب تحويلها إلى نص باستخدام `JSON.stringify()`.
- **تجاوز السعة**: عند محاولة تخزين بيانات تتجاوز الحد المسموح به، ستظهر رسالة خطأ. تأكد من إدارتك لحجم البيانات المخزنة.
- **عدم التوافق مع المتصفحات القديمة**: تأكد من أن البيئات التي تعمل عليها تدعم `sessionStorage`، حيث أن بعض المتصفحات القديمة قد لا تدعمها.

## ملخص في جملة واحدة
`sessionStorage` في JavaScript هي خاصية مثالية لتخزين البيانات مؤقتًا في المتصفح أثناء جلسة المستخدم، مما يساعد في تحسين تجربة المستخدم.