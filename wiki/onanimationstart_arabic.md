<!--
Meta Description: # onanimationstart في JavaScript: كيفية التعامل مع بداية الرسوم المتحركة ## ملخص `onanimationstart` هو حدث في JavaScript يُستخدم للإشارة إلى بدء الرسو...
Meta Keywords: المتحركة, الرسوم, onanimationstart, style, javascript
-->

# onanimationstart في JavaScript: كيفية التعامل مع بداية الرسوم المتحركة

## ملخص
`onanimationstart` هو حدث في JavaScript يُستخدم للإشارة إلى بدء الرسوم المتحركة المحددة بواسطة CSS. يسمح للمطورين بتنفيذ تعليمات برمجية معينة عندما تبدأ الرسوم المتحركة، مما يُعزز من تفاعل المستخدم وتجربة الموقع.

## الوثائق
### الغرض
يُستخدم `onanimationstart` لمراقبة بداية الرسوم المتحركة في عناصر HTML. يعتبر جزءًا من واجهة برمجة التطبيقات الخاصة بالرسوم المتحركة في CSS، حيث يمكن استخدامه مع خصائص الرسوم المتحركة مثل `@keyframes`.

### الاستخدام
تتم إضافة حدث `onanimationstart` كخاصية على كائن العنصر. يمكن استخدامه مع أي عنصر HTML يحتوي على رسوم متحركة.

#### الصيغة الأساسية:
```javascript
element.onanimationstart = function(event) {
    // التعليمات البرمجية التي سيتم تنفيذها عند بدء الرسوم المتحركة
};
```

### التفاصيل
- **الحدث**: يتم إطلاقه عندما تبدأ الرسوم المتحركة.
- **الخصائص**: يحتوي الكائن الخاص بالحدث (`event`) على معلومات إضافية مثل اسم الرسوم المتحركة، العنصر المستهدف، والوقت الذي بدأت فيه الرسوم المتحركة.
- **التوافق**: مدعوم في معظم المتصفحات الحديثة، ولكن يُفضل التحقق من التوافق مع المتصفحات القديمة.

## الأمثلة
### مثال 1: استخدام `onanimationstart`
```html
<div id="animatedBox" style="width: 100px; height: 100px; background-color: red; animation: example 5s;">
</div>

<script>
    document.getElementById('animatedBox').onanimationstart = function(event) {
        console.log('الرسوم المتحركة بدأت: ' + event.animationName);
    };
</script>

<style>
@keyframes example {
    from { background-color: red; }
    to { background-color: yellow; }
}
</style>
```

### مثال 2: تغيير النص عند بدء الرسوم المتحركة
```html
<div id="text" style="animation: fadeIn 3s;">
    نص الرسوم المتحركة
</div>

<script>
    document.getElementById('text').onanimationstart = function() {
        this.innerText = 'الرسوم المتحركة بدأت!';
    };
</script>

<style>
@keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
}
</style>
```

## الشرح
### العثرات الشائعة
- **عدم دعم المتصفح**: تحقق من توافق المستعرضات، خاصة إذا كنت تستهدف متصفحات قديمة.
- **التحقق من وجود الرسوم المتحركة**: تأكد من أن العنصر لديه رسوم متحركة فعّالة أثناء استخدام `onanimationstart`.
- **تداخل الأحداث**: إذا كانت هناك رسوم متحركة متعددة، تأكد من معالجة كل حدث بشكل منفصل لتجنب التصادمات في التنفيذ.

## ملخص جملة واحدة
`onanimationstart` هو حدث في JavaScript يُستخدم لمراقبة بداية الرسوم المتحركة، مما يسمح بتنفيذ تعليمات برمجية عند بدء الرسوم المتحركة.