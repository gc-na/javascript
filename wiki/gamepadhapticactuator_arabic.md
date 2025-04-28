<!--
Meta Description: # GamepadHapticActuator في JavaScript: دليل شامل ## ملخص GamepadHapticActuator هو واجهة برمجية في JavaScript تتيح للمطورين التحكم في أنظمة الاهتزاز لل...
Meta Keywords: gamepad, الاهتزاز, actuator, gamepadhapticactuator, javascript
-->

# GamepadHapticActuator في JavaScript: دليل شامل

## ملخص
GamepadHapticActuator هو واجهة برمجية في JavaScript تتيح للمطورين التحكم في أنظمة الاهتزاز للمتحكمات (gamepads)، مما يعزز تجربة اللعب من خلال توفير ردود فعل لمسية.

## الوثائق
### الغرض
تُستخدم GamepadHapticActuator لتوفير ردود فعل لمسية للمستخدمين أثناء اللعب، مما يخلق تجربة تفاعلية أكثر عمقًا. هذه الواجهة تدعم اهتزازات مختلفة يمكن التحكم بها، مثل الاهتزازات المستمرة أو النبضات ذات القوة المتغيرة.

### الاستخدام
يمكن الوصول إلى GamepadHapticActuator عبر كائن `Gamepad` في واجهة برمجة التطبيقات (API) الخاصة بالمتحكمات. يتطلب ذلك وجود متحكم متصل بالجهاز.

### التفاصيل
- **الخصائص**:
  - `pulse()`: وظيفة لبدء الاهتزاز بقوة معينة ومدة محددة.
  - `strongValue`: قيمة الاهتزاز القوي (من 0 إلى 1).
  - `weakValue`: قيمة الاهتزاز الضعيف (من 0 إلى 1).

### كيفية الاستخدام
للتمكن من استخدام GamepadHapticActuator، يجب أولاً التأكد من توفر المتحكم وتحميله في متصفح يدعم واجهة برمجة التطبيقات. ثم يمكن استخدام الكود التالي:

```javascript
navigator.getGamepads().forEach((gamepad) => {
    if (gamepad.hapticActuators) {
        const actuator = gamepad.hapticActuators[0];
        actuator.pulse(1, 200); // اهتزاز قوي لمدة 200 مللي ثانية
    }
});
```

## الأمثلة
### مثال 1: بدء الاهتزاز
```javascript
navigator.getGamepads().forEach((gamepad) => {
    if (gamepad.hapticActuators.length > 0) {
        const actuator = gamepad.hapticActuators[0];
        actuator.pulse(0.5, 1000); // اهتزاز متوسط لمدة 1000 مللي ثانية
    }
});
```

### مثال 2: اهتزازات متعددة
```javascript
function startHapticFeedback(gamepad) {
    const actuator = gamepad.hapticActuators[0];
    actuator.pulse(0.8, 500); // اهتزاز قوي لمدة 500 مللي ثانية
    setTimeout(() => {
        actuator.pulse(0.2, 300); // اهتزاز ضعيف لمدة 300 مللي ثانية
    }, 600);
}
```

## الشرح
### الأخطاء الشائعة
- **عدم توفر المتحكم**: تأكد من أن المتحكم متصل بشكل صحيح.
- **عدم دعم المتصفح**: تحقق من دعم المتصفح لواجهة برمجة التطبيقات الخاصة بالمتحكمات.
- **الاستخدام غير الصحيح لوظائف الاهتزاز**: تأكد من تمرير القيم الصحيحة للوظائف مثل `pulse()`.

### ملاحظات إضافية
- يمكن أن تختلف ميزات الاهتزاز من متحكم لآخر، لذا تأكد من اختبار الكود على المتحكمات المختلفة.
- بعض المتصفحات قد تحتاج إلى إذن إضافي لاستخدام ميزات الاهتزاز.

## ملخص
GamepadHapticActuator في JavaScript يتيح التحكم في ردود فعل المتحكمات، مما يعزز من تفاعلية الألعاب من خلال الاهتزازات الدقيقة.