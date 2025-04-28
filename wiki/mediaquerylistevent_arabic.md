<!--
Meta Description: # MediaQueryListEvent في جافا سكريبت: فهم الأحداث المتعلقة باستعلامات الوسائط ## الملخص MediaQueryListEvent هو كائن في جافا سكريبت يُستخدم للاستجابة ل...
Meta Keywords: mediaquerylistevent, الوسائط, mediaquerylist, استعلام, استعلامات
-->

# MediaQueryListEvent في جافا سكريبت: فهم الأحداث المتعلقة باستعلامات الوسائط

## الملخص
MediaQueryListEvent هو كائن في جافا سكريبت يُستخدم للاستجابة للتغيرات في استعلامات الوسائط (Media Queries) والتي تُستخدم بشكل شائع في تصميم واجهات المستخدم المتجاوبة.

## التوثيق
### الغرض
MediaQueryListEvent يمثل حدثًا يُطلق عندما يتغير حالة استعلام الوسائط، مثل الانتقال من حالة "مطبقة" إلى "غير مطبقة" أو العكس. هذا يسمح للمطورين بتعديل محتوى الصفحة أو تنسيقها بناءً على حجم الشاشة أو خصائص العرض الأخرى.

### الاستخدام
يمكن استخدام MediaQueryListEvent بالتزامن مع `matchMedia` لإنشاء استعلامات وسائط. عندما يتغير استعلام الوسائط، يتم إطلاق حدث `change`، مما يتيح لك تنفيذ وظائف معينة.

### التفاصيل
- **الإنشاء**: يتم إنشاء MediaQueryListEvent تلقائيًا بواسطة المتصفح.
- **الخصائص**:
  - `matches`: خاصية تشير إلى ما إذا كان استعلام الوسائط مطبقًا حاليًا.
  - `media`: خاصية تحتوي على سلسلة تمثل استعلام الوسائط المرتبط بالحدث.

## الأمثلة

### مثال 1: استخدام MediaQueryListEvent
```javascript
const mediaQueryList = window.matchMedia('(max-width: 600px)');

function handleChange(event) {
    if (event.matches) {
        console.log('الشاشة أقل من 600px');
    } else {
        console.log('الشاشة أكبر من 600px');
    }
}

// إضافة مستمع حدث
mediaQueryList.addEventListener('change', handleChange);

// استدعاء الوظيفة في البداية
handleChange(mediaQueryList);
```

### مثال 2: استعلام وسائط متعددة
```javascript
const mediaQueryList = window.matchMedia('(prefers-color-scheme: dark)');

function handleColorSchemeChange(event) {
    if (event.matches) {
        document.body.classList.add('dark-mode');
    } else {
        document.body.classList.remove('dark-mode');
    }
}

mediaQueryList.addEventListener('change', handleColorSchemeChange);
handleColorSchemeChange(mediaQueryList);
```

## الشرح
### المشاكل الشائعة
1. **عدم التوافق مع المتصفحات**: تأكد من أن المتصفح الذي تعمل به يدعم MediaQueryListEvent، حيث قد لا تدعمه بعض الإصدارات القديمة.
2. **عدم إضافة مستمع الحدث**: إذا لم تقم بإضافة مستمع حدث، فلن يتم استجابة الصفحة للتغييرات في استعلامات الوسائط.

### ملاحظات إضافية
- يُفضل استخدام `addEventListener` بدلاً من `addListener`، حيث أن `addListener` قد تكون غير مدعومة في بعض المتصفحات الحديثة.

## ملخص جملة واحدة
MediaQueryListEvent في جافا سكريبت يمكّنك من الاستجابة للتغيرات في استعلامات الوسائط، مما يساعد على بناء واجهات مستخدم متجاوبة.