<!--
Meta Description: # حدث "ondurationchange" في JavaScript: دليل شامل ## ملخص يُعتبر حدث "ondurationchange" في JavaScript أحد الأحداث المهمة المستخدمة في التحكم في عناصر ...
Meta Keywords: ondurationchange, مدة, الحدث, الوسائط, الفيديو
-->

# حدث "ondurationchange" في JavaScript: دليل شامل

## ملخص
يُعتبر حدث "ondurationchange" في JavaScript أحد الأحداث المهمة المستخدمة في التحكم في عناصر الوسائط المتعددة، حيث يُستخدم لمراقبة التغييرات في مدة الميديا مثل الفيديو أو الصوت.

## الوثائق
### الغرض
يستخدم حدث "ondurationchange" للكشف عن التغييرات في مدة عنصر الوسائط. يحدث هذا الحدث عندما تتغير مدة الوسائط، على سبيل المثال، عند تحميل فيديو أو عند تغيير مصدره.

### الاستخدام
يمكن استخدام "ondurationchange" مع عناصر HTML5 مثل `<video>` و`<audio>`. يتم تعيين معالج الحدث للتفاعل مع تغييرات المدة.

#### كيفية الاستخدام:
```javascript
const videoElement = document.getElementById('myVideo');

videoElement.ondurationchange = function() {
    console.log('مدة الفيديو قد تغيرت إلى: ' + videoElement.duration + ' ثواني');
};
```

### التفاصيل
- **نوع العنصر**: يمكن استخدام "ondurationchange" مع عناصر `<audio>` و`<video>`.
- **الحدث**: يتم استدعاء المعالج عندما تتغير مدة العنصر، وهو مفيد بشكل خاص عند تحميل وسائط جديدة.
- **الدعم**: مدعوم في معظم المتصفحات الحديثة.

## الأمثلة
### مثال 1: استخدام "ondurationchange" مع عنصر فيديو
```html
<video id="myVideo" controls>
    <source src="movie.mp4" type="video/mp4">
    متصفحك لا يدعم الفيديو.
</video>

<script>
    const videoElement = document.getElementById('myVideo');

    videoElement.ondurationchange = function() {
        alert('مدة الفيديو هي: ' + videoElement.duration + ' ثواني');
    };
</script>
```

### مثال 2: استخدام "ondurationchange" مع عنصر صوت
```html
<audio id="myAudio" controls>
    <source src="audio.mp3" type="audio/mpeg">
    متصفحك لا يدعم الصوت.
</audio>

<script>
    const audioElement = document.getElementById('myAudio');

    audioElement.ondurationchange = function() {
        console.log('مدة الصوت هي: ' + audioElement.duration + ' ثواني');
    };
</script>
```

## الشرح
### الأخطاء الشائعة
- **عدم التحقق من الدعم**: قد يحدث أن بعض المتصفحات القديمة لا تدعم هذا الحدث.
- **إعداد المعالج قبل تحميل الميديا**: يجب التأكد من تعيين معالج الحدث قبل تحميل المصدر لضمان استدعاء الحدث بشكل صحيح.
- **عدم تحديث المدة**: في بعض الحالات، قد لا يتم تحديث المدة على الفور عند تغيير المصدر، لذا يُنصح بإعادة التحقق من المدة بعد فترة قصيرة.

### ملاحظات إضافية
- يمكن استخدام هذا الحدث في التطبيقات التفاعلية التي تتطلب تفاعل المستخدم مع الوسائط، مثل مشغلات الفيديو المخصصة.
- يعتبر "ondurationchange" مفيدًا أيضًا في تحسين تجربة المستخدم من خلال توفير معلومات فورية حول محتوى الوسائط.

## ملخص من جملة واحدة
يعتبر حدث "ondurationchange" في JavaScript أداة رئيسية لمراقبة التغييرات في مدة عناصر الوسائط مثل الفيديو والصوت.