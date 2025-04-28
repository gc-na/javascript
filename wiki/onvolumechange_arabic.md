<!--
Meta Description: # onvolumechange في جافا سكريبت: مفهوم وأمثلة ## الملخص تعتبر خاصية `onvolumechange` في جافا سكريبت من الأحداث المهمة التي تساعد المطورين في التعامل م...
Meta Keywords: الصوت, مستوى, audio, onvolumechange, html
-->

# onvolumechange في جافا سكريبت: مفهوم وأمثلة

## الملخص
تعتبر خاصية `onvolumechange` في جافا سكريبت من الأحداث المهمة التي تساعد المطورين في التعامل مع تغييرات مستوى الصوت في عناصر الوسائط مثل الفيديو والصوت.

## الوثائق
### الغرض
تُستخدم خاصية `onvolumechange` للكشف عن التغييرات في مستوى الصوت لعناصر الصوت والفيديو. عند تغيير مستوى الصوت، يتم استدعاء هذا الحدث، مما يسمح للمطورين بتنفيذ إجراءات معينة استجابةً لذلك.

### الاستخدام
يمكن استخدام `onvolumechange` مع عناصر `<audio>` و`<video>` في HTML. يتم تعيين الوظيفة التي ترغب في تنفيذها عند حدوث الحدث، مثل تحديث واجهة المستخدم أو حفظ حالة مستوى الصوت.

### التفاصيل
تعتبر `onvolumechange` حدثًا يتم تشغيله بشكل تلقائي عند تغيير مستوى الصوت، سواء عن طريق واجهة المستخدم أو البرمجة. يمكن استخدامه لتقديم تجارب تفاعلية للمستخدمين، مثل إظهار إشعار عند زيادة أو خفض مستوى الصوت.

## الأمثلة
### مثال أساسي
```html
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>مثال على onvolumechange</title>
</head>
<body>

<audio id="myAudio" controls>
    <source src="sample.mp3" type="audio/mpeg">
    متصفحك لا يدعم عنصر الصوت.
</audio>

<script>
    const audio = document.getElementById('myAudio');

    audio.onvolumechange = function() {
        console.log('تم تغيير مستوى الصوت إلى: ' + audio.volume);
    };
</script>

</body>
</html>
```

### مثال مع واجهة مستخدم
```html
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>مثال onvolumechange مع واجهة مستخدم</title>
</head>
<body>

<audio id="myAudio" controls>
    <source src="sample.mp3" type="audio/mpeg">
    متصفحك لا يدعم عنصر الصوت.
</audio>

<div id="volumeLevel">مستوى الصوت: 1</div>

<script>
    const audio = document.getElementById('myAudio');
    const volumeLevelDiv = document.getElementById('volumeLevel');

    audio.onvolumechange = function() {
        volumeLevelDiv.textContent = 'مستوى الصوت: ' + audio.volume.toFixed(2);
    };
</script>

</body>
</html>
```

## الشرح
### الأخطاء الشائعة
1. **عدم دعم المتصفح**: تأكد من أن المتصفح يدعم الأحداث الخاصة بالصوت والفيديو.
2. **عدم الاستجابة**: تأكد من أن العنصر (مثل `<audio>` أو `<video>`) يتم تحميله بشكل صحيح قبل محاولة تعيين الحدث.
3. **تغييرات مستوى الصوت السلبية**: تذكر أن مستوى الصوت يتراوح من 0.0 إلى 1.0. أي محاولة تعيين مستوى صوت أقل من 0.0 أو أكثر من 1.0 قد تؤدي إلى عدم الاستجابة.

### ملاحظات إضافية
يمكن استخدام `onvolumechange` مع العناصر الأخرى التي تدعم مستوى الصوت، مما يوفر مرونة كبيرة في تصميم التطبيقات التفاعلية.

## ملخص جملة واحدة
`onvolumechange` هو حدث في جافا سكريبت يُستخدم للكشف عن تغييرات مستوى الصوت في عناصر الوسائط، مما يسمح بتنفيذ إجراءات تفاعلية بناءً على تلك التغييرات.