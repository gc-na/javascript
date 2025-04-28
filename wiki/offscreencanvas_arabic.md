<!--
Meta Description: # OffscreenCanvas في JavaScript: الرسم في الخلفية ## ملخص OffscreenCanvas هو كائن في JavaScript يتيح لك رسم المحتوى في خلفية تطبيقات الويب، مما يحسن ا...
Meta Keywords: offscreencanvas, const, context, javascript, worker
-->

# OffscreenCanvas في JavaScript: الرسم في الخلفية

## ملخص
OffscreenCanvas هو كائن في JavaScript يتيح لك رسم المحتوى في خلفية تطبيقات الويب، مما يحسن الأداء ويقلل من تحميل واجهات المستخدم.

## الوثائق
OffscreenCanvas هو واجهة تتيح لك إنشاء كائنات Canvas يمكن استخدامها في خيوط Web Worker. يهدف هذا الكائن إلى تحسين أداء الرسوميات من خلال السماح بالمعالجة الرسومية في خيوط خلفية، مما يمنع تحميل واجهة المستخدم ويؤدي إلى تجربة أكثر سلاسة.

### الغرض
تتمثل الفائدة الرئيسية من استخدام OffscreenCanvas في أنه يسمح برسم المحتوى بعيدًا عن الخيط الرئيسي، مما يحسن الأداء ويساعد في منع التجميد أو التباطؤ عند إجراء عمليات الرسم المعقدة.

### الاستخدام
لإنشاء OffscreenCanvas، يمكنك استخدام الكود التالي:

```javascript
const offscreenCanvas = new OffscreenCanvas(width, height);
```

يمكنك بعد ذلك استخدام دالة `getContext()` للحصول على سياق الرسم:

```javascript
const context = offscreenCanvas.getContext('2d');
```

بعد الحصول على السياق، يمكنك استخدامه تمامًا كما تفعل مع Canvas عادي.

## الأمثلة
### مثال 1: رسم دائرة بسيطة
```javascript
const offscreenCanvas = new OffscreenCanvas(200, 200);
const context = offscreenCanvas.getContext('2d');

context.fillStyle = 'blue';
context.beginPath();
context.arc(100, 100, 50, 0, Math.PI * 2);
context.fill();
```

### مثال 2: استخدام OffscreenCanvas مع Web Workers
```javascript
// worker.js
self.onmessage = function() {
    const offscreenCanvas = new OffscreenCanvas(200, 200);
    const context = offscreenCanvas.getContext('2d');

    context.fillStyle = 'red';
    context.fillRect(0, 0, 200, 200);

    self.postMessage(offscreenCanvas.transferToImageBitmap());
};

// main.js
const worker = new Worker('worker.js');
worker.onmessage = function(event) {
    const bitmap = event.data;
    const img = new Image();
    img.src = URL.createObjectURL(bitmap);
    document.body.appendChild(img);
};
```

## الشرح
### الأخطاء الشائعة
- **عدم التوافق**: تأكد من أن المتصفح الذي تستخدمه يدعم OffscreenCanvas. ليس كل المتصفحات تدعمه بعد.
- **مشاركة البيانات**: لا يمكن إرسال كائن OffscreenCanvas مباشرةً عبر الخيوط. يجب استخدام `transferToImageBitmap()` لنقل البيانات.

### ملاحظات إضافية
- OffscreenCanvas لا يعمل فقط مع سياق 2D، بل يمكن استخدامه مع WebGL أيضًا.
- استخدام OffscreenCanvas يمكن أن يؤدي إلى تحسين كبير في الأداء، خاصة في التطبيقات التي تتطلب رسوميات معقدة أو رسوم متحركة.

## ملخص بجملة واحدة
OffscreenCanvas في JavaScript يقدم طريقة فعالة لرسم المحتوى في الخلفية، مما يعزز الأداء ويقلل من التحميل على واجهات المستخدم.