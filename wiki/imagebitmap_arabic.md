<!--
Meta Description: # صورة بتنسيق ImageBitmap في JavaScript ## ملخص تُستخدم واجهة ImageBitmap في JavaScript لإنشاء كائنات صورة مُحسّنة لتحسين الأداء عند معالجة الصور في ا...
Meta Keywords: imagebitmap, const, img, imagedata, canvas
-->

# صورة بتنسيق ImageBitmap في JavaScript

## ملخص
تُستخدم واجهة ImageBitmap في JavaScript لإنشاء كائنات صورة مُحسّنة لتحسين الأداء عند معالجة الصور في التطبيقات، مما يساعد على تحميل الصور بشكل أسرع وأكثر كفاءة.

## الوثائق
### الغرض
تتيح واجهة ImageBitmap إمكانية التعامل مع الصور بطريقة أكثر كفاءة، حيث يتم تحميل الصور في الذاكرة دون الحاجة إلى إعادة التحميل من المصدر الأصلي. يُمكن استخدامها في بيئات مثل Canvas وWebGL.

### الاستخدام
يمكن إنشاء كائنات ImageBitmap باستخدام دالة `createImageBitmap()`. يمكن أن تأخذ هذه الدالة مجموعة متنوعة من المدخلات، مثل عناصر `<img>`، أو عناصر `<canvas>`, أو حتى بيانات البكسل.

### التفاصيل
- **المدخلات**: يمكن أن تكون المدخلات صورة (Image)، عنصر فيديو (Video)، أو كائن Canvas (HTMLCanvasElement) أو حتى بيانات بكسل (ImageData).
- **الخيارات**: يمكنك تخصيص خيارات التحميل، مثل تحديد منطقة معينة من الصورة باستخدام معلمات `sourceRect` أو تغيير حجم الصورة باستخدام معلمة `imageOrientation`.

## أمثلة
### إنشاء ImageBitmap من عنصر صورة
```javascript
const img = document.createElement('img');
img.src = 'path/to/image.jpg';

img.onload = async () => {
    const bitmap = await createImageBitmap(img);
    console.log(bitmap);
};
```

### استخدام ImageBitmap مع Canvas
```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');

const img = new Image();
img.src = 'path/to/image.jpg';

img.onload = async () => {
    const bitmap = await createImageBitmap(img);
    ctx.drawImage(bitmap, 0, 0);
};
```

### إنشاء ImageBitmap من بيانات البكسل
```javascript
const width = 100;
const height = 100;
const imageData = new ImageData(width, height);

// ملء بيانات البكسل (كمثال)
for (let i = 0; i < imageData.data.length; i += 4) {
    imageData.data[i] = 255; // الأحمر
    imageData.data[i + 1] = 0; // الأخضر
    imageData.data[i + 2] = 0; // الأزرق
    imageData.data[i + 3] = 255; // الشفافية
}

createImageBitmap(imageData).then(bitmap => {
    const canvas = document.getElementById('myCanvas');
    const ctx = canvas.getContext('2d');
    ctx.drawImage(bitmap, 0, 0);
});
```

## الشرح
### العقبات الشائعة
- **التحكم في التحميل**: تأكد من أن الصورة تم تحميلها قبل محاولة إنشاء كائن ImageBitmap منها. استخدام `onload` أو `Promise` يمكن أن يحل هذه المشكلة.
- **الدعم في المتصفحات**: تأكد من أن المتصفح الذي تستخدمه يدعم واجهة ImageBitmap، حيث قد لا تكون متاحة في بعض الإصدارات القديمة.

### ملاحظات إضافية
- **الأداء**: استخدام ImageBitmap يمكن أن يحسن الأداء في التطبيقات التي تتطلب معالجة صور بكثافة.
- **التوافق**: تأكد من مراجعة التوافق مع المتصفحات قبل استخدام هذه الواجهة في الإنتاج.

## ملخص جملة واحدة
تعتبر واجهة ImageBitmap في JavaScript أداة قوية لتحسين أداء معالجة الصور في التطبيقات، مما يوفر وسيلة فعالة لإنشاء كائنات صورة من مصادر متعددة.