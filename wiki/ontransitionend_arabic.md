<!--
Meta Description: # حدث ontransitionend في JavaScript: فهم شامل ## ملخص يعد حدث `ontransitionend` من الأحداث الهامة في JavaScript، حيث يُستخدم للكشف عن نهاية الانتقالات...
Meta Keywords: box, event, ontransitionend, الانتقال, button
-->

# حدث ontransitionend في JavaScript: فهم شامل

## ملخص
يعد حدث `ontransitionend` من الأحداث الهامة في JavaScript، حيث يُستخدم للكشف عن نهاية الانتقالات (transitions) في أنماط CSS. يتيح للمطورين تنفيذ وظائف معينة بعد انتهاء تأثيرات الانتقال، مما يعزز تجربة المستخدم.

## الوثائق
### الغرض
يتم استخدام `ontransitionend` لتحديد متى ينتهي تأثير الانتقال المحدد على عنصر ما. هذا الحدث مفيد بشكل خاص عند العمل مع الرسوم المتحركة أو التحولات، حيث يمكن أن تحتاج إلى إجراء معين بعد انتهاء تأثير معين.

### الاستخدام
يتم ربط حدث `ontransitionend` بعنصر HTML معين، ويمكن استخدامه مع أي عنصر يدعم CSS transitions. يمكن تعيين معالج الحدث الخاص به باستخدام JavaScript كالتالي:

```javascript
element.addEventListener('transitionend', function(event) {
    console.log('الانتقال انتهى:', event.propertyName);
});
```

### التفاصيل
- **الخصائص**: يحتوي كائن الحدث `event` على معلومات مهمة، مثل:
  - `propertyName`: اسم خاصية CSS التي انتهى انتقالها.
  - `elapsedTime`: الوقت الذي استغرقه الانتقال.
  - `pseudoElement`: إذا كان الانتقال قد تم على عنصر زائف (مثل `::before` أو `::after`).

## الأمثلة
### مثال 1: استخدام ontransitionend
```html
<div id="box" style="width: 100px; height: 100px; background: red; transition: background 1s;"></div>
<button id="changeColor">غيّر اللون</button>

<script>
    const box = document.getElementById('box');
    const button = document.getElementById('changeColor');

    button.addEventListener('click', () => {
        box.style.background = 'blue';
    });

    box.addEventListener('transitionend', (event) => {
        console.log(`الانتقال انتهى للخاصية: ${event.propertyName}`);
    });
</script>
```

### مثال 2: استخدام ontransitionend مع عدة خصائص
```html
<div id="box" style="width: 100px; height: 100px; background: red; transition: width 1s, height 1s;"></div>
<button id="resize">تغيير الحجم</button>

<script>
    const box = document.getElementById('box');
    const button = document.getElementById('resize');

    button.addEventListener('click', () => {
        box.style.width = '200px';
        box.style.height = '200px';
    });

    box.addEventListener('transitionend', (event) => {
        console.log(`الانتقال انتهى للخاصية: ${event.propertyName}`);
    });
</script>
```

## الشرح
### المزالق الشائعة
- **عدم تطابق الخصائص**: قد يحدث أن يتم استدعاء الحدث `ontransitionend` لأكثر من خاصية في نفس الوقت. تأكد من التحقق من `event.propertyName` لمعرفة أي خاصية انتهت.
- **تأخر في الاستجابة**: في بعض الأحيان، قد لا يتم تسجيل الحدث إذا تم تغيير الأنماط بشكل متكرر جداً. تأكد من إجراء التغييرات بطريقة منظمة.
- **الاعتبار للعنصر الزائف**: إذا كنت تستخدم عناصر زائفة، تأكد من التعامل مع `event.pseudoElement` إذا كان ذلك ضرورياً.

## ملخص من جملة واحدة
يعد حدث `ontransitionend` في JavaScript وسيلة فعالة لرصد نهاية تأثيرات الانتقال في CSS، مما يتيح تنفيذ وظائف معينة بعد انتهاء هذه التأثيرات.