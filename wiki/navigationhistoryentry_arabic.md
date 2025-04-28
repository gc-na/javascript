<!--
Meta Description: # NavigationHistoryEntry في JavaScript: توثيق شامل ## ملخص `NavigationHistoryEntry` هو كائن في JavaScript يمثل مدخلًا في تاريخ التنقل للمتصفح، ويستخدم...
Meta Keywords: navigationhistoryentry, عنوان, history, javascript, إلى
-->

# NavigationHistoryEntry في JavaScript: توثيق شامل

## ملخص
`NavigationHistoryEntry` هو كائن في JavaScript يمثل مدخلًا في تاريخ التنقل للمتصفح، ويستخدم لتوفير المعلومات حول الصفحات التي تم زيارتها.

## التوثيق
### الغرض
يهدف `NavigationHistoryEntry` إلى تمكين المطورين من الوصول إلى معلومات الصفحات التي تم التنقل إليها، مما يسهل إدارة تجربة المستخدم في التطبيقات التي تعتمد على التصفح.

### الاستخدام
يمكن استخدام `NavigationHistoryEntry` في سياق واجهة برمجة التطبيقات (API) الخاصة بالتاريخ، حيث يوفر معلومات مثل عنوان الصفحة ورابطها. يمكن الوصول إلى كائنات `NavigationHistoryEntry` من خلال واجهة `History` في المتصفح.

### التفاصيل
- **الخصائص**:
  - `url`: يحدد عنوان URL للمدخل في تاريخ التنقل.
  - `title`: يعرض عنوان الصفحة كما هو معروض في شريط العنوان.
  
- **طرق الاستخدام**:
لا توجد طرق محددة لكائن `NavigationHistoryEntry`، حيث يتم استخدامه بشكل غير مباشر عبر واجهة `History`.

## الأمثلة
### مثال 1: الوصول إلى عنوان URL
```javascript
if (window.history.state) {
    let navigationEntry = window.history.state;
    console.log(navigationEntry.url); // طباعة عنوان URL
}
```

### مثال 2: عرض عنوان الصفحة
```javascript
if (window.history.state) {
    let navigationEntry = window.history.state;
    document.title = navigationEntry.title; // تعيين عنوان الصفحة
}
```

## الشرح
### الفخاخ الشائعة
- **عدم التوافق**: `NavigationHistoryEntry` قد لا يكون مدعومًا في جميع المتصفحات، لذا من المهم التحقق من التوافق.
- **الإعدادات الخاطئة**: قد يؤدي الاستخدام غير الصحيح لـ `window.history.state` إلى الحصول على معلومات غير صحيحة.

### ملاحظات إضافية
- يمكن أن تتغير المعلومات في `NavigationHistoryEntry` بناءً على التفاعلات المختلفة للمستخدم، لذا يجب التعامل معها بحذر.
- يُفضل استخدام هذه الواجهة في تطبيقات الويب التي تتطلب إدارة معقدة للتاريخ.

## ملخص جملة واحدة
`NavigationHistoryEntry` في JavaScript هو كائن يوفر معلومات حول مدخلات تاريخ التنقل، مما يسهل إدارة تجربة المستخدم.