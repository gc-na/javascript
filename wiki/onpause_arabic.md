<!--
Meta Description: # onpause في JavaScript: فهم واستخدام خاصية الأحداث في البرمجة ## ملخص خاصية `onpause` في JavaScript تُستخدم للكشف عن توقف الوسائط المتعددة، مثل الفيد...
Meta Keywords: onpause, video, audio, الوسائط, script
-->

# onpause في JavaScript: فهم واستخدام خاصية الأحداث في البرمجة

## ملخص
خاصية `onpause` في JavaScript تُستخدم للكشف عن توقف الوسائط المتعددة، مثل الفيديو أو الصوت، أثناء تشغيلها. يتم تفعيل هذه الخاصية عندما يتم إيقاف تشغيل الوسائط، مما يسمح للمطورين بتنفيذ إجراءات معينة عندما يحدث هذا.

## الوثائق
### الغرض
`onpause` هو حدث مخصص يتم استخدامه مع عناصر الوسائط المتعددة في HTML5، مثل `<video>` و`<audio>`. يتيح هذا الحدث للمطورين التعرف على متى تم إيقاف الوسائط عن التشغيل.

### الاستخدام
يمكن استخدام `onpause` بطريقة سهلة من خلال تعيين دالة للحدث عند عنصر الوسائط. عند وقوع الحدث، ستقوم هذه الدالة بتنفيذ التعليمات البرمجية المحددة.

### التفاصيل
- **النوع**: حدث.
- **الأحداث المرتبطة**: `play`, `pause`, `ended`.
- **المدخلات**: لا توجد مدخلات محددة.
  
### كيفية تعيين `onpause`
يمكن تعيين `onpause` باستخدام خاصية JavaScript أو من خلال HTML:
```html
<video id="myVideo" src="video.mp4" controls></video>
<script>
  const videoElement = document.getElementById('myVideo');
  videoElement.onpause = function() {
    console.log('تم إيقاف الفيديو.');
  };
</script>
```

## أمثلة
### مثال 1: استخدام `onpause` مع عنصر فيديو
```html
<video id="myVideo" width="320" height="240" controls>
  <source src="movie.mp4" type="video/mp4">
  متصفحك لا يدعم الفيديو.
</video>
<script>
  const video = document.getElementById('myVideo');
  video.onpause = function() {
    alert('الفيديو قد تم إيقافه.');
  };
</script>
```

### مثال 2: استخدام `onpause` مع عنصر صوت
```html
<audio id="myAudio" controls>
  <source src="audio.mp3" type="audio/mp3">
  متصفحك لا يدعم الصوت.
</audio>
<script>
  const audio = document.getElementById('myAudio');
  audio.onpause = function() {
    console.log('تم إيقاف الصوت.');
  };
</script>
```

## الشرح
### المشاكل الشائعة
- **عدم التفعيل في جميع المتصفحات**: تأكد من اختبار الحدث في المتصفحات المختلفة لضمان التوافق.
- **أداء الحدث**: إذا كانت الدالة المعينة لـ `onpause` تتضمن عمليات كثيفة، قد تؤثر على أداء التطبيق.

### ملاحظات إضافية
- من الجيد استخدام `onpause` بالتزامن مع أحداث أخرى مثل `onplay` أو `onended` للحصول على تجربة مستخدم أفضل.
- تأكد من أن العنصر قد تم تحميله بالكامل قبل تعيين `onpause`.

## ملخص بعبارة واحدة
`onpause` هو حدث في JavaScript يُستخدم للكشف عن توقف تشغيل الوسائط المتعددة، مما يتيح تنفيذ إجراءات محددة عند حدوث ذلك.