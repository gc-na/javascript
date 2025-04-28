<!--
Meta Description: # XRHand في JavaScript: استكشاف تقنية الواقع الممتد ## ملخص XRHand هو واجهة برمجة تطبيقات (API) متعلقة بالواقع الممتد (XR) في JavaScript، تُستخدم للتف...
Meta Keywords: اليد, xrhand, hand, على, session
-->

# XRHand في JavaScript: استكشاف تقنية الواقع الممتد

## ملخص
XRHand هو واجهة برمجة تطبيقات (API) متعلقة بالواقع الممتد (XR) في JavaScript، تُستخدم للتفاعل مع يد المستخدم في بيئات الواقع الافتراضي والواقع المعزز. يتيح XRHand المطورين إمكانية بناء تجارب غامرة من خلال تتبع حركة اليد.

## الوثائق
### الغرض
تعد XRHand جزءًا من واجهة برمجة تطبيقات WebXR، والتي تهدف إلى جعل تطوير التطبيقات المخصصة للواقع الافتراضي والواقع المعزز أسهل وأكثر سلاسة. توفر XRHand بيانات حول موضع اليد، حركاتها، وحالة أصابعها، مما يمكّن المطورين من إنشاء تجارب تفاعلية.

### الاستخدام
لتفعيل XRHand، يجب على المطورين أولاً التأكد من أن تطبيقهم يدعم WebXR. يجب أن يتم استدعاء XRHand في سياق جلسة WebXR، حيث يمكن الحصول على معلومات اليد عبر `navigator.xr.requestSession()`.

### التفاصيل
- **XRHand**: تمثل يد المستخدم (اليد اليسرى أو اليمنى)، وتتيح الوصول إلى موضع اليد وحالة الأصابع.
- **XRHandJoint**: يمثل كل إصبع أو جزء من اليد، مما يوفر بيانات دقيقة حول حركات اليد.
- **الخصائص**:
  - `position`: موضع اليد في الفضاء ثلاثي الأبعاد.
  - `rotation`: دوران اليد.
  - `joints`: مصفوفة تحتوي على XRHandJoint، تمثل كل جزء من اليد.

## الأمثلة
### مثال بسيط على استخدام XRHand
```javascript
if (navigator.xr) {
    navigator.xr.requestSession('immersive-vr').then(session => {
        session.addEventListener('selectstart', event => {
            const hand = event.target;
            console.log('Hand position:', hand.position);
        });
        session.update = () => {
            // تحديثات الوضعية
        };
    });
}
```

### مثال على تتبع حركة اليد
```javascript
session.requestReferenceSpace('local').then(referenceSpace => {
    session.requestAnimationFrame(function onAnimationFrame(t, frame) {
        const hand = frame.getHand(0); // 0 لليد اليسرى و 1 لليد اليمنى
        if (hand) {
            console.log('Hand position:', hand.position);
            console.log('Hand rotation:', hand.rotation);
        }
        session.requestAnimationFrame(onAnimationFrame);
    });
});
```

## الشرح
### الأخطاء الشائعة
- **عدم دعم المتصفح**: يجب التأكد من أن المتصفح يدعم WebXR. تحقق من التوافق قبل بدء الاستخدام.
- **إغفال التهيئة**: يجب تهيئة الجلسة بشكل صحيح قبل محاولة الوصول إلى بيانات XRHand.
- **الاعتماد على الأحداث**: تأكد من استخدام الأحداث بدلاً من الاستدعاء المباشر للحصول على بيانات اليد لضمان الأداء السلس.

### ملاحظات إضافية
تقدم XRHand إمكانيات واسعة لتطوير تجارب تفاعلية، لكن من المهم مراعاة قيود الأجهزة المختلفة، حيث قد تختلف دقة تتبع اليد من جهاز إلى آخر.

## ملخص بجملة واحدة
XRHand في JavaScript هو واجهة برمجة تطبيقات تتيح تتبع حركة اليد وتحركات الأصابع في بيئات الواقع الممتد، مما يعزز التفاعل في التطبيقات الغامرة.