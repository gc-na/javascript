<!--
Meta Description: # CanvasCaptureMediaStreamTrack في JavaScript: دليلك الشامل ## الملخص تعتبر CanvasCaptureMediaStreamTrack من الخصائص المفيدة في JavaScript التي تتيح ل...
Meta Keywords: canvas, const, canvascapturemediastreamtrack, تيار, ctx
-->

# CanvasCaptureMediaStreamTrack في JavaScript: دليلك الشامل

## الملخص
تعتبر CanvasCaptureMediaStreamTrack من الخصائص المفيدة في JavaScript التي تتيح لك التقاط محتوى عنصر `<canvas>` وتحويله إلى تيار وسائط يمكن استخدامه في تطبيقات الويب.

## الوثائق
### الغرض
تساعد CanvasCaptureMediaStreamTrack في التقاط الرسومات المتحركة أو الصور الثابتة من عنصر canvas، مما يتيح للمطورين إمكانية مشاركة هذه الرسومات عبر الشبكة أو استخدامها في تطبيقات الوسائط المتعددة.

### الاستخدام
يمكن استخدام CanvasCaptureMediaStreamTrack لإنشاء تيار وسائط MediaStream من محتوى canvas. يتطلب هذا إنشاء عنصر canvas ثم استخدام كائن `CanvasCaptureMediaStreamTrack` لتوليد تيار.

### التفاصيل
- **الإنشاء**: يتم إنشاء CanvasCaptureMediaStreamTrack من خلال استدعاء `canvas.captureStream()`.
- **الإعدادات**: يمكنك تحديد معدل الإطار (frame rate) عند التقاط المحتوى.
- **التوافق**: تدعم هذه الخاصية معظم المتصفحات الحديثة، لكنها قد لا تكون مدعومة في بعض الإصدارات القديمة.

## الأمثلة
### مثال أساسي
```javascript
// إنشاء عنصر canvas
const canvas = document.createElement('canvas');
const ctx = canvas.getContext('2d');

// رسم شيء ما على canvas
ctx.fillStyle = 'red';
ctx.fillRect(10, 10, 100, 100);

// التقاط تيار الوسائط من عنصر canvas
const stream = canvas.captureStream(30); // 30 إطارًا في الثانية

// استخدام تيار الوسائط
const videoElement = document.querySelector('video');
videoElement.srcObject = stream;
videoElement.play();
```

### مثال متقدم
```javascript
// إعداد canvas
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');

// رسم متحرك
let x = 0;
function draw() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    ctx.fillStyle = 'blue';
    ctx.fillRect(x, 20, 50, 50);
    x += 1;
    if (x > canvas.width) x = 0;
    requestAnimationFrame(draw);
}

// بدء الرسم
draw();

// التقاط تيار الوسائط
const stream = canvas.captureStream(60);
const videoElement = document.querySelector('video');
videoElement.srcObject = stream;
videoElement.play();
```

## الشرح
### العثرات الشائعة
- **عدم دعم المتصفحات**: تأكد من أن المتصفح الذي تستخدمه يدعم `captureStream()`. يمكنك استخدام أدوات مثل [Can I use](https://caniuse.com/) للتحقق من الدعم.
- **معدل الإطار**: قد يؤدي اختيار معدل إطار مرتفع جدًا إلى زيادة استهلاك الموارد. من الجيد دائمًا الاختبار للحصول على توازن بين الجودة والأداء.
- **قيود الأمان**: تأكد من أن المحتوى الذي ترسمه على canvas ليس مستمدًا من مصدر خارجي دون إذن، حيث يمكن أن تؤدي قيود CORS إلى مشاكل في التقاط التيار.

## ملخص جملة واحدة
CanvasCaptureMediaStreamTrack في JavaScript يوفر وسيلة فعالة لتوليد تيار وسائط من محتوى عنصر canvas، مما يسهل مشاركة الرسومات المتحركة في تطبيقات الويب.