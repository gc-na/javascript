<!--
Meta Description: # حدث onpointercancel في JavaScript: كل ما تحتاج معرفته ## ملخص يعد حدث `onpointercancel` من الأحداث الهامة في JavaScript، حيث يُستخدم للتعامل مع إلغا...
Meta Keywords: onpointercancel, box, event, حدث, إلغاء
-->

# حدث onpointercancel في JavaScript: كل ما تحتاج معرفته

## ملخص
يعد حدث `onpointercancel` من الأحداث الهامة في JavaScript، حيث يُستخدم للتعامل مع إلغاء مؤشرات اللمس أو المؤشرات الأخرى. يُعتبر هذا الحدث جزءًا من واجهة برمجة التطبيقات (API) الخاصة بالمؤشرات، ويساعد المطورين في تحسين تجربة المستخدم في تطبيقاتهم.

## التوثيق
### الغرض
يهدف حدث `onpointercancel` إلى إعلام المطورين بأنه قد تم إلغاء عملية التفاعل مع عنصر ما، سواء كان لمسة أو مؤشرًا أو حتى استخدام القلم. يُستخدم هذا الحدث بشكل شائع في تطبيقات الويب التفاعلية التي تعتمد على اللمس أو الإدخال المباشر.

### الاستخدام
يمكن استخدام `onpointercancel` عبر إضافة مستمع (event listener) للحدث إلى عنصر DOM معين. عندما يتم إلغاء المؤشر، يتم استدعاء الدالة المعينة لهذا الحدث.

#### التركيب
```javascript
element.onpointercancel = function(event) {
    // معالجة حدث إلغاء المؤشر
};
```

### تفاصيل
- **الخاصية**: `pointercancel`
- **القيمة**: لا تُعيد قيمة، بل تُنفذ دالة عند حدوث الحدث.
- **المدخلات**: يقوم الحدث بتمرير كائن `PointerEvent` الذي يحتوي على معلومات حول المؤشر الذي تم إلغاؤه.

## أمثلة
### مثال أساسي
```javascript
const box = document.getElementById('box');

box.onpointercancel = function(event) {
    console.log('تم إلغاء المؤشر: ', event.pointerId);
};

box.addEventListener('pointerdown', function(event) {
    console.log('تم الضغط على المؤشر: ', event.pointerId);
});
```

### مثال مع CSS
```html
<div id="box" style="width: 200px; height: 200px; background-color: lightblue;"></div>
<script>
    const box = document.getElementById('box');

    box.onpointercancel = function(event) {
        box.style.backgroundColor = 'red';
        console.log('تم إلغاء المؤشر: ', event.pointerId);
    };
</script>
```

## الشرح
### الأخطاء الشائعة
- **عدم استخدام `pointerdown`**: يجب أن يكون هناك حدث `pointerdown` قبل `pointercancel` ليكون ذو معنى.
- **عدم التحقق من `pointerId`**: ينبغي على المطورين التحقق من `pointerId` لمعرفة أي مؤشر قد تم إلغاؤه، خاصة عند التعامل مع أكثر من مؤشر في نفس الوقت.
- **التوافق مع المتصفحات**: يجب مراعاة أن دعم حدث `onpointercancel` قد يختلف بين المتصفحات، لذا من المهم اختبار التطبيق على عدة بيئات.

## ملخص جملة واحدة
حدث `onpointercancel` في JavaScript يُستخدم لإدارة إلغاء المؤشرات، مما يحسن من تفاعل المستخدمين مع التطبيقات.