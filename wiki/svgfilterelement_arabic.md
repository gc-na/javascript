<!--
Meta Description: # عنصر SVGFilterElement في جافا سكريبت ## ملخص عنصر SVGFilterElement هو جزء من واجهة برمجة التطبيقات SVG في جافا سكريبت، ويستخدم لتطبيق تأثيرات الفلتر...
Meta Keywords: svg, الفلتر, filter, على, العناصر
-->

# عنصر SVGFilterElement في جافا سكريبت

## ملخص
عنصر SVGFilterElement هو جزء من واجهة برمجة التطبيقات SVG في جافا سكريبت، ويستخدم لتطبيق تأثيرات الفلترة على العناصر الرسومية في مستندات SVG.

## الوثائق
### الغرض
يستخدم عنصر SVGFilterElement لإنشاء تأثيرات بصرية مثل الظلال، التمويه، والسطوع على العناصر الرسومية داخل مستند SVG. يمكن أن تعمل الفلاتر على تحسين المظهر البصري للرسوم المتحركة والتصاميم.

### الاستخدام
يمكن استخدام SVGFilterElement عن طريق تعريف عنصر `<filter>` داخل مستند SVG، ثم تطبيق الفلتر على العناصر باستخدام سمة `filter`. يتم تعريف الفلاتر باستخدام مجموعة من العناصر الفرعية مثل `<feGaussianBlur>`, `<feColorMatrix>`, وغيرها.

### التفاصيل
- **الخصائص**:
  - `id`: معرف الفلتر، يجب أن يكون فريدًا ضمن مستند SVG.
  - `x`, `y`: تحديد موقع الفلتر.
  - `width`, `height`: تحديد أبعاد الفلتر.
  - `filterUnits`: تحديد وحدات الفلتر (userSpaceOnUse أو objectBoundingBox).
  
- **العناصر الفرعية**:
  - `<feGaussianBlur>`: لتطبيق تأثير تمويه Gaussian.
  - `<feOffset>`: لتحريك الفلتر.
  - `<feMerge>`: لدمج عدة تأثيرات.

## أمثلة

### مثال بسيط
```html
<svg width="200" height="200">
  <defs>
    <filter id="blurFilter">
      <feGaussianBlur in="SourceGraphic" stdDeviation="5" />
    </filter>
  </defs>
  <circle cx="100" cy="100" r="80" fill="blue" filter="url(#blurFilter)" />
</svg>
```

### مثال مع عناصر متعددة
```html
<svg width="200" height="200">
  <defs>
    <filter id="shadowFilter">
      <feGaussianBlur in="SourceAlpha" stdDeviation="3" result="blur" />
      <feOffset dx="2" dy="2" result="offsetBlur" />
      <feMerge>
        <feMergeNode />
        <feMergeNode in="offsetBlur" />
      </feMerge>
    </filter>
  </defs>
  <rect x="20" y="20" width="150" height="150" fill="red" filter="url(#shadowFilter)" />
</svg>
```

## الشرح
من الشائع أن يواجه المطورون مشاكل تتعلق بتعريف الفلاتر بشكل صحيح. على سبيل المثال، يجب ضمان أن يكون `id` الفلتر فريدًا. أيضًا، يجب أن تكون أبعاد الفلتر مناسبة لتجنب تداخلات غير مرغوب فيها مع العناصر الرسومية. بالإضافة إلى ذلك، قد تحتاج إلى ضبط `stdDeviation` في `feGaussianBlur` للحصول على التأثير المطلوب.

إذا تم تطبيق الفلتر بشكل غير صحيح، فقد لا تظهر التأثيرات أو تظهر بشكل غير متوقع. تأكد من استخدام أدوات المطور في المتصفح لتصحيح أي مشاكل محتملة.

## ملخص جملة واحدة
يعتبر عنصر SVGFilterElement في جافا سكريبت أداة قوية لإنشاء تأثيرات بصرية مخصصة على العناصر الرسومية داخل مستندات SVG.