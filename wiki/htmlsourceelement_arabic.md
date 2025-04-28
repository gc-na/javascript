<!--
Meta Description: # عنصر HTMLSourceElement في JavaScript: كل ما تحتاج معرفته ## ملخص عنصر `HTMLSourceElement` هو جزء من واجهة برمجة التطبيقات في JavaScript، يتعلق بعناص...
Meta Keywords: audio, video, source, عنصر, الوسائط
-->

# عنصر HTMLSourceElement في JavaScript: كل ما تحتاج معرفته

## ملخص
عنصر `HTMLSourceElement` هو جزء من واجهة برمجة التطبيقات في JavaScript، يتعلق بعناصر `<source>` التي تُستخدم في تضمين الوسائط مثل الصوت والفيديو في صفحات الويب.

## الوثائق
### الغرض
تُستخدم عناصر `HTMLSourceElement` لتوفير مصادر متعددة لجهاز تشغيل الوسائط، مما يسمح للمتصفح باختيار المصدر الأنسب بناءً على قدراته أو الفضاء المتاح.

### الاستخدام
يمكن استخدام `HTMLSourceElement` مع عناصر `<audio>` أو `<video>`، حيث يُتيح للمطورين تحديد مصادر مختلفة للوسائط. يتم تحديد كل مصدر من خلال عنصر `<source>`، والذي يتضمن سمة `src` لتحديد عنوان المصدر وسمة `type` لتحديد نوع الوسائط.

### التفاصيل
- **الخصائص**:
  - `src`: عنوان المصدر.
  - `type`: نوع الوسائط (مثل "audio/mpeg" أو "video/mp4").
- **التوافق**: مدعوم في معظم المتصفحات الحديثة.

## الأمثلة
### مثال 1: استخدام عنصر `<source>` مع `<video>`
```html
<video controls>
    <source src="video.mp4" type="video/mp4">
    <source src="video.ogg" type="video/ogg">
    Your browser does not support the video tag.
</video>
```

### مثال 2: استخدام عنصر `<source>` مع `<audio>`
```html
<audio controls>
    <source src="audio.mp3" type="audio/mpeg">
    <source src="audio.ogg" type="audio/ogg">
    Your browser does not support the audio tag.
</audio>
```

## الشرح
### الأخطاء الشائعة
- **عدم توافق الصيغ**: تأكد من أن أنواع الوسائط المدعومة متوافقة مع المتصفح، حيث أن بعض المتصفحات قد لا تدعم أنواع معينة.
- **مسارات غير صحيحة**: تحقق من صحة مسارات الملفات الموجودة في سمات `src`، حيث أن مسارًا غير صحيح سيؤدي إلى عدم تشغيل الوسائط.

### ملاحظات إضافية
- يُفضل دائمًا إضافة عنصر بديل مثل نص "متصفحك لا يدعم هذا العنصر" لتوفير تجربة مستخدم أفضل.
- يمكن استخدام JavaScript للتحكم في تشغيل الوسائط أو التبديل بين المصادر بشكل ديناميكي.

## ملخص بسيط
عنصر `HTMLSourceElement` يُستخدم لتحديد مصادر متعددة للصوت والفيديو في صفحات الويب باستخدام JavaScript.