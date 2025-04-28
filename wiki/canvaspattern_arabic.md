<!--
Meta Description: # CanvasPattern في جافا سكريبت: كيفية استخدام الأنماط في الرسم على الـ Canvas ## ملخص CanvasPattern هي كائن في واجهة Canvas API في جافا سكريبت تُستخدم...
Meta Keywords: canvas, الصورة, repeat, image, استخدام
-->

# CanvasPattern في جافا سكريبت: كيفية استخدام الأنماط في الرسم على الـ Canvas

## ملخص
CanvasPattern هي كائن في واجهة Canvas API في جافا سكريبت تُستخدم لإنشاء أنماط مخصصة يمكن تطبيقها على رسومات الـ Canvas. تتيح هذه الأنماط إمكانية تعبئة الأشكال والتصاميم باستخدام الصور أو الأنماط المكررة.

## الوثائق
### الغرض
تُستخدم CanvasPattern لتسهيل عملية إضافة أنماط معقدة مثل الصور أو الأشكال المكررة، بحيث يمكن استخدامها كخلفيات أو لتزيين الأشكال على الـ Canvas.

### الاستخدام
لإنشاء CanvasPattern، يجب استخدام دالة `createPattern()` المتاحة في كائن CanvasRenderingContext2D. تأخذ هذه الدالة معطين: الصورة أو العنصر الذي تريد استخدامه كقالب، ونمط التكرار (مثل "repeat"، "repeat-x"، "repeat-y" أو "no-repeat").

### التفاصيل
- **إنشاء نمط**: 
    ```javascript
    let pattern = context.createPattern(image, repeat);
    ```
- **المعطيات**:
  - `image`: يمكن أن تكون صورة، عنصر `<canvas>`, أو عنصر `<video>`.
  - `repeat`: نوع التكرار، يمكن أن يكون واحدًا من القيم التالية:
    - `"repeat"`: تكرار الصورة في كلا الاتجاهين.
    - `"repeat-x"`: تكرار الصورة أفقيًا فقط.
    - `"repeat-y"`: تكرار الصورة عموديًا فقط.
    - `"no-repeat"`: عدم تكرار الصورة.

## أمثلة
### مثال بسيط على استخدام CanvasPattern
```javascript
// إعداد الـ Canvas
const canvas = document.getElementById('myCanvas');
const context = canvas.getContext('2d');

// تحميل الصورة
const image = new Image();
image.src = 'path/to/image.png';
image.onload = function() {
    // إنشاء نمط
    const pattern = context.createPattern(image, 'repeat');

    // استخدام النمط لتعبئة مستطيل
    context.fillStyle = pattern;
    context.fillRect(0, 0, canvas.width, canvas.height);
};
```

## الشرح
### المشكلات الشائعة
- **تأخير تحميل الصورة**: تأكد من أن الصورة قد تم تحميلها بالكامل قبل استخدام `createPattern()`. يُفضل استخدام حدث `onload` لضمان جاهزية الصورة.
- **عدم ظهور النمط**: إذا كان النمط غير مرئي، تحقق من حجم الصورة ونوع التكرار المستخدم. قد يكون من المفيد استخدام نمط تكرار مختلف أو تعديل أبعاد الصورة.

### ملاحظات إضافية
- يمكن أن تؤثر أنماط Canvas على أداء الرسومات إذا كانت الصورة كبيرة جدًا أو إذا تم استخدامها بكثرة. تأكد من تحسين الصور المستخدمة.

## ملخص جملة واحدة
CanvasPattern في جافا سكريبت هو أداة قوية لإنشاء أنماط مخصصة للرسم على الـ Canvas باستخدام الصور أو الأشكال المكررة.