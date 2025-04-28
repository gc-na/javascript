<!--
Meta Description: # حدث onpointerleave في JavaScript: كيفية استخدامه وتأثيره ## ملخص حدث `onpointerleave` هو حدث يُستخدم في JavaScript للكشف عن مغادرة المؤشر (مثل الماو...
Meta Keywords: onpointerleave, المؤشر, javascript, عند, مغادرة
-->

# حدث onpointerleave في JavaScript: كيفية استخدامه وتأثيره

## ملخص
حدث `onpointerleave` هو حدث يُستخدم في JavaScript للكشف عن مغادرة المؤشر (مثل الماوس أو القلم) لعناصر معينة في واجهة المستخدم. يُعتبر هذا الحدث جزءًا من واجهة برمجة تطبيقات المؤشرات (Pointer Events API) التي تهدف إلى تبسيط التعامل مع المدخلات المتعددة.

## الوثائق
### الغرض
يستخدم حدث `onpointerleave` لمراقبة متى يغادر المؤشر منطقة عنصر معين. يمكن أن يكون هذا مفيدًا في تحسين تجربة المستخدم، مثل إخفاء عناصر أو تنفيذ تفاعلات معينة عند مغادرة المؤشر.

### الاستخدام
يمكن استخدام `onpointerleave` مباشرة على العناصر في HTML أو من خلال JavaScript. عند استخدامه في JavaScript، يتم تعيينه كدالة رد نداء (callback function) يتم استدعاؤها عند وقوع الحدث.

### التركيب
```javascript
element.onpointerleave = function(event) {
    // الكود الذي سيتم تنفيذه عند مغادرة المؤشر
};
```

أو باستخدام `addEventListener`:
```javascript
element.addEventListener('pointerleave', function(event) {
    // الكود الذي سيتم تنفيذه عند مغادرة المؤشر
});
```

## الأمثلة
### مثال بسيط
```html
<div id="myElement" style="width: 200px; height: 200px; background-color: lightblue;">
    مرر الماوس هنا
</div>

<script>
    const myElement = document.getElementById('myElement');

    myElement.onpointerleave = function(event) {
        alert('لقد غادرت المنطقة!');
    };
</script>
```

### استخدام `addEventListener`
```html
<div id="anotherElement" style="width: 200px; height: 200px; background-color: lightgreen;">
    مرر الماوس هنا
</div>

<script>
    const anotherElement = document.getElementById('anotherElement');

    anotherElement.addEventListener('pointerleave', function(event) {
        console.log('المؤشر غادر العنصر!');
    });
</script>
```

## الشرح
### الأخطاء الشائعة
- **عدم استخدام `preventDefault()`:** عند التعامل مع الأحداث، قد تحتاج إلى استخدام `preventDefault()` لمنع السلوك الافتراضي، خاصةً إذا كنت تتعامل مع عناصر تفاعلية مثل الأزرار.
- **الخلط بين الأحداث:** قد يتم الخلط بين `onpointerleave` و`onpointerout`. من المهم فهم أن `onpointerleave` يتم استدعاؤه فقط عندما يغادر المؤشر العنصر نفسه، في حين أن `onpointerout` قد يُستدعى عند مغادرة أي عنصر فرعي.

### ملاحظات إضافية
- يدعم `onpointerleave` جميع المتصفحات الحديثة، ولكنه قد لا يعمل بشكل صحيح في المتصفحات القديمة.
- يُفضل استخدام `addEventListener` لزيادة قابلية القراءة وإمكانية الصيانة للكود.

## ملخص بجملة واحدة
حدث `onpointerleave` في JavaScript يُستخدم لكشف مغادرة المؤشر لعناصر واجهة المستخدم، مما يعزز التفاعل وتحسين تجربة المستخدم.