<!--
Meta Description: # حدث تغيير إدخال التنقل (NavigationCurrentEntryChangeEvent) في JavaScript: كل ما تحتاج معرفته ## الملخص حدث تغيير إدخال التنقل (NavigationCurrentEntr...
Meta Keywords: التنقل, تغيير, الإدخال, حدث, إدخال
-->

# حدث تغيير إدخال التنقل (NavigationCurrentEntryChangeEvent) في JavaScript: كل ما تحتاج معرفته

## الملخص
حدث تغيير إدخال التنقل (NavigationCurrentEntryChangeEvent) هو حدث يتيح للمطورين مراقبة تغييرات الإدخالات في تاريخ التصفح. يستخدم هذا الحدث بشكل شائع في تطبيقات الويب الحديثة لتحسين تجربة المستخدم من خلال إدارة التنقل بشكل أكثر كفاءة.

## الوثائق
### الغرض
يستخدم حدث تغيير إدخال التنقل لمراقبة تغييرات الإدخالات الحالية في سجل التنقل. يمكن للمطورين استخدام هذا الحدث للتفاعل مع تغييرات الحالة في تطبيقاتهم، مما يسمح بتحديث واجهة المستخدم أو بيانات التطبيق عند تغيير الإدخال.

### الاستخدام
يمكن الوصول إلى حدث تغيير إدخال التنقل من خلال واجهة `Navigation`, وهو جزء من واجهة برمجة التطبيقات الخاصة بالتاريخ (History API) في JavaScript. يتم تفعيل هذا الحدث عندما يتغير الإدخال الحالي في سجل التنقل، مما يتيح للمطورين تنفيذ إجراءات معينة بناءً على هذه التغييرات.

### التفاصيل
- **الحدث**: `NavigationCurrentEntryChangeEvent`
- **الخصائص**: 
  - `entry`: يوفر معلومات حول الإدخال الحالي الجديد.
  - `previousEntry`: يوفر معلومات حول الإدخال السابق.

## الأمثلة
### مثال 1: الاستماع لحدث تغيير إدخال التنقل
```javascript
window.addEventListener('navigationcurrententrychange', function(event) {
    console.log('تم تغيير الإدخال الحالي:', event.entry);
    console.log('الإدخال السابق:', event.previousEntry);
});
```

### مثال 2: توجيه المستخدم بناءً على الإدخال الحالي
```javascript
window.addEventListener('navigationcurrententrychange', function(event) {
    if (event.entry.url === 'https://example.com/page2') {
        // تنفيذ شيء معين عند الانتقال إلى page2
        alert('لقد انتقلت إلى الصفحة 2!');
    }
});
```

## الشرح
### الفخاخ الشائعة والملاحظات
- **التوافق**: تأكد من التحقق من دعم المتصفح لواجهة برمجة التطبيقات الخاصة بالتاريخ قبل استخدام هذا الحدث، حيث قد لا تتوفر في جميع المتصفحات.
- **الأداء**: عند التعامل مع أحداث كثيرة، من المهم إدارة الأحداث بشكل صحيح لتجنب التأثير على أداء التطبيق.
- **التغييرات المفاجئة**: قد يؤدي التفاعل مع تغييرات الإدخالات إلى سلوك غير متوقع إذا لم يتم التعامل مع الحالات الخاصة بشكل صحيح.

## ملخص من جملة واحدة
حدث تغيير إدخال التنقل (NavigationCurrentEntryChangeEvent) في JavaScript يمكن المطورين من مراقبة تغييرات الإدخالات في سجل التنقل، مما يعزز تجربة المستخدم في تطبيقات الويب.