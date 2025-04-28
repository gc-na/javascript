<!--
Meta Description: # ImageCapture في جافا سكريبت: التقاط الصور من الكاميرات ## ملخص تُستخدم واجهة `ImageCapture` في جافا سكريبت لالتقاط الصور من الكاميرات المتصلة، مثل ك...
Meta Keywords: error, imagecapture, img, التقاط, const
-->

# ImageCapture في جافا سكريبت: التقاط الصور من الكاميرات

## ملخص
تُستخدم واجهة `ImageCapture` في جافا سكريبت لالتقاط الصور من الكاميرات المتصلة، مثل كاميرات الويب أو كاميرات الهواتف الذكية، مما يوفر وسيلة مرنة وسهلة للتفاعل مع الأجهزة.

## التوثيق
### الغرض
تتيح واجهة `ImageCapture` للمطورين التقاط الصور من وسائط الفيديو، مما يوفر إمكانية الوصول المباشر إلى الصور الثابتة من كاميرا الفيديو. يُستخدم هذا في التطبيقات التي تتطلب التقاط صور فورية، مثل تطبيقات المراسلة أو البرامج التعليمية.

### الاستخدام
للاستفادة من واجهة `ImageCapture`، يجب أولاً الحصول على كائن `MediaStream` من الكاميرا. يمكن ذلك باستخدام واجهة `navigator.mediaDevices.getUserMedia`. بعد ذلك، يتم إنشاء كائن `ImageCapture` باستخدام كائن `MediaStreamTrack`.

### التفاصيل
- **إنشاء كائن `ImageCapture`:** 
  لإنشاء كائن `ImageCapture`، يجب أولاً الحصول على `MediaStream` من الكاميرا:
  ```javascript
  navigator.mediaDevices.getUserMedia({ video: true })
    .then((stream) => {
      const track = stream.getVideoTracks()[0];
      const imageCapture = new ImageCapture(track);
    })
    .catch((error) => console.error('Error accessing media devices.', error));
  ```

- **التقاط صورة:**
  بعد إنشاء كائن `ImageCapture`، يمكن التقاط صورة باستخدام الدالة `takePhoto`:
  ```javascript
  imageCapture.takePhoto()
    .then((blob) => {
      const img = document.createElement('img');
      img.src = URL.createObjectURL(blob);
      document.body.appendChild(img);
    })
    .catch((error) => console.error('Error taking photo:', error));
  ```

## الأمثلة
### مثال 1: التقاط صورة واحدة من الكاميرا
```javascript
navigator.mediaDevices.getUserMedia({ video: true })
  .then((stream) => {
    const track = stream.getVideoTracks()[0];
    const imageCapture = new ImageCapture(track);
    
    imageCapture.takePhoto()
      .then((blob) => {
        const img = document.createElement('img');
        img.src = URL.createObjectURL(blob);
        document.body.appendChild(img);
      })
      .catch((error) => console.error('Error taking photo:', error));
  })
  .catch((error) => console.error('Error accessing media devices.', error));
```

### مثال 2: التقاط صورة مع إعدادات معينة
```javascript
imageCapture.takePhoto({ fillLightMode: 'on' })
  .then((blob) => {
    const img = document.createElement('img');
    img.src = URL.createObjectURL(blob);
    document.body.appendChild(img);
  })
  .catch((error) => console.error('Error taking photo:', error));
```

## الشرح
### الأخطاء الشائعة
- **عدم الحصول على إذن:** تأكد من أنك قد حصلت على إذن لاستخدام كاميرا الجهاز. فشل الحصول على إذن سيؤدي إلى عدم تمكنك من التقاط الصور.
- **عدم دعم المتصفح:** تأكد من أن المتصفح الذي تستخدمه يدعم واجهة `ImageCapture`. ليس جميع المتصفحات تدعم هذه الواجهة بالكامل.
- **التقاط صورة بمجرد النقر:** قد يؤدي التقاط صورة في نفس اللحظة التي يتم فيها تشغيل الفيديو إلى الحصول على صورة غير واضحة. يُفضل الانتظار لبضع ثوانٍ بعد بدء الفيديو.

## ملخص من جملة واحدة
تتيح واجهة `ImageCapture` في جافا سكريبت التقاط الصور مباشرة من الكاميرات المتصلة، مما يوفر وسيلة سهلة وفعالة للتفاعل مع وسائط الفيديو.