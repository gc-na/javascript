<!--
Meta Description: # onwebkitanimationiteration: فهم الحدث في JavaScript ## الملخص يُعتبر حدث `onwebkitanimationiteration` واحدًا من الأحداث المهمة في JavaScript، حيث يُ...
Meta Keywords: onwebkitanimationiteration, الرسوم, المتحركة, animateddiv, style
-->

# onwebkitanimationiteration: فهم الحدث في JavaScript

## الملخص
يُعتبر حدث `onwebkitanimationiteration` واحدًا من الأحداث المهمة في JavaScript، حيث يُستخدم لتحديد الإجراءات التي يجب اتخاذها عند تكرار الرسوم المتحركة (Animation) في متصفح ويب يعتمد على محرك WebKit.

## الوثائق
### الغرض
يتم استخدام `onwebkitanimationiteration` للتعامل مع تكرار الرسوم المتحركة في عناصر HTML. يقوم هذا الحدث بإشعار المطورين عند انتهاء دورة الرسوم المتحركة، مما يتيح لهم تنفيذ تعليمات برمجية معينة مثل تعديل الأنماط أو تنفيذ وظائف إضافية.

### الاستخدام
يمكن ربط حدث `onwebkitanimationiteration` بعنصر HTML باستخدام جافا سكريبت. يتم تعيينه كخاصية على العنصر المستهدف، ويمكن استخدامه مع أي نوع من الرسوم المتحركة التي تم إنشاؤها باستخدام CSS.

### التفاصيل
- **النوع**: حدث (Event)
- **المدخلات**: لا تتطلب أي مدخلات.
- **الإخراج**: يتم تشغيل دالة رد الفعل (callback function) عند تكرار الرسوم المتحركة.

## الأمثلة

### مثال 1: استخدام `onwebkitanimationiteration` مع عنصر HTML

```html
<div id="animatedDiv" style="width:100px; height:100px; background:blue; animation: myAnimation 2s infinite;"></div>

<script>
    const animatedDiv = document.getElementById('animatedDiv');

    animatedDiv.onwebkitanimationiteration = function() {
        console.log('تم تكرار الرسوم المتحركة!');
    };
</script>

<style>
@keyframes myAnimation {
    0% { transform: translateX(0); }
    100% { transform: translateX(100px); }
}
</style>
```

### مثال 2: تغيير الأنماط عند التكرار

```html
<div id="animatedDiv" style="width:100px; height:100px; background:blue; animation: myAnimation 2s infinite;"></div>

<script>
    const animatedDiv = document.getElementById('animatedDiv');

    animatedDiv.onwebkitanimationiteration = function() {
        this.style.background = this.style.background === 'blue' ? 'red' : 'blue';
    };
</script>

<style>
@keyframes myAnimation {
    0% { transform: translateY(0); }
    100% { transform: translateY(100px); }
}
</style>
```

## الشرح
### الأخطاء الشائعة
- **عدم دعم المتصفح**: قد لا يدعم بعض المتصفحات القديمة حدث `onwebkitanimationiteration`. تأكد من اختبار الكود على متصفحات مختلفة.
- **عدم استخدام CSS بشكل صحيح**: تأكد من أن الرسوم المتحركة قد تم تعريفها بشكل صحيح في CSS، وإلا فلن يتم تشغيل الحدث.

### ملاحظات إضافية
- يُفضل استخدام `animationiteration` كبديل عام، حيث أنه مدعوم على نطاق واسع عبر المتصفحات، بينما `onwebkitanimationiteration` هو خاص بـ WebKit.

## ملخص في جملة واحدة
يتيح حدث `onwebkitanimationiteration` للمطورين تنفيذ إجراءات محددة عند تكرار الرسوم المتحركة في متصفحات تعتمد على WebKit.