<!--
Meta Description: # onmousewheel في JavaScript: التحكم في أحداث تمرير الماوس ## ملخص onmousewheel هو حدث في JavaScript يُستخدم للكشف عن حركة تمرير الماوس (Scroll) على ا...
Meta Keywords: الماوس, على, onmousewheel, تمرير, event
-->

# onmousewheel في JavaScript: التحكم في أحداث تمرير الماوس

## ملخص
onmousewheel هو حدث في JavaScript يُستخدم للكشف عن حركة تمرير الماوس (Scroll) على العناصر في صفحة الويب. يُستخدم هذا الحدث عادةً لتحسين تجربة المستخدم من خلال استجابة واجهة المستخدم لتفاعلات التمرير.

## الوثائق
### الغرض
يُستخدم حدث onmousewheel لمراقبة حركة تمرير الماوس على صفحة الويب أو على عنصر معين. يتيح للمطورين تنفيذ إجراءات معينة استجابةً لتمرير الماوس، مثل تغيير المحتوى أو تعديل التفاعل مع الصفحة.

### الاستخدام
يمكن استخدام onmousewheel على أي عنصر من عناصر HTML. يتلقى هذا الحدث كائنًا يحتوي على معلومات حول حركة الماوس، بما في ذلك مقدار التمرير.

### التفاصيل
- **الصيغة**: 
```javascript
element.onmousewheel = function(event) {
    // كود الاستجابة للتمرير
};
```
- **المعلمات**: 
  - `event`: كائن الحدث الذي يحتوي على معلومات مثل `deltaY` و `deltaX` اللذان يحددان اتجاه وكمية التمرير.
  
- **الدعم المتصفح**: 
  - متاح في معظم المتصفحات الحديثة، لكن يُفضل استخدام `addEventListener` للحصول على دعم أفضل.

## أمثلة
### مثال 1: حدث تمرير بسيط
```html
<div id="scrollable" style="height: 200px; overflow: auto;">
    <p>محتوى طويل هنا...</p>
</div>

<script>
    document.getElementById("scrollable").onmousewheel = function(event) {
        console.log("تم تمرير الماوس بمقدار: " + event.deltaY);
    };
</script>
```

### مثال 2: استخدام `addEventListener`
```html
<div id="scrollable" style="height: 200px; overflow: auto;">
    <p>محتوى طويل هنا...</p>
</div>

<script>
    document.getElementById("scrollable").addEventListener("mousewheel", function(event) {
        console.log("تم تمرير الماوس بمقدار: " + event.deltaY);
    });
</script>
```

## الشرح
### الأخطاء الشائعة
- **عدم استخدام `preventDefault()`**: إذا كنت ترغب في منع التمرير الافتراضي، يجب عليك استدعاء `event.preventDefault()` داخل وظيفة المعالجة.
- **عدم التعامل مع المتصفحات المختلفة**: بعض المتصفحات قد تستخدم `wheel` بدلاً من `mousewheel`. لذا يُفضل التحقق من الدعم وإضافة معالجات لكل منها.

### ملاحظات إضافية
- يُفضل استخدام `wheel` (الذي يقدم معلومات أفضل عن التمرير) بدلاً من `mousewheel` في التطبيقات الحديثة.
- تأكد من اختبار الحدث عبر مختلف المتصفحات لضمان تجربة مستخدم متسقة.

## ملخص جملة واحدة
onmousewheel هو حدث في JavaScript يُستخدم للتفاعل مع حركة تمرير الماوس، مما يتيح تحسين تجربة المستخدم على صفحات الويب.