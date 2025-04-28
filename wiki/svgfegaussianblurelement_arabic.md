<!--
Meta Description: # عنصر SVGFEGaussianBlurElement في JavaScript ## ملخص يعتبر عنصر SVGFEGaussianBlurElement من عناصر SVG المستخدمة في تطبيق تأثيرات التمويه على الرسوم ا...
Meta Keywords: filter, svg, على, stddeviation, عنصر
-->

# عنصر SVGFEGaussianBlurElement في JavaScript

## ملخص
يعتبر عنصر SVGFEGaussianBlurElement من عناصر SVG المستخدمة في تطبيق تأثيرات التمويه على الرسوم المتحركة والصور. يمكن استخدامه في JavaScript لتخصيص الرسوم البيانية بشكل ديناميكي.

## الوثائق
### الغرض
يستخدم عنصر SVGFEGaussianBlurElement لتطبيق تأثير تمويه Gaussian على العناصر الرسومية في SVG. يساعد هذا العنصر في تحسين المظهر البصري للرسوم المتحركة والإبداعات الفنية.

### الاستخدام
يمكن استخدام هذا العنصر ضمن عنصر `<filter>` داخل SVG، مما يسمح بتطبيق تأثيرات على الأشكال مثل الدوائر، والمستطيلات، والنصوص. يتم التحكم في مقدار التمويه بواسطة خاصية `stdDeviation`.

### التفاصيل
- **الخصائص الأساسية**:
  - `stdDeviation`: تحدد مقدار التمويه. يمكن أن تكون قيمة واحدة (لتمويه متساوي على كل الاتجاهات) أو قيمتين (لتمويه غير متساوي).
  - `in`: تحدد المدخلات التي سيتم تطبيق التأثير عليها.
  - `result`: تحدد اسم المخرج الذي يمكن استخدامه في عناصر أخرى ضمن نفس الفلتر.

- **الهيكل العام**:
```xml
<filter id="blur">
  <feGaussianBlur in="SourceGraphic" stdDeviation="5" />
</filter>
```

## أمثلة
### مثال 1: تطبيق تأثير تمويه بسيط
```html
<svg width="200" height="200">
  <defs>
    <filter id="blur">
      <feGaussianBlur in="SourceGraphic" stdDeviation="5" />
    </filter>
  </defs>
  <circle cx="100" cy="100" r="80" fill="blue" filter="url(#blur)" />
</svg>
```

### مثال 2: استخدام قيمة stdDeviation متعددة
```html
<svg width="200" height="200">
  <defs>
    <filter id="blur">
      <feGaussianBlur in="SourceGraphic" stdDeviation="5 10" />
    </filter>
  </defs>
  <rect x="20" y="20" width="160" height="160" fill="green" filter="url(#blur)" />
</svg>
```

## الشرح
### الأخطاء الشائعة
- **القيم غير الصحيحة**: يجب التأكد من أن القيم المستخدمة في `stdDeviation` صحيحة وغير سالبة.
- **عدم رؤية التأثير**: إذا لم يظهر التأثير، تأكد من أن العنصر الرسومي مرتبط بشكل صحيح بالفلتر.
- **تداخل الفلاتر**: عند استخدام أكثر من فلتر، تأكد من ترتيبها بشكل صحيح لضمان الأداء المطلوب.

### ملاحظات إضافية
- من الممكن دمج عنصر SVGFEGaussianBlurElement مع عناصر تأثير أخرى مثل `feColorMatrix` أو `feBlend` للحصول على تأثيرات أكثر تعقيدًا.
- يمكن أن يؤثر استخدام التمويه على أداء الرسوم المتحركة، لذا يُفضل استخدامه بحذر.

## ملخص جملة واحدة
يتيح عنصر SVGFEGaussianBlurElement في JavaScript تطبيق تأثيرات تمويه Gaussian ديناميكية على الرسوم المتحركة والصور في SVG.