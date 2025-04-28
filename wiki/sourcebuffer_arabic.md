<!--
Meta Description: # SourceBuffer في JavaScript: دليل شامل ## ملخص SourceBuffer هو واجهة في JavaScript تُستخدم لإدارة تدفقات البيانات في Web APIs، خاصةً عند التعامل مع و...
Meta Keywords: sourcebuffer, mediasource, البيانات, javascript, const
-->

# SourceBuffer في JavaScript: دليل شامل

## ملخص
SourceBuffer هو واجهة في JavaScript تُستخدم لإدارة تدفقات البيانات في Web APIs، خاصةً عند التعامل مع وسائط متعددة مثل الفيديو والصوت. تُعتبر SourceBuffer جزءاً من واجهة MediaSource التي تسمح بتخصيص التحكم في تحميل البيانات.

## الوثائق
### الغرض
تم تصميم SourceBuffer لتسهيل إضافة بيانات جديدة إلى تدفق الوسائط، مما يسمح بتشغيل المحتوى بشكل متقطع دون الحاجة إلى تحميل الملف بالكامل. هذا يجعلها مثالية لتطبيقات البث المباشر أو التشغيل المتقطع.

### الاستخدام
لإنشاء SourceBuffer، يجب أولاً إنشاء كائن MediaSource، ثم استخدام دالة `addSourceBuffer()` لإضافة SourceBuffer جديد. يمكن التحكم في البيانات المضافة، ومعالجة الأخطاء، وإدارة حالة التشغيل.

### التفاصيل
- **إنشاء MediaSource:**
  ```javascript
  const mediaSource = new MediaSource();
  const sourceBuffer = mediaSource.addSourceBuffer('video/webm; codecs="vp8"');
  ```

- **إضافة بيانات:**
  لتحديث SourceBuffer، يمكنك استخدام دالة `appendBuffer()`:
  ```javascript
  const newData = new Uint8Array([/* بيانات الفيديو */]);
  sourceBuffer.appendBuffer(newData);
  ```

- **إدارة الأخطاء:**
  يجب مراقبة أحداث الأخطاء مثل `error` و `updateend` للتأكد من أن البيانات تتم معالجتها بشكل صحيح.

## أمثلة
### مثال أساسي
```javascript
// إنشاء MediaSource
const mediaSource = new MediaSource();
const videoElement = document.querySelector('video');
videoElement.src = URL.createObjectURL(mediaSource);

// إضافة SourceBuffer
mediaSource.addEventListener('sourceopen', function() {
  const sourceBuffer = mediaSource.addSourceBuffer('video/webm; codecs="vp8"');

  // إضافة بيانات للفيديو
  fetch('video.webm')
    .then(response => response.arrayBuffer())
    .then(data => {
      sourceBuffer.appendBuffer(data);
    });
});
```

### مثال مع معالجة الأخطاء
```javascript
sourceBuffer.addEventListener('error', function(e) {
  console.error('حدث خطأ:', e);
});

// تحديث البيانات
sourceBuffer.addEventListener('updateend', function() {
  console.log('تم تحديث SourceBuffer بنجاح');
});
```

## الشرح
### العقبات الشائعة
- **حجم البيانات:** يجب أن تكون البيانات التي تتم إضافتها إلى SourceBuffer مناسبة من حيث الحجم، وإلا قد تتسبب في حدوث أخطاء.
- **توقيت الإضافة:** يجب أن يتم إضافة البيانات فقط عندما يكون SourceBuffer في حالة `updating`، وإلا سيتسبب ذلك في أخطاء.
- **التوافق مع المتصفحات:** تأكد من أن المتصفح الذي تستخدمه يدعم الميزات المطلوبة وتهيئة الكود بشكل صحيح.

## ملخص بعبارة واحدة
SourceBuffer في JavaScript هو واجهة حيوية لإدارة تدفقات البيانات في الوسائط المتعددة، مما يسهل التشغيل المتقطع للوسائط مثل الفيديو والصوت.