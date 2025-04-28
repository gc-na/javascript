<!--
Meta Description: # قياس النصوص في JavaScript: TextMetrics ## الملخص TextMetrics هي واجهة في JavaScript تُستخدم لتوفير معلومات حول قياسات النصوص، مما يساعد المطورين في ...
Meta Keywords: النصوص, canvas, const, textmetrics, context
-->

# قياس النصوص في JavaScript: TextMetrics

## الملخص
TextMetrics هي واجهة في JavaScript تُستخدم لتوفير معلومات حول قياسات النصوص، مما يساعد المطورين في التعامل مع النصوص بشكل أكثر فعالية واحترافية.

## الوثائق
تُستخدم واجهة TextMetrics لقياس خصائص النصوص مثل العرض والارتفاع، مما يوفر معلومات دقيقة حول كيفية عرض النص داخل عناصر HTML. يتم الحصول على كائن TextMetrics عادةً من خلال استخدام دالة `measureText()` الخاصة بكائن السياق في Canvas API، والتي تُستخدم في رسم النصوص على لوحات الرسم.

### الغرض
الغرض من TextMetrics هو تمكين المطورين من قياس النصوص بدقة، مما يساعد في تصميم واجهات مستخدم أكثر فعالية، خاصةً عند التعامل مع الرسومات والنصوص المختلطة.

### الاستخدام
للحصول على قياسات نص معين، يجب أولاً إنشاء كائن Canvas، ثم استخدام دالة `measureText()` كما يلي:

```javascript
const canvas = document.createElement('canvas');
const context = canvas.getContext('2d');
context.font = '16px Arial';
const metrics = context.measureText('نص تجريبي');
```

### التفاصيل
- **العرض (width)**: يمثل عرض النص المنقوش.
- **الارتفاع (height)**: يُشير إلى ارتفاع النص، ولكنه غير مُعطى مباشرةً، لذا يمكن حسابه بناءً على إعدادات الخط المستخدمة.
- **سطر الارتفاع (actualBoundingBoxAscent و actualBoundingBoxDescent)**: يوفر معلومات إضافية حول ارتفاع النص بناءً على محتواه.

## الأمثلة
### مثال بسيط
```javascript
const canvas = document.createElement('canvas');
const context = canvas.getContext('2d');
context.font = '20px Arial';
const metrics = context.measureText('مرحبا بالعالم');
console.log('عرض النص:', metrics.width);
```

### قياس نصوص متعددة
```javascript
const texts = ['نص أول', 'نص ثاني', 'نص ثالث'];
texts.forEach(text => {
    const metrics = context.measureText(text);
    console.log(`عرض "${text}":`, metrics.width);
});
```

## الشرح
قد يواجه المطورون بعض المشكلات عند استخدام TextMetrics، مثل:

- **مقياس الخط**: يجب التأكد من أن الخط مُعين بشكل صحيح قبل القياس. إذا كان الخط غير موجود أو غير مُعرف، قد تُعطي النتائج قياسات غير دقيقة.
- **الخطوط المتغيرة**: قد تختلف القياسات بين الخطوط المختلفة، لذا من المهم اختبار النصوص مع الخطوط المستهدفة.
- **القياسات المرتبطة**: لا يتم توفير الارتفاع بشكل مباشر، مما قد يتطلب حسابات إضافية بناءً على إعدادات الخط.

## ملخص بعبارة واحدة
TextMetrics في JavaScript تُتيح قياس خصائص النصوص لتسهيل تصميم واجهات مستخدم فعّالة.