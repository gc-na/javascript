<!--
Meta Description: # عنصر HTMLTrackElement في JavaScript: دليل شامل ## ملخص يُستخدم عنصر HTMLTrackElement في JavaScript لإدارة الترجمة والعناوين الفرعية في وسائط HTML5 م...
Meta Keywords: video, src, track, htmltrackelement, kind
-->

# عنصر HTMLTrackElement في JavaScript: دليل شامل

## ملخص
يُستخدم عنصر HTMLTrackElement في JavaScript لإدارة الترجمة والعناوين الفرعية في وسائط HTML5 مثل الفيديو والصوت.

## الوثائق
### الغرض
يُعتبر HTMLTrackElement جزءًا من واجهة برمجة التطبيقات (API) الخاصة بـ HTML5، ويستخدم لإضافة مسارات الترجمة أو العناوين الفرعية إلى عناصر الفيديو والصوت. يمكن للمتصفح عرض هذه المسارات للمستخدمين، مما يعزز إمكانية الوصول والفهم.

### الاستخدام
يتم استخدام HTMLTrackElement مع عناصر `<track>` داخل عناصر `<video>` و`<audio>`. يتضمن هذا العنصر مجموعة من الخصائص المهمة، مثل `kind`، `src`، `srclang`، و`label`. 

#### الخصائص الرئيسية:
- **kind**: يحدد نوع المسار (مثل "subtitles" أو "captions").
- **src**: يحدد عنوان URL للمسار.
- **srclang**: يحدد لغة المسار (مثل "en" للإنجليزية).
- **label**: يحدد تسمية المسار، والتي ستظهر للمستخدم.

### طريقة الاستخدام
يمكن إضافة عنصر `<track>` إلى عنصر `<video>` أو `<audio>` كما يلي:

```html
<video controls>
  <source src="video.mp4" type="video/mp4">
  <track kind="subtitles" src="subs_en.vtt" srclang="en" label="English">
  <track kind="subtitles" src="subs_ar.vtt" srclang="ar" label="العربية">
  Your browser does not support the video tag.
</video>
```

## الأمثلة
### مثال 1: إضافة ترجمات باللغة الإنجليزية
```html
<video controls>
  <source src="movie.mp4" type="video/mp4">
  <track kind="subtitles" src="subs_en.vtt" srclang="en" label="English">
</video>
```

### مثال 2: إضافة عناوين فرعية باللغة العربية
```html
<video controls>
  <source src="movie.mp4" type="video/mp4">
  <track kind="subtitles" src="subs_ar.vtt" srclang="ar" label="العربية">
</video>
```

## الشرح
### الأخطاء الشائعة
- **عدم تحميل ملفات VTT**: تأكد من أن مسارات الترجمة صحيحة وأن الملفات متاحة على الخادم.
- **إغفال الخصائص**: إذا لم يتم ضبط الخصائص بشكل صحيح، فقد لا تظهر العناوين الفرعية أو الترجمة كما هو متوقع.
- **عدم دعم المتصفح**: تأكد من اختبار الوظائف على مجموعة من المتصفحات، حيث قد تكون هناك اختلافات في دعم HTMLTrackElement.

### ملاحظات إضافية
- يمكن أن يؤدي استخدام عناصر `<track>` بشكل صحيح إلى تحسين تجربة المستخدم بشكل كبير، خاصةً للأشخاص الذين يحتاجون إلى دعم لغوي إضافي.

## ملخص جملة واحدة
يتيح عنصر HTMLTrackElement في JavaScript إضافة ترجمات وعناوين فرعية إلى وسائط HTML5، مما يسهل الوصول والفهم للمستخدمين.