<!--
Meta Description: # أحداث التخزين في JavaScript: فهم StorageEvent ## ملخص تُستخدم أحداث التخزين (StorageEvent) في JavaScript لإعلام التطبيقات عند حدوث تغييرات على التخز...
Meta Keywords: event, التخزين, javascript, localstorage, يتم
-->

# أحداث التخزين في JavaScript: فهم StorageEvent

## ملخص
تُستخدم أحداث التخزين (StorageEvent) في JavaScript لإعلام التطبيقات عند حدوث تغييرات على التخزين المحلي (localStorage) أو تخزين الجلسة (sessionStorage) في المتصفح. تعتبر هذه الأحداث مهمة لتطبيقات الويب التي تعتمد على البيانات المشتركة بين النوافذ أو علامات التبويب.

## الوثائق
### الغرض
تساعد أحداث التخزين في تحسين تجربة المستخدم من خلال السماح للتطبيقات بالتفاعل بشكل ديناميكي مع التغييرات في البيانات المخزنة. عندما يتم تغيير قيمة في التخزين المحلي أو تخزين الجلسة، يتم إطلاق حدث "storage".

### الاستخدام
يمكن التقاط أحداث التخزين باستخدام مستمعي الأحداث (event listeners) في JavaScript. يتم تنفيذ الكود داخل وظيفة مستمع الأحداث عند حدوث الحدث.

### التفاصيل
- **الحدث (event)**: يتضمن معلومات حول التغيير، مثل:
  - `key`: مفتاح العنصر الذي تم تغييره.
  - `newValue`: القيمة الجديدة للعنصر.
  - `oldValue`: القيمة القديمة للعنصر.
  - `url`: عنوان URL للصفحة التي قامت بإجراء التغيير.
  - `storageArea`: يشير إلى المنطقة التي تم تغييرها (localStorage أو sessionStorage).

### كيفية الاستخدام
تستطيع إضافة مستمع للحدث كما يلي:

```javascript
window.addEventListener('storage', function(event) {
    console.log('The key changed: ' + event.key);
    console.log('Old Value: ' + event.oldValue);
    console.log('New Value: ' + event.newValue);
    console.log('URL: ' + event.url);
});
```

## الأمثلة
### مثال 1: التقاط حدث التخزين
```javascript
// إضافة مستمع لحدث التخزين
window.addEventListener('storage', function(event) {
    alert(`تم تغيير المفتاح: ${event.key} من ${event.oldValue} إلى ${event.newValue}`);
});

// تغيير قيمة في localStorage
localStorage.setItem('username', 'JohnDoe');
```

### مثال 2: استخدام التخزين المحلي للتفاعل بين النوافذ
```javascript
// إضافة مستمع لحدث التخزين
window.addEventListener('storage', function(event) {
    if (event.key === 'counter') {
        console.log(`العداد الجديد: ${event.newValue}`);
    }
});

// تغيير القيمة في نافذة أخرى
localStorage.setItem('counter', 1);
```

## الشرح
### الأخطاء الشائعة
- **عدم عمل الحدث في نفس النافذة**: يجب أن يتم استدعاء `localStorage` أو `sessionStorage` من نافذة أو علامة تبويب مختلفة حتى يتم إطلاق حدث "storage".
- **تجاهل القيم القديمة**: في بعض الأحيان، قد ينسى المطورون التعامل مع القيم القديمة، مما قد يؤدي إلى سلوك غير متوقع في التطبيق.

### ملاحظات إضافية
- لا يتم إطلاق حدث التخزين عند التغييرات في نفس السياق (نفس النافذة أو علامة التبويب).
- يمكن أن يؤثر التخزين المشترك على الأداء، لذا يُفضل استخدامه بحذر.

## ملخص جملة واحدة
تعد أحداث التخزين في JavaScript وسيلة فعالة لمراقبة التغييرات في البيانات المخزنة بين نوافذ المتصفح أو علامات التبويب.