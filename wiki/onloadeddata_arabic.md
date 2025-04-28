<!--
Meta Description: # الحدث "onloadeddata" في JavaScript: دليل شامل ## ملخص يعد حدث "onloadeddata" واحدًا من الأحداث المهمة في JavaScript والتي تُستخدم مع عناصر الوسائط م...
Meta Keywords: onloadeddata, حدث, الوسائط, البيانات, الحدث
-->

# الحدث "onloadeddata" في JavaScript: دليل شامل

## ملخص
يعد حدث "onloadeddata" واحدًا من الأحداث المهمة في JavaScript والتي تُستخدم مع عناصر الوسائط مثل الفيديو والصوت. يتم تفعيل هذا الحدث عند تحميل البيانات الأولية لوسائط الفيديو أو الصوت، مما يعني أن البيانات أصبحت جاهزة للتشغيل.

## الوثائق
### الغرض
يستخدم حدث "onloadeddata" للإشارة إلى أن بيانات الوسائط (مثل الفيديو أو الصوت) قد تم تحميلها بنجاح، مما يسمح للمطورين بتحديد الإجراءات التي يجب اتخاذها عند تحميل البيانات، مثل بدء تشغيل الفيديو تلقائيًا.

### الاستخدام
يتم استخدام حدث "onloadeddata" مع عناصر الوسائط في HTML5. يمكن إضافة معالج لهذا الحدث باستخدام خاصية الأحداث في JavaScript.

### التفاصيل
- **النوع**: حدث
- **الهدف**: إشعار المستخدم بتحميل البيانات
- **الإصدار**: HTML5
- **النمط**: `element.onloadeddata = function() { ... }` أو `element.addEventListener('loadeddata', function() { ... });`

## الأمثلة
### مثال أساسي
```html
<video id="myVideo" width="320" height="240" controls>
    <source src="movie.mp4" type="video/mp4">
    Your browser does not support the video tag.
</video>

<script>
    const videoElement = document.getElementById('myVideo');
    
    videoElement.onloadeddata = function() {
        console.log('تم تحميل البيانات بشكل كامل.');
    };
</script>
```

### استخدام addEventListener
```html
<audio id="myAudio" controls>
    <source src="audio.mp3" type="audio/mpeg">
    Your browser does not support the audio tag.
</audio>

<script>
    const audioElement = document.getElementById('myAudio');

    audioElement.addEventListener('loadeddata', function() {
        console.log('تم تحميل بيانات الصوت.');
    });
</script>
```

## الشرح
عند استخدام حدث "onloadeddata"، يجب أن تكون على علم بأن:
- هذا الحدث لا يعني بالضرورة أن الوسائط قد بدأت في التشغيل، بل يعني فقط أن البيانات قد تم تحميلها.
- قد يحدث هذا الحدث عدة مرات، خاصةً عند تحميل أجزاء جديدة من الوسائط.
- إذا كان لديك معالج أحداث آخر مثل "oncanplay"، فقد ترغب في استخدامه أيضًا لتحديد متى يمكن البدء في التشغيل.

## ملخص من سطر واحد
يستخدم حدث "onloadeddata" في JavaScript للإشارة إلى أن بيانات الوسائط قد تم تحميلها بنجاح، مما يسهل التحكم في تشغيل المحتوى.