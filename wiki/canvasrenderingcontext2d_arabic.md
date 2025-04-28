<!--
Meta Description: # CanvasRenderingContext2D في JavaScript: الدليل الشامل ## الملخص CanvasRenderingContext2D هو واجهة برمجة تطبيقات تتيح لك رسم الرسوميات ثنائية الأبعاد...
Meta Keywords: ctx, رسم, canvas, canvasrenderingcontext2d, javascript
-->

# CanvasRenderingContext2D في JavaScript: الدليل الشامل

## الملخص
CanvasRenderingContext2D هو واجهة برمجة تطبيقات تتيح لك رسم الرسوميات ثنائية الأبعاد على عنصر `<canvas>` في HTML. يوفر مجموعة متعددة من الأساليب والخصائص للتعامل مع الأشكال، النصوص، والصور.

## الوثائق
تعتبر CanvasRenderingContext2D جزءًا أساسيًا من رسم الرسوميات على الويب. يتم الحصول عليه من خلال استدعاء `getContext('2d')` على عنصر `<canvas>`. 

### الغرض
تسمح CanvasRenderingContext2D للمطورين بإنشاء رسومات ديناميكية، مثل الألعاب، الرسوم التفاعلية، والرسوم المتحركة.

### الاستخدام
للحصول على سياق الرسم، يجب أولاً إنشاء عنصر `<canvas>` ثم استخدام الكود التالي:

```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');
```

### التفاصيل
- **الخصائص**: تشمل خصائص مثل `fillStyle`, `strokeStyle`, و`lineWidth` التي تحدد مظهر الرسومات.
- **الأساليب**: هناك العديد من الأساليب مثل `fillRect()`, `strokeRect()`, `beginPath()`, و`drawImage()` التي تستخدم لرسم الأشكال والصور.
- **التنسيق**: يمكن استخدام CanvasRenderingContext2D لرسم الأشكال، النصوص، والصور بدقة عالية.

## أمثلة
### رسم مستطيل
```javascript
ctx.fillStyle = 'blue';
ctx.fillRect(10, 10, 100, 50);
```

### رسم دائرة
```javascript
ctx.beginPath();
ctx.arc(75, 75, 50, 0, Math.PI * 2);
ctx.fillStyle = 'red';
ctx.fill();
```

### رسم نص
```javascript
ctx.font = '30px Arial';
ctx.fillStyle = 'black';
ctx.fillText('مرحبًا بالعالم!', 10, 50);
```

## الشرح
### الأخطاء الشائعة
- **عدم وجود عنصر `<canvas>`**: تأكد من أن عنصر الـ canvas موجود في الـ DOM قبل استدعاء `getContext()`.
- **عدم إعداد الخصائص بشكل صحيح**: تأكد من تعيين الخصائص مثل `fillStyle` و`strokeStyle` قبل رسم الأشكال.
- **عدم إدارة السياق بشكل صحيح**: تذكر استخدام `beginPath()` عند رسم أشكال متعددة لتجنب دمجها.

### ملاحظات إضافية
- CanvasRenderingContext2D لا يدعم الرسوميات ثلاثية الأبعاد، لذا استخدم `WebGL` لهذا الغرض.
- الأداء يمكن أن يتأثر عند رسم عدد كبير من الأشكال أو عند تحديث الـ canvas بشكل متكرر.

## ملخص من جملة واحدة
CanvasRenderingContext2D هو واجهة في JavaScript تتيح رسم الرسوميات ثنائية الأبعاد على عناصر `<canvas>`، مما يوفر أدوات قوية لإنشاء محتوى بصري ديناميكي.