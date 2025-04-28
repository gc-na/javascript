<!--
Meta Description: # GamepadButton في JavaScript: كل ما تحتاج معرفته ## ملخص تُستخدم خاصية GamepadButton في JavaScript لتحديد حالة الأزرار على أجهزة التحكم الخاصة بالألع...
Meta Keywords: التحكم, gamepad, gamepadbutton, على, حالة
-->

# GamepadButton في JavaScript: كل ما تحتاج معرفته

## ملخص
تُستخدم خاصية GamepadButton في JavaScript لتحديد حالة الأزرار على أجهزة التحكم الخاصة بالألعاب (Gamepads) وتوفير واجهة برمجية للتفاعل معها.

## الوثائق
تُعتبر GamepadButton جزءًا من واجهة Gamepad API، والتي تتيح للمطورين القدرة على قراءة البيانات من أجهزة التحكم المختلفة. يمثل كل زر في جهاز التحكم كائن GamepadButton، والذي يحتوي على معلومات حول حالة الزر، مثل ما إذا كان الزر مضغوطًا أم لا.

### الخصائص الأساسية
- **pressed**: خاصية Boolean تُشير إلى ما إذا كان الزر مضغوطًا حاليًا.
- **value**: قيمة عددية تمثل مدى ضغط الزر (من 0 إلى 1)، حيث يُعبر 0 عن عدم الضغط و1 عن الضغط الكامل.

### الاستخدام
لتتمكن من استخدام GamepadButton، يجب أولاً التأكد من أن المتصفح يدعم Gamepad API. يمكن الوصول إلى حالة الأزرار عبر كائن `navigator.getGamepads()` والذي يعود بمصفوفة من كائنات Gamepad.

### شيفرة الاستخدام
```javascript
window.addEventListener("gamepadconnected", function(event) {
    const gamepad = event.gamepad;
    console.log("جهاز التحكم متصل: " + gamepad.id);
});

function checkGamepad() {
    const gamepads = navigator.getGamepads();
    if (gamepads[0]) {
        const button = gamepads[0].buttons[0]; // زر الأول في جهاز التحكم
        console.log("زر مضغوط: " + button.pressed);
        console.log("قيمة الزر: " + button.value);
    }
    requestAnimationFrame(checkGamepad);
}

checkGamepad();
```

## الشرح
### العوائق الشائعة
- **عدم وجود الدعم**: تأكد من استخدام متصفح يدعم Gamepad API. يمكن لبعض المتصفحات أن لا تدعمه بشكل كامل.
- **توقيت الفحص**: يجب استخدام `requestAnimationFrame` لضمان فحص حالة الأزرار بشكل مستمر دون التأثير على أداء اللعبة.

### ملاحظات إضافية
- يمكن أن تحتوي أجهزة التحكم على عدد متنوع من الأزرار، لذا من المهم التحقق من عدد الأزرار المتاحة على الجهاز.
- يمكن للأزرار أن تكون ذات قيم متغيرة، لذا يجب التعامل مع قيمها بحذر.

## ملخص في جملة واحدة
GamepadButton في JavaScript يوفر واجهة برمجية لقراءة حالة أزرار أجهزة التحكم الخاصة بالألعاب، مما يسهل تفاعل المطورين مع الألعاب.