<!--
Meta Description: # عنصر SVGLinearGradientElement في JavaScript: الاستخدامات والميزات ## ملخص يعد عنصر `SVGLinearGradientElement` جزءًا من واجهة SVG في JavaScript، ويست...
Meta Keywords: stop, svg, defs, 100, offset
-->

# عنصر SVGLinearGradientElement في JavaScript: الاستخدامات والميزات

## ملخص
يعد عنصر `SVGLinearGradientElement` جزءًا من واجهة SVG في JavaScript، ويستخدم لإنشاء تدرجات لونية خطية يمكن تطبيقها على الأشكال المختلفة في الرسومات المتجهة.

## الوثائق
### الوصف
`SVGLinearGradientElement` هو عنصر يمثل تدرجًا لونيًا خطيًا يستخدم في SVG (Scalable Vector Graphics). يتيح للمطورين إنشاء تدرجات لونية سلسة يمكن أن تتغير من لون إلى آخر على طول خط مستقيم. يعد هذا العنصر مفيدًا في تصميم واجهات المستخدم والرسومات البيانية، حيث يمكن استخدامه لإضفاء تأثيرات جمالية على الأشكال.

### الاستخدام
يمكن استخدام `SVGLinearGradientElement` مع عناصر SVG مثل `<rect>`, `<circle>`, `<path>`, وغيرها، لتطبيق التدرجات اللونية. يتم تعريف التدرج داخل عنصر `<defs>` ويتم الإشارة إليه باستخدام خاصية `fill` أو `stroke` للأشكال المختلفة.

#### التركيب الأساسي
```html
<svg width="200" height="200">
  <defs>
    <linearGradient id="grad1" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:rgb(255,255,0);stop-opacity:1" />
      <stop offset="100%" style="stop-color:rgb(255,0,0);stop-opacity:1" />
    </linearGradient>
  </defs>
  <rect width="200" height="200" fill="url(#grad1)" />
</svg>
```

## أمثلة
### مثال 1: تدرج لوني بسيط
```html
<svg width="300" height="300">
  <defs>
    <linearGradient id="simpleGrad" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:blue;stop-opacity:1" />
      <stop offset="100%" style="stop-color:green;stop-opacity:1" />
    </linearGradient>
  </defs>
  <rect width="300" height="300" fill="url(#simpleGrad)" />
</svg>
```

### مثال 2: تدرج لوني مع أكثر من لون
```html
<svg width="400" height="400">
  <defs>
    <linearGradient id="multiGrad" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:red;stop-opacity:1" />
      <stop offset="50%" style="stop-color:yellow;stop-opacity:1" />
      <stop offset="100%" style="stop-color:blue;stop-opacity:1" />
    </linearGradient>
  </defs>
  <circle cx="200" cy="200" r="150" fill="url(#multiGrad)" />
</svg>
```

## الشرح
### الأخطاء الشائعة
- **عدم تحديد الأبعاد**: قد يؤدي عدم تحديد خصائص `x1`, `y1`, `x2`, `y2` بشكل صحيح إلى تدرجات غير مرئية أو غير متوقعة.
- **الاعتماد على التدرجات بدون تعريف**: يجب التأكد من أن التدرجات المحددة في عنصر `<defs>` موجودة قبل استخدامها في الأشكال.
- **استخدام ألوان غير مدعومة**: يجب استخدام الألوان التي تدعمها المتصفحات لضمان عدم ظهور أي مشاكل في عرض الألوان.

## ملخص
`SVGLinearGradientElement` يمكّن المطورين من إنشاء تدرجات لونية خطية جذابة في SVG باستخدام JavaScript، مما يضيف عمقًا وجمالًا للرسومات المتجهة.