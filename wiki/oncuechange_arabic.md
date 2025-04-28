<!--
Meta Description: # الحدث oncuechange في JavaScript: دليلك الشامل ## الملخص يعتبر حدث `oncuechange` في JavaScript من الأحداث المهمة التي تتعامل مع عناصر الوسائط المتعدد...
Meta Keywords: video, oncuechange, activecues, javascript, القوس
-->

# الحدث oncuechange في JavaScript: دليلك الشامل

## الملخص
يعتبر حدث `oncuechange` في JavaScript من الأحداث المهمة التي تتعامل مع عناصر الوسائط المتعددة، حيث يحدث هذا الحدث عندما يتغير حالة الترجمة أو التعليق الصوتي في عنصر الفيديو أو الصوت. 

## الوثائق
### الغرض
يستخدم حدث `oncuechange` لمراقبة التغييرات التي تحدث في الترجمة أو التعليق الصوتي، مما يسمح للمطورين بالتفاعل مع هذه التغييرات وتقديم تجربة مستخدم أكثر تفاعلية.

### الاستخدام
للاستفادة من حدث `oncuechange`، يمكن إضافته كحدث على عنصر `<video>` أو `<audio>` في HTML، ويتم ربطه بوظيفة JavaScript يتم تنفيذها عند حدوث التغيير.

#### التركيب
```javascript
mediaElement.oncuechange = function() {
    // الوظيفة التي سيتم تنفيذها عند حدوث تغيير
};
```

### التفاصيل
- **العنصر المدعوم**: يجب أن يكون العنصر من نوع `<video>` أو `<audio>`.
- **التنفيذ**: يتم استدعاء الدالة المرتبطة بالحدث في كل مرة يتغير فيها القوس (cue) النشط.
- **الخصائص**: يمكن استخدام خصائص العنصر لتحديد معلومات حول القوس النشط الحالي مثل النص أو التوقيت.

## الأمثلة
### مثال بسيط
```html
<video id="myVideo" controls>
    <track kind="subtitles" src="subtitles_en.vtt" srclang="en" label="English">
    <source src="movie.mp4" type="video/mp4">
    Your browser does not support the video tag.
</video>

<script>
    const videoElement = document.getElementById('myVideo');

    videoElement.oncuechange = function() {
        const activeCue = videoElement.textTracks[0].activeCues[0];
        if (activeCue) {
            console.log('تغيير القوس النشط:', activeCue.text);
        }
    };
</script>
```

### مثال متقدم
```html
<video id="advancedVideo" controls>
    <track kind="captions" src="captions.vtt" srclang="en" label="English">
    <source src="advanced_movie.mp4" type="video/mp4">
    Your browser does not support the video tag.
</video>

<script>
    const advancedVideoElement = document.getElementById('advancedVideo');

    advancedVideoElement.oncuechange = function() {
        const activeCues = advancedVideoElement.textTracks[0].activeCues;
        for (let i = 0; i < activeCues.length; i++) {
            console.log('نص القوس النشط:', activeCues[i].text);
        }
    };
</script>
```

## الشرح
### الأخطاء الشائعة
- **عدم وجود ترجمة**: إذا لم يكن هناك أي ترجمة، فإن استخدام `oncuechange` لن يكون له تأثير ملموس.
- **عدم دعم المتصفح**: تأكد من أن المتصفح يدعم ميزات `textTracks`، حيث أن بعض المتصفحات القديمة قد لا تدعمها بشكل كامل.
- **عدم تحديث البيانات**: تأكد من أن المعلومات التي يتم استخراجها من `activeCues` صحيحة، حيث قد يحدث تداخل بين القوس النشط والزمن الحالي.

## ملخص بجملة واحدة
يعد حدث `oncuechange` في JavaScript أداة قوية لمراقبة التغييرات في الترجمة أو التعليق الصوتي داخل عناصر الوسائط المتعددة.