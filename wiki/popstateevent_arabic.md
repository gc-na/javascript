<!--
Meta Description: # حدث PopStateEvent في JavaScript: فهم شامل ## ملخص يعد حدث `PopStateEvent` جزءًا أساسيًا من واجهة برمجة تطبيقات التاريخ (History API) في JavaScript، ...
Meta Keywords: event, الحالة, popstate, javascript, state
-->

# حدث PopStateEvent في JavaScript: فهم شامل

## ملخص
يعد حدث `PopStateEvent` جزءًا أساسيًا من واجهة برمجة تطبيقات التاريخ (History API) في JavaScript، حيث يُستخدم لتتبع تغييرات الحالة في سجل المتصفح عندما يتنقل المستخدم بين الصفحات باستخدام زر الرجوع أو الأمام.

## الوثائق
### الغرض
يتم إنشاء حدث `PopStateEvent` عندما يتم استدعاء `history.pushState()` أو `history.replaceState()`، ويُستخدم في الغالب لتحديث واجهة المستخدم بناءً على حالة جديدة دون إعادة تحميل الصفحة.

### الاستخدام
للاستماع إلى حدث `popstate`، يمكنك استخدام `window.addEventListener()` كما يلي:

```javascript
window.addEventListener('popstate', function(event) {
    // التعامل مع حدث popstate
    console.log('تمت استعادة الحالة:', event.state);
});
```

### التفاصيل
- **متغير `event.state`**: يحتوي على بيانات الحالة المرتبطة بالتاريخ. يمكن أن تكون هذه البيانات كائنات JavaScript تم تمريرها عند استدعاء `pushState()` أو `replaceState()`.
- **تعدد الأحداث**: يتم استدعاء `popstate` فقط عندما ينتقل المستخدم إلى حالة سابقة أو لاحقة في سجل التاريخ. لا يتم استدعاؤه عند تحميل الصفحة لأول مرة.
- **التوافق**: مدعوم في معظم المتصفحات الحديثة ولكنه قد يتطلب تجريبية في بعض الإصدارات القديمة.

## الأمثلة
### مثال 1: استخدام PushState
```javascript
// إضافة حالة جديدة إلى السجل
history.pushState({ page: 1 }, 'عنوان الصفحة 1', '?page=1');

// الاستماع لحدث popstate
window.addEventListener('popstate', function(event) {
    if (event.state) {
        console.log('تمت استعادة الحالة:', event.state);
    }
});
```

### مثال 2: استخدام ReplaceState
```javascript
// استبدال الحالة الحالية
history.replaceState({ page: 2 }, 'عنوان الصفحة 2', '?page=2');

window.addEventListener('popstate', function(event) {
    console.log('تمت استعادة الحالة:', event.state);
});
```

## الشرح
### الأخطاء الشائعة
- **عدم استجابة الحدث في أول تحميل**: كما ذُكر سابقًا، لا يتم استدعاء `popstate` عند تحميل الصفحة لأول مرة، لذا يجب التأكد من التعامل مع الحالة الافتراضية.
- **عدم وجود بيانات في `event.state`**: إذا لم يتم تمرير حالة عند استخدام `pushState` أو `replaceState`، فإن `event.state` سيكون `null`.

### ملاحظات إضافية
- يجب توخي الحذر عند إدارة تاريخ المتصفح، حيث يمكن أن تؤدي التغييرات غير المدروسة إلى سلوك غير متوقع.
- يُفضل استخدام `event.preventDefault()` لمنع السلوك الافتراضي للروابط إذا كنت تتعامل مع التنقل في الصفحة بشكل ديناميكي.

## ملخص جملة واحدة
يعد `PopStateEvent` أداة مهمة في JavaScript لتتبع تغييرات الحالة في سجل المتصفح، مما يسمح بتطبيقات الويب الديناميكية والتفاعلية.