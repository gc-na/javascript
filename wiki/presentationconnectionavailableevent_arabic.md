<!--
Meta Description: # حدث PresentationConnectionAvailableEvent في JavaScript ## ملخص يعتبر حدث `PresentationConnectionAvailableEvent` جزءًا من واجهة API الخاصة بالعرض الت...
Meta Keywords: presentation, العرض, presentationconnectionavailableevent, javascript, اتصال
-->

# حدث PresentationConnectionAvailableEvent في JavaScript

## ملخص
يعتبر حدث `PresentationConnectionAvailableEvent` جزءًا من واجهة API الخاصة بالعرض التقديمي في JavaScript، ويستخدم لتحديد اتصالات العرض المتاحة بين الأجهزة.

## الوثائق
### الغرض
يتم استخدام `PresentationConnectionAvailableEvent` للإخطار بوجود اتصال عرض جديد متاح. هذا يمكن أن يكون مفيدًا في التطبيقات التي تتطلب عرض المحتوى على شاشات خارجية مثل أجهزة التلفاز أو شاشات العرض.

### الاستخدام
يتم تفعيل هذا الحدث عادةً عندما يتم إنشاء اتصال عرض جديد من قبل واجهة `Presentation`، مما يسمح للمستخدمين بالتفاعل مع المحتوى المعروض.

### التفاصيل
- **الحدث**: `PresentationConnectionAvailableEvent`
- **الخصائص**:
  - `connection`: يُرجع كائن `PresentationConnection` الذي يمثل الاتصال الجديد المتاح.
- **الاستماع للحدث**:
  يمكنك الاستماع لهذا الحدث عن طريق استخدام `addEventListener` على كائن `Presentation`.

## الأمثلة
### مثال أساسي
```javascript
const presentation = new Presentation();

presentation.addEventListener('connectionavailable', (event) => {
    console.log('اتصال عرض جديد متاح:', event.connection);
});

// بدء عملية البحث عن اتصالات العرض
presentation.startPresentation();
```

### مثال متقدم مع معالجة الأخطاء
```javascript
const presentation = new Presentation();

presentation.addEventListener('connectionavailable', (event) => {
    console.log('اتصال عرض جديد:', event.connection);
    
    // التعامل مع اتصال العرض
    event.connection.addEventListener('closed', () => {
        console.log('تم إغلاق الاتصال.');
    });
});

// بدء عملية البحث عن اتصالات العرض
presentation.startPresentation().catch((error) => {
    console.error('خطأ في بدء العرض:', error);
});
```

## الشرح
### الأخطاء الشائعة
- **عدم الاستماع للحدث**: تأكد من أنك تستمع لحدث `connectionavailable` بعد إنشاء كائن `Presentation`.
- **التعامل مع الاتصالات المغلقة**: تذكر أن تتعامل مع الأحداث مثل `closed` لضمان إدارة الاتصالات بشكل فعال.

### ملاحظات إضافية
- تأكد من أن الأجهزة متوافقة مع واجهة API الخاصة بالعرض التقديمي.
- قد لا يعمل هذا الحدث في جميع البيئات، لذا تحقق من التوافق مع المتصفحات المختلفة.

## ملخص في جملة واحدة
يعد حدث `PresentationConnectionAvailableEvent` في JavaScript أداة مهمة للكشف عن الاتصالات الجديدة المتاحة لعروض المحتوى بين الأجهزة.