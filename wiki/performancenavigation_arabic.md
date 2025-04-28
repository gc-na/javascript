<!--
Meta Description: # PerformanceNavigation في JavaScript: تحسين أداء تطبيقات الويب ## ملخص PerformanceNavigation هو كائن في واجهة برمجة التطبيقات للأداء (Performance API...
Meta Keywords: performancenavigation, navigation, performance, تحميل, الصفحة
-->

# PerformanceNavigation في JavaScript: تحسين أداء تطبيقات الويب

## ملخص
PerformanceNavigation هو كائن في واجهة برمجة التطبيقات للأداء (Performance API) في JavaScript، يسمح للمطورين بجمع معلومات حول كيفية تحميل صفحة الويب. هذه المعلومات تساعد في تحسين أداء التطبيقات وضمان تجربة مستخدم أفضل.

## التوثيق
### الغرض
يهدف PerformanceNavigation إلى توفير معلومات حول كيفية تنقل المستخدم إلى الصفحة. يتضمن هذا معلومات حول نوع التحميل (مثل التحميل الأولي، إعادة التحميل، أو الانتقال من صفحة أخرى).

### الاستخدام
يمكن الوصول إلى PerformanceNavigation من خلال `performance.navigation`. الكائن الناتج يحتوي على خصائص تعكس نوع التصفح:

- `type`: نوع التنقل، والذي يمكن أن يكون واحدًا من القيم التالية:
  - `0`: التحميل العادي (فرصة تحميل الصفحة لأول مرة).
  - `1`: إعادة تحميل الصفحة.
  - `2`: الانتقال من صفحة أخرى.

### التفاصيل
للوصول إلى PerformanceNavigation، يمكن استخدام الشيفرة التالية:

```javascript
const navigation = performance.navigation;
console.log(navigation.type);
```

## الأمثلة
### مثال 1: التحقق من نوع التنقل
```javascript
if (performance.navigation.type === performance.navigation.TYPE_NAVIGATE) {
    console.log("تم تحميل الصفحة لأول مرة.");
} else if (performance.navigation.type === performance.navigation.TYPE_RELOAD) {
    console.log("تم إعادة تحميل الصفحة.");
}
```

### مثال 2: استخدام PerformanceNavigation لتخصيص تجربة المستخدم
```javascript
if (performance.navigation.type === 1) {
    alert("مرحبا بعودتك! تم إعادة تحميل الصفحة.");
} else {
    alert("مرحبًا بك في موقعنا!");
}
```

## الشرح
### الأخطاء الشائعة
- **عدم التحقق من وجود الكائن**: بعض المتصفحات قد لا تدعم PerformanceNavigation. تأكد من التحقق من وجود الكائن قبل استخدامه.
- **عدم فهم قيم `type`**: يجب فهم القيم المختلفة لـ `type` لتجنب الأخطاء في منطق التطبيق.

### ملاحظات إضافية
- PerformanceNavigation تم إهماله في بعض المتصفحات الحديثة، لذا من الأفضل استخدام واجهات برمجة التطبيقات الأخرى لجمع معلومات الأداء.
- قد يكون من المفيد دمج PerformanceNavigation مع أدوات التحليل الأخرى للحصول على رؤى أعمق حول أداء الصفحة.

## ملخص جملة واحدة
PerformanceNavigation في JavaScript يوفر معلومات قيمة حول كيفية تحميل الصفحات، مما يساعد في تحسين تجربة المستخدم.