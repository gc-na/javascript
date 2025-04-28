<!--
Meta Description: # XRInputSourceArray في JavaScript: دليلك الشامل ## ملخص XRInputSourceArray هو كائن في واجهة برمجة التطبيقات للواقع الافتراضي والواقع المعزز (WebXR) ف...
Meta Keywords: xrinputsourcearray, الإدخال, javascript, مجموعة, session
-->

# XRInputSourceArray في JavaScript: دليلك الشامل

## ملخص
XRInputSourceArray هو كائن في واجهة برمجة التطبيقات للواقع الافتراضي والواقع المعزز (WebXR) في JavaScript. يُستخدم هذا الكائن لتمثيل مجموعة من مصادر الإدخال مثل أجهزة التحكم أو الأجهزة المتصلة الأخرى التي تتيح التفاعل مع تجارب الواقع الافتراضي والواقع المعزز.

## الوثائق
### الغرض
تم تصميم XRInputSourceArray لتسهيل الوصول إلى مجموعة من المصادر التي يمكن استخدامها في تجارب الواقع الافتراضي والواقع المعزز. يوفر هذا الكائن واجهة موحدة للتفاعل مع الأجهزة المختلفة مثل وحدات التحكم اليدوية ونقاط الإدخال.

### الاستخدام
يمكن استخدام XRInputSourceArray لاسترجاع وتحليل المعلومات المتعلقة بمصادر الإدخال النشطة المتاحة. يتم الوصول إليه عادةً من خلال كائن XRSession، مما يسمح للمطورين بإنشاء تفاعلات أكثر غنى وواقعية في تطبيقاتهم.

### التفاصيل
- **الخصائص**: XRInputSourceArray يتضمن مجموعة من الخصائص التي تتيح لك معرفة نوع مصدر الإدخال، حالته، وما إذا كان متصلاً.
- **الطرق**: يحتوي الكائن على طرق تساعد في إدارة تفاعلات المستخدم مع المصادر المختلفة.
- **التوافق**: يتوافق XRInputSourceArray مع جميع المتصفحات التي تدعم واجهة WebXR.

## الأمثلة
### مثال 1: استرجاع مصادر الإدخال
```javascript
navigator.xr.requestSession('immersive-vr').then((session) => {
    session.addEventListener('selectstart', (event) => {
        const inputSources = session.inputSources;
        inputSources.forEach((inputSource) => {
            console.log('Input Source: ', inputSource);
        });
    });
});
```

### مثال 2: التحقق من نوع الإدخال
```javascript
navigator.xr.requestSession('immersive-vr').then((session) => {
    session.addEventListener('inputsourceadded', (event) => {
        const inputSource = event.inputSource;
        if (inputSource.handedness === 'right') {
            console.log('Right hand controller added');
        }
    });
});
```

## الشرح
### الأخطاء الشائعة
1. **عدم التحقق من التوافر**: يجب التأكد من أن المتصفح يدعم WebXR قبل محاولة استخدام XRInputSourceArray.
2. **التعامل مع مصادر الإدخال غير المتصلة**: يجب أن تكون مستعدًا لفحص حالة كل مصدر إدخال، فقد يكون بعضها غير متصل في أي وقت.

### ملاحظات إضافية
- يمكن أن تتغير تفاصيل XRInputSourceArray بناءً على تحديثات واجهة WebXR، لذا يُنصح بمراجعة الوثائق الرسمية بانتظام.
- تأكد من اختبار تطبيقاتك على مجموعة متنوعة من الأجهزة لضمان تجربة مستخدم سلسة.

## ملخص جملة واحدة
XRInputSourceArray هو كائن في JavaScript يتيح الوصول إلى مجموعة من مصادر الإدخال المستخدمة في تجارب الواقع الافتراضي والواقع المعزز.