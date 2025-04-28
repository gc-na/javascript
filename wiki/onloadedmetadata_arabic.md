<!--
Meta Description: # حدث onloadedmetadata في JavaScript: دليل شامل ## ملخص حدث `onloadedmetadata` في JavaScript هو حدث يُستخدم مع عناصر الوسائط مثل `<audio>` و`<video>` ...
Meta Keywords: onloadedmetadata, بيانات, التعريف, audio, video
-->

# حدث onloadedmetadata في JavaScript: دليل شامل

## ملخص
حدث `onloadedmetadata` في JavaScript هو حدث يُستخدم مع عناصر الوسائط مثل `<audio>` و`<video>` للإشارة إلى أن بيانات التعريف (metadata) للوسائط قد تم تحميلها بالكامل. يُعتبر هذا الحدث مفيدًا للتفاعل مع معلومات مثل مدة الملف أو أبعاد الفيديو.

## الوثائق
### الغرض
يتم استخدام حدث `onloadedmetadata` لإعلام المطورين بأن بيانات التعريف للوسائط قد أصبحت متاحة. يتضمن ذلك معلومات مثل مدة الصوت أو الفيديو، عرض الفيديو وطوله، مما يتيح للمطورين اتخاذ الإجراءات المناسبة مثل إعداد واجهة المستخدم أو بدء التشغيل التلقائي.

### الاستخدام
يمكن ربط الحدث `onloadedmetadata` بعناصر `<audio>` و`<video>` باستخدام JavaScript. يتم تفعيل هذا الحدث تلقائيًا عند تحميل بيانات التعريف.

#### كيفية الاستخدام:
```javascript
const videoElement = document.getElementById('myVideo');

videoElement.onloadedmetadata = function() {
    console.log('تم تحميل بيانات التعريف للفيديو.');
    console.log('مدة الفيديو: ' + videoElement.duration + ' ثواني');
};
```

## الأمثلة
### مثال بسيط
```html
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>مثال onloadedmetadata</title>
</head>
<body>
    <video id="myVideo" controls>
        <source src="video.mp4" type="video/mp4">
        متصفحك لا يدعم عنصر الفيديو.
    </video>

    <script>
        const videoElement = document.getElementById('myVideo');

        videoElement.onloadedmetadata = function() {
            console.log('تم تحميل بيانات التعريف للفيديو.');
            console.log('مدة الفيديو: ' + videoElement.duration + ' ثواني');
        };
    </script>
</body>
</html>
```

### مثال مع عنصر الصوت
```html
<audio id="myAudio" controls>
    <source src="audio.mp3" type="audio/mp3">
    متصفحك لا يدعم عنصر الصوت.
</audio>

<script>
    const audioElement = document.getElementById('myAudio');

    audioElement.onloadedmetadata = function() {
        console.log('تم تحميل بيانات التعريف للصوت.');
        console.log('مدة الصوت: ' + audioElement.duration + ' ثواني');
    };
</script>
```

## الشرح
### الأخطاء الشائعة
- **عدم الاستجابة للحدث**: تأكد من أن العنصر موجود في DOM قبل محاولة ربط الحدث به.
- **عدم دعم المتصفح**: تأكد من أن المتصفح المستخدم يدعم عناصر `<audio>` و`<video>`، وأن الملفات المستخدمة متوافقة مع هذه العناصر.
- **عدم تحميل البيانات**: في بعض الأحيان، إذا لم يتم تحميل الملف بشكل صحيح، قد لا يتم تفعيل الحدث.

### ملاحظات إضافية
- يُفضل استخدام الحدث `onloadedmetadata` بدلاً من `onload` لأنه يوفر معلومات دقيقة حول الوسائط.
- يمكن استخدام هذا الحدث لتشغيل الفيديو أو الصوت تلقائيًا بعد تحميل بيانات التعريف، لكن يجب مراعاة تجربة المستخدم.

## ملخص جملة واحدة
حدث `onloadedmetadata` في JavaScript يُستخدم للإشارة إلى أن بيانات التعريف للوسائط قد تم تحميلها، مما يتيح للمطورين الوصول إلى معلومات مثل مدة الوسائط.