<!--
Meta Description: # XRInputSource في JavaScript: دليل شامل لفهم واستخدام واجهة الإدخال في الواقع المعزز ## ملخص XRInputSource هو واجهة برمجة تطبيقات (API) في JavaScript...
Meta Keywords: واجهة, xrinputsource, الإدخال, javascript, تطبيقات
-->

# XRInputSource في JavaScript: دليل شامل لفهم واستخدام واجهة الإدخال في الواقع المعزز

## ملخص
XRInputSource هو واجهة برمجة تطبيقات (API) في JavaScript تُستخدم للتعامل مع مصادر الإدخال في تطبيقات الواقع المعزز (AR) والواقع الافتراضي (VR). تسمح هذه الواجهة للمطورين بالتفاعل مع الأجهزة مثل وحدات التحكم وأجهزة الاستشعار في بيئات الواقع المعزز.

## الوثائق
### الغرض
تُستخدم واجهة XRInputSource لتمثيل الأجهزة المدخلة التي يمكن أن تتفاعل مع تطبيقات XR. تشمل هذه الأجهزة عادةً وحدات التحكم (controllers)، أجهزة استشعار الحركة، وأي جهاز آخر يمكنه إرسال بيانات الإدخال إلى تطبيق XR.

### الاستخدام
يتم الوصول إلى XRInputSource من خلال واجهة XRSession، حيث يتم إنشاء جلسة XR باستخدام XRWebGLLayer أو XRViewport. يُمكنك استرداد قائمة مصادر الإدخال النشطة من خلال استخدام دالة `getInputSources()`.

### التفاصيل
- **الخصائص**:
  - `handedness`: تحدد ما إذا كانت اليد اليمنى أو اليسرى.
  - `profiles`: قائمة البروفيلات التي تشير إلى نوع الجهاز.
  - `gamepad`: تمثل واجهة Gamepad للمدخلات من جهاز التحكم.
  - `targetRaySpace`: تمثل الفضاء الذي يتم فيه توجيه الشعاع الخاص بالجهاز.

- **الطرق**:
  - `getTargetRaySpace()`: تُستخدم لاسترجاع الفضاء الذي يشير إليه الشعاع.

## أمثلة
### مثال 1: استرداد مصادر الإدخال
```javascript
navigator.xr.requestSession('immersive-vr').then(session => {
    session.addEventListener('selectstart', event => {
        const inputSources = session.getInputSources();
        inputSources.forEach(inputSource => {
            console.log(inputSource.handedness);
        });
    });
});
```

### مثال 2: استخدام جهاز التحكم
```javascript
navigator.xr.requestSession('immersive-vr').then(session => {
    session.addEventListener('inputsourceschange', event => {
        event.added.forEach(inputSource => {
            if (inputSource.gamepad) {
                console.log("Gamepad connected: ", inputSource.gamepad);
            }
        });
    });
});
```

## الشرح
### الأخطاء الشائعة
- **عدم التحقق من توفر XR**: قبل استدعاء أي دالة مرتبطة بالـ XR، تأكد من أن المتصفح يدعم واجهة XR.
- **عدم وجود مصادر إدخال**: عند عدم وجود أجهزة مدخلة متصلة، قد تبدو النتائج فارغة، لذا يجب التعامل مع هذه الحالة بشكل مناسب.

### ملاحظات إضافية
- تأكد من أنك قمت بتفعيل إعدادات XR في المتصفح.
- تحقق من الوثائق الخاصة بكل جهاز للتحقق من توافقه مع XRInputSource.

## ملخص بجملة واحدة
XRInputSource في JavaScript هي واجهة برمجة تطبيقات تتيح للمطورين التفاعل مع مصادر الإدخال في تطبيقات الواقع المعزز والواقع الافتراضي.