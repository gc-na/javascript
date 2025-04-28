<!--
Meta Description: # MediaRecorder في JavaScript: توثيق شامل ## ملخص تعتبر واجهة `MediaRecorder` في JavaScript أداة قوية لتسجيل الوسائط مثل الصوت والفيديو مباشرة من المت...
Meta Keywords: mediarecorder, video, function, javascript, واجهة
-->

# MediaRecorder في JavaScript: توثيق شامل

## ملخص
تعتبر واجهة `MediaRecorder` في JavaScript أداة قوية لتسجيل الوسائط مثل الصوت والفيديو مباشرة من المتصفح، مما يتيح للمطورين إنشاء تطبيقات تفاعلية ومتعددة الوسائط بسهولة.

## التوثيق
تُستخدم واجهة `MediaRecorder` لتسجيل البيانات من `MediaStream`، مثل تدفقات الفيديو والصوت التي يتم الحصول عليها من الكاميرا والميكروفون. يمكن استخدام هذه الواجهة لإنشاء تطبيقات تتطلب تسجيلات صوتية أو فيديو، مثل أدوات تسجيل الشاشة أو التطبيقات الاجتماعية.

### الاستخدام
للبدء باستخدام `MediaRecorder`، يجب أولاً الحصول على `MediaStream`، والذي يمكن الحصول عليه من خلال `getUserMedia` أو APIs مشابهة. بعد ذلك، يمكنك إنشاء كائن `MediaRecorder` كما يلي:

```javascript
navigator.mediaDevices.getUserMedia({ audio: true, video: true })
    .then(function(stream) {
        const mediaRecorder = new MediaRecorder(stream);
        // باقي الكود هنا
    })
    .catch(function(err) {
        console.log("حدث خطأ: " + err);
    });
```

### الخصائص والطرق
- **الخصائص**:
  - `state`: تُظهر حالة التسجيل، مثل "inactive" أو "recording".
  - `mimeType`: تُظهر نوع الوسائط المستخدم.

- **الطرق**:
  - `start()`: يبدأ التسجيل.
  - `stop()`: يوقف التسجيل.
  - `requestData()`: يطلب البيانات المسجلة حتى الآن.

## أمثلة
### مثال بسيط لتسجيل الصوت والفيديو
```javascript
navigator.mediaDevices.getUserMedia({ audio: true, video: true })
    .then(function(stream) {
        const mediaRecorder = new MediaRecorder(stream);
        let chunks = [];

        mediaRecorder.ondataavailable = function(event) {
            chunks.push(event.data);
        };

        mediaRecorder.onstop = function() {
            const blob = new Blob(chunks, { type: 'video/webm' });
            const url = URL.createObjectURL(blob);
            const video = document.createElement('video');
            video.src = url;
            video.controls = true;
            document.body.appendChild(video);
            video.play();
        };

        mediaRecorder.start();

        setTimeout(() => {
            mediaRecorder.stop();
        }, 5000); // تسجيل لمدة 5 ثوان
    })
    .catch(function(err) {
        console.log("حدث خطأ: " + err);
    });
```

## الشرح
### الأخطاء الشائعة
- **عدم دعم المتصفح**: تأكد من أن المتصفح يدعم واجهة `MediaRecorder`. يمكنك التحقق من ذلك باستخدام `MediaRecorder.isTypeSupported()`.
- **أذونات المستخدم**: تأكد من منح الأذونات اللازمة للوصول إلى الميكروفون والكاميرا.
- **إعدادات MIME**: تأكد من استخدام نوع MIME مدعوم عند إنشاء كائن `MediaRecorder`.

### ملاحظات إضافية
- يمكن استخدام واجهة `MediaRecorder` مع مكتبات أخرى مثل `ffmpeg.js` لتحويل وتحرير التسجيلات.
- يجب فحص حجم البيانات المسجلة، خصوصًا عند التسجيل لفترات طويلة، لضمان الأداء السلس.

## ملخص جملة واحدة
واجهة `MediaRecorder` في JavaScript توفر طريقة فعالة لتسجيل الصوت والفيديو من المتصفح، مما يمكّن المطورين من إنشاء تطبيقات وسائط متعددة بشكل سهل وسريع.