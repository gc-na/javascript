<!--
Meta Description: # حدث GamepadEvent في JavaScript: دليل شامل ## ملخص يعد حدث GamepadEvent جزءًا من واجهة برمجة التطبيقات الخاصة بالألعاب في JavaScript، مما يتيح للمطور...
Meta Keywords: التحكم, جهاز, أجهزة, event, gamepadevent
-->

# حدث GamepadEvent في JavaScript: دليل شامل

## ملخص
يعد حدث GamepadEvent جزءًا من واجهة برمجة التطبيقات الخاصة بالألعاب في JavaScript، مما يتيح للمطورين التفاعل مع أجهزة التحكم في الألعاب مثل أجهزة التحكم باليد والأجهزة الأخرى المماثلة.

## الوثائق
### الغرض
تمكن GamepadEvent المطورين من رصد التغييرات في حالة أجهزة التحكم في الألعاب، مثل التوصيل والفصل، مما يسهل تطوير ألعاب وتطبيقات تفاعلية تعتمد على هذه الأجهزة.

### الاستخدام
يتم استخدام GamepadEvent في تطبيقات الويب التي تحتاج إلى دعم أجهزة التحكم في الألعاب. يمكن أن يتضمن ذلك الألعاب عبر الإنترنت، تطبيقات المحاكاة، أو أي مشروع يتطلب مدخلات من أجهزة التحكم.

### التفاصيل
يتم إصدار GamepadEvent عند حدوث تغييرات في حالة جهاز التحكم. تشمل الخصائص المهمة للحدث:
- `gamepad`: الكائن الذي يمثل جهاز التحكم المتصل.
- `type`: نوع الحدث (مثل "connected" أو "disconnected").
- `timestamp`: الوقت الذي حدث فيه الحدث.

يمكن الاستماع إلى هذه الأحداث باستخدام `window.addEventListener` كالتالي:
```javascript
window.addEventListener("gamepadconnected", function(event) {
    console.log("جهاز التحكم متصل", event.gamepad);
});

window.addEventListener("gamepaddisconnected", function(event) {
    console.log("جهاز التحكم مفصول", event.gamepad);
});
```

## الأمثلة
### مثال 1: رصد اتصال جهاز التحكم
```javascript
window.addEventListener("gamepadconnected", function(event) {
    console.log("تم توصيل جهاز التحكم:", event.gamepad.id);
});
```

### مثال 2: رصد فصل جهاز التحكم
```javascript
window.addEventListener("gamepaddisconnected", function(event) {
    console.log("تم فصل جهاز التحكم:", event.gamepad.id);
});
```

## الشرح
### الأخطاء الشائعة
- **عدم دعم المتصفح**: تأكد من أن المتصفح الذي تستخدمه يدعم واجهة Gamepad API.
- **عدم وجود أجهزة تحكم متصلة**: تأكد من توصيل جهاز التحكم بشكل صحيح قبل اختبار الكود.

### ملاحظات إضافية
- يمكن استخدام `navigator.getGamepads()` للحصول على حالة جميع أجهزة التحكم المتصلة.
- تأكد من اختبار الكود في بيئة تدعم الأحداث بشكل كامل، مثل الألعاب عبر الإنترنت أو التطبيقات التفاعلية.

## ملخص من جملة واحدة
حدث GamepadEvent في JavaScript يتيح للمطورين رصد التغييرات في حالة أجهزة التحكم في الألعاب، مما يسهل تطوير تجارب تفاعلية.