<!--
Meta Description: # واجهة التحكم (Gamepad) في JavaScript ## ملخص تتيح واجهة التحكم (Gamepad API) في JavaScript إمكانية التفاعل مع أجهزة التحكم في الألعاب، مما يسهل تطوي...
Meta Keywords: gamepad, التحكم, واجهة, gamepads, javascript
-->

# واجهة التحكم (Gamepad) في JavaScript

## ملخص
تتيح واجهة التحكم (Gamepad API) في JavaScript إمكانية التفاعل مع أجهزة التحكم في الألعاب، مما يسهل تطوير ألعاب ويب تفاعلية باستخدام متصفحات الويب الحديثة.

## الوثائق
### الغرض
تمكن واجهة التحكم المطورين من الوصول إلى أجهزة التحكم بالألعاب المتصلة بالجهاز، مما يتيح لهم قراءة حالة الأزرار والمحاور، وبالتالي تحسين تجربة اللعب.

### الاستخدام
تعمل واجهة Gamepad API على توفير معلومات حول الأجهزة المتصلة، ويمكن استخدامها في مجموعة متنوعة من التطبيقات، بما في ذلك ألعاب الفيديو على الويب. يتم استدعاء البيانات باستخدام دالة `navigator.getGamepads()`.

### التفاصيل
1. **التوافق**: تدعم معظم المتصفحات الحديثة واجهة Gamepad API، بما في ذلك Chrome وFirefox وEdge.
2. **الأجهزة المدعومة**: يمكن استخدام واجهة Gamepad API مع مجموعة متنوعة من أجهزة التحكم، بما في ذلك وحدات التحكم التقليدية وأجهزة التحكم المتقدمة.
3. **التحقق من الأجهزة**: يجب التحقق من توفر الأجهزة المتصلة باستخدام `navigator.getGamepads()`.

## أمثلة
### مثال بسيط
```javascript
window.addEventListener("gamepadconnected", function(event) {
    console.log("Gamepad connected at index " + event.gamepad.index + ": " + event.gamepad.id);
});

function updateGamepadStatus() {
    const gamepads = navigator.getGamepads();
    if (gamepads) {
        for (let gamepad of gamepads) {
            if (gamepad) {
                console.log("Buttons: ", gamepad.buttons);
                console.log("Axes: ", gamepad.axes);
            }
        }
    }
    requestAnimationFrame(updateGamepadStatus);
}

updateGamepadStatus();
```

### مثال متقدم
```javascript
function handleGamepadInput() {
    const gamepads = navigator.getGamepads();
    if (gamepads) {
        const gp = gamepads[0]; // استخدام أول جهاز تحكم متصل
        if (gp) {
            // التعامل مع الأزرار
            if (gp.buttons[0].pressed) {
                console.log("زر A مضغوط");
            }
            // التعامل مع المحاور
            const xAxis = gp.axes[0];
            const yAxis = gp.axes[1];
            console.log(`المحور X: ${xAxis}, المحور Y: ${yAxis}`);
        }
    }
    requestAnimationFrame(handleGamepadInput);
}

handleGamepadInput();
```

## الشرح
### الأخطاء الشائعة
- **عدم التعرف على الجهاز**: تأكد من أن الجهاز متصل بشكل صحيح وأن المتصفح يدعمه.
- **تأخير في القراءة**: استخدم `requestAnimationFrame` لتحديث حالة التحكم بشكل دوري ولتجنب أي تأخير في استجابة اللعبة.
- **الأزرار غير المستجيبة**: تأكد من استخدام الفهارس الصحيحة لأزرار جهاز التحكم، حيث قد يختلف الترتيب حسب نوع الجهاز.

## ملخص جملة واحدة
تتيح واجهة Gamepad API في JavaScript للمطورين التفاعل مع أجهزة التحكم في الألعاب، مما يسهل تطوير ألعاب ويب تفاعلية.