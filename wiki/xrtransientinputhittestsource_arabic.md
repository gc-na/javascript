<!--
Meta Description: # XRTransientInputHitTestSource في JavaScript: كل ما تحتاج لمعرفته ## الملخص XRTransientInputHitTestSource هي واجهة برمجية في JavaScript تستخدم لتقديم...
Meta Keywords: اللمس, اختبار, xrsession, xrtransientinputhittestsource, javascript
-->

# XRTransientInputHitTestSource في JavaScript: كل ما تحتاج لمعرفته

## الملخص
XRTransientInputHitTestSource هي واجهة برمجية في JavaScript تستخدم لتقديم نتائج اختبار اللمس للمدخلات العابرة في تجارب الواقع المعزز والافتراضي. تم تصميمها لتسهيل التعامل مع المدخلات في بيئات XR.

## الوثائق
### الغرض
تُستخدم XRTransientInputHitTestSource لتوفير معلومات حول النقاط التي يتم اختبارها عند استخدام مدخلات مثل اللمس أو الإيماءات في تطبيقات الواقع المعزز أو الافتراضي. يُعتبر هذا الأمر مهمًا لإنشاء تجارب تفاعلية غامرة.

### الاستخدام
لإنشاء XRTransientInputHitTestSource، يجب أن يكون لديك XRSession نشطة. يتم استخدام الطريقة `requestHitTestSource` على XRSession للحصول على مصدر اختبار اللمس. 

#### التركيب
```javascript
const hitTestSource = await xrSession.requestHitTestSource({
  space: xrSpace,
  offsetRay: xrRay
});
```

### التفاصيل
- **المساحة (space)**: يمثل الفضاء الذي يتم فيه اختبار اللمس.
- **إزاحة الشعاع (offsetRay)**: يمثل الشعاع المستخدم لتحديد نقطة اختبار اللمس.

## الأمثلة
### مثال أساسي
```javascript
// إنشاء جلسة XR
navigator.xr.requestSession('immersive-vr').then((xrSession) => {
  // إعداد الفضاء
  const xrSpace = xrSession.requestReferenceSpace('local');

  // طلب مصدر اختبار اللمس
  xrSession.requestHitTestSource({
    space: xrSpace,
    offsetRay: new XRRay(new XRRigidTransform())
  }).then((hitTestSource) => {
    console.log(hitTestSource);
  });
});
```

## الشرح
- **نقاط يجب الانتباه لها**: تأكد من أن XRSession نشطة قبل محاولة إنشاء مصدر اختبار اللمس.
- **المشكلات الشائعة**: قد تواجه مشاكل في الأداء إذا تم استخدام عدد كبير من مصادر اختبار اللمس في وقت واحد. من الأفضل إدارة مواردك بعناية.
- **ملاحظات إضافية**: هذه الواجهة جزء من مجموعة أكبر من واجهات برمجة التطبيقات XR، لذا يُنصح بالتعرف على كيفية التفاعل مع هذه الواجهات لتحقيق أقصى استفادة من تجارب XR.

## ملخص جملة واحدة
XRTransientInputHitTestSource هي واجهة برمجية في JavaScript تستخدم لاختبار المدخلات العابرة في تجارب الواقع المعزز والافتراضي.