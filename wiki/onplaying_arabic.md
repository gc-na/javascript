<!--
Meta Description: # استخدام onplaying في JavaScript: دليل شامل ## ملخص تُستخدم خاصية `onplaying` في JavaScript لتحديد حدث بدء تشغيل الوسائط مثل الصوت أو الفيديو. يتم تف...
Meta Keywords: video, onplaying, javascript, تشغيل, audio
-->

# استخدام onplaying في JavaScript: دليل شامل

## ملخص
تُستخدم خاصية `onplaying` في JavaScript لتحديد حدث بدء تشغيل الوسائط مثل الصوت أو الفيديو. يتم تفعيل هذا الحدث عندما يبدأ تشغيل الوسائط بعد توقف مؤقت.

## الوثائق
### الغرض
تُعتبر `onplaying` جزءًا من واجهات برمجة التطبيقات الخاصة بالوسائط في JavaScript، وتُستخدم بشكل رئيسي مع عناصر HTML5 مثل `<audio>` و `<video>`. يتيح هذا الحدث للمطورين تنفيذ أكواد معينة عندما يبدأ تشغيل الوسائط، مما يسمح بتعزيز تفاعل المستخدم.

### الاستخدام
يمكن استخدام `onplaying` كخاصية للعنصر الوسيطي، بحيث يتم تعيين دالة تُنفذ عند بدء التشغيل. يمكن تعيينها باستخدام JavaScript أو HTML.

**مثال على تعيينها في HTML:**
```html
<video id="myVideo" onplaying="myFunction()">
  <source src="movie.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>
```

**مثال على تعيينها في JavaScript:**
```javascript
const video = document.getElementById('myVideo');
video.onplaying = function() {
  console.log('The video is now playing!');
};
```

## الأمثلة
### مثال 1: استخدام onplaying مع عنصر فيديو
```html
<video id="myVideo" controls>
  <source src="example.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

<script>
  const video = document.getElementById('myVideo');
  video.onplaying = function() {
    alert('بدأ تشغيل الفيديو!');
  };
</script>
```

### مثال 2: استخدام onplaying مع عنصر صوت
```html
<audio id="myAudio" controls>
  <source src="example.mp3" type="audio/mpeg">
  Your browser does not support the audio tag.
</audio>

<script>
  const audio = document.getElementById('myAudio');
  audio.onplaying = function() {
    console.log('يتم تشغيل الصوت الآن!');
  };
</script>
```

## الشرح
### الأخطاء الشائعة والملاحظات
- **عدم الاستجابة:** قد لا تعمل `onplaying` إذا لم يكن العنصر في حالة تشغيل فعلي. تأكد من أن الوسائط قد بدأت بالفعل.
- **عدم دعم المتصفح:** تأكد من اختبار الكود على متصفحات مختلفة، حيث قد تختلف دعم الأحداث.
- **تعيين الأحداث المتعددة:** إذا قمت بتعيين عدة وظائف لنفس الحدث، فإن الوظيفة الأخيرة هي التي ستعمل. استخدم `addEventListener` إذا كنت بحاجة إلى تعيين وظائف متعددة.

## ملخص
تُستخدم خاصية `onplaying` في JavaScript للكشف عن بدء تشغيل الوسائط، مما يتيح للمطورين تحسين تجربة المستخدم.