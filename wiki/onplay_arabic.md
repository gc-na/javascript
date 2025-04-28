<!--
Meta Description: # وظيفة onplay في جافا سكريبت: دليل شامل ## ملخص وظيفة `onplay` في جافا سكريبت هي حدث يتم تفعيله عندما يبدأ تشغيل محتوى الوسائط، مثل الفيديو أو الصوت....
Meta Keywords: video, onplay, audio, تشغيل, script
-->

# وظيفة onplay في جافا سكريبت: دليل شامل

## ملخص
وظيفة `onplay` في جافا سكريبت هي حدث يتم تفعيله عندما يبدأ تشغيل محتوى الوسائط، مثل الفيديو أو الصوت. تُستخدم هذه الوظيفة بشكل شائع في تطوير واجهات المستخدم والتطبيقات التفاعلية.

## التوثيق
تُستخدم `onplay` كحدث في عناصر الوسائط مثل `<video>` و`<audio>`. الهدف من هذا الحدث هو السماح للمطورين بتنفيذ شيفرة معينة عندما يبدأ تشغيل الوسائط، مما يوفر تفاعلية أكبر للمستخدمين. يمكن استخدام `onplay` لتفعيل ميزات مثل عرض الرسائل، أو تحديث واجهات المستخدم، أو بدء مؤقتات.

### الاستخدام
لتطبيق وظيفة `onplay`، يمكنك إضافة معالج الحدث مباشرة إلى عنصر الوسائط في HTML أو استخدام JavaScript لإضافته بعد تحميل الصفحة. إليك هيكل الاستخدام:

```html
<video id="myVideo" controls>
    <source src="video.mp4" type="video/mp4">
    Your browser does not support the video tag.
</video>

<script>
    const video = document.getElementById('myVideo');
    video.onplay = function() {
        console.log('بدأ تشغيل الفيديو!');
    };
</script>
```

## الأمثلة
### مثال أساسي
في هذا المثال، سنقوم بعرض رسالة في وحدة التحكم عندما يبدأ الفيديو في التشغيل:

```html
<audio id="myAudio" controls>
    <source src="audio.mp3" type="audio/mpeg">
    Your browser does not support the audio tag.
</audio>

<script>
    const audio = document.getElementById('myAudio');
    audio.onplay = function() {
        console.log('بدأ تشغيل الصوت!');
    };
</script>
```

### مثال متقدم
يمكنك استخدام `onplay` لبدء مؤقت أو لتغيير نمط واجهة المستخدم:

```html
<video id="myVideo" controls>
    <source src="video.mp4" type="video/mp4">
    Your browser does not support the video tag.
</video>

<script>
    const video = document.getElementById('myVideo');
    video.onplay = function() {
        // تغيير لون الخلفية عند بدء التشغيل
        document.body.style.backgroundColor = 'lightblue';
        console.log('بدأ تشغيل الفيديو مع تغيير لون الخلفية!');
    };
</script>
```

## الشرح
### الأخطاء الشائعة
- **عدم تفعيل الحدث عند التشغيل**: تأكد من أن العنصر يحتوي على مصدر وسائط صحيح وأنه تم تحميله بشكل كامل.
- **تعارض مع أحداث أخرى**: قد تؤدي إضافة عدة معالجات لحدث `onplay` إلى تعارضات، لذا تأكد من إدارة الأحداث بشكل صحيح.

### ملاحظات إضافية
- يمكن استخدام `onplay` بالتوازي مع أحداث أخرى مثل `onpause` و`onended` لتحسين تجربة المستخدم.
- تأكد من اختبار الوظيفة في متصفحات متعددة لضمان التوافق.

## ملخص بجملة واحدة
وظيفة `onplay` في جافا سكريبت تُستخدم لتفعيل أحداث معينة عند بدء تشغيل محتوى الوسائط، مما يعزز التفاعل مع المستخدم.