<!--
Meta Description: # عنصر SVGImageElement في JavaScript: الدليل الشامل ## ملخص عنصر SVGImageElement هو واجهة تمثل عنصر الصورة داخل SVG (Scalable Vector Graphics) في مستن...
Meta Keywords: الصورة, svg, عنصر, width, height
-->

# عنصر SVGImageElement في JavaScript: الدليل الشامل

## ملخص
عنصر SVGImageElement هو واجهة تمثل عنصر الصورة داخل SVG (Scalable Vector Graphics) في مستندات HTML. يتيح لك استخدام JavaScript التحكم في خصائص الصورة، مثل المصدر، الأبعاد، والمزيد.

## الوثائق
### الغرض
يستخدم SVGImageElement لإدراج صور نقطية في عناصر SVG. يتيح لك هذا العنصر التعامل مع الصور ضمن الرسوميات المتجهة، مما يوفر مرونة أكبر في تصميم واجهات المستخدم.

### الاستخدام
يمكن استخدام عنصر SVGImageElement بطرق متعددة، مثل:

- تحميل صورة من ملف خارجي.
- تعديل خصائص الصورة باستخدام JavaScript.
- تضمين الصور في الرسوميات المتجهة عالية الدقة.

### التفاصيل
يتم إنشاء عنصر SVGImageElement باستخدام عنصر `<image>` داخل SVG. يمكن الوصول إليه وتعديله باستخدام JavaScript. فيما يلي الخصائص الأساسية التي يمكن تعديلها:

- `href`: تحديد مسار الصورة.
- `width`: تحديد عرض الصورة.
- `height`: تحديد ارتفاع الصورة.

## الأمثلة
### مثال 1: إضافة صورة بسيطة إلى SVG
```html
<svg width="500" height="500">
  <image href="image.png" width="200" height="200" />
</svg>
```

### مثال 2: تعديل خصائص الصورة باستخدام JavaScript
```html
<svg width="500" height="500" id="mySvg">
  <image id="myImage" href="image.png" width="200" height="200" />
</svg>

<script>
  const imageElement = document.getElementById('myImage');
  imageElement.setAttribute('href', 'newImage.png');
  imageElement.setAttribute('width', '300');
  imageElement.setAttribute('height', '300');
</script>
```

## الشرح
### الأخطاء الشائعة
- **مسار الصورة غير صحيح**: تأكد من أن مسار الصورة المحدد في `href` صحيح. إذا كان غير صحيح، فلن تظهر الصورة.
- **عدم تحديد الأبعاد**: يجب تحديد أبعاد الصورة (`width` و `height`) لضمان عرضها بشكل صحيح داخل SVG.
- **توافق المتصفح**: تأكد من أن المتصفح الذي تستخدمه يدعم عناصر SVG بشكل كامل، حيث أن بعض المتصفحات الأقدم قد تواجه مشكلات في عرض SVG.

### ملاحظات إضافية
- يمكن استخدام خاصية `preserveAspectRatio` لتحديد كيفية عرض الصورة داخل العناصر المحددة.
- تأكد من استخدام تنسيقات الصور المدعومة مثل PNG وJPEG.

## ملخص من سطر واحد
عنصر SVGImageElement في JavaScript يتيح لك إدراج وتعديل الصور داخل مستندات SVG بسهولة ومرونة.