<!--
Meta Description: # عنصر SVGFEDistantLightElement في JavaScript: دليل شامل ## ملخص يعتبر عنصر SVGFEDistantLightElement جزءًا من واجهة برمجة التطبيقات SVG في JavaScript،...
Meta Keywords: fediffuselighting, svg, عنصر, azimuth, elevation
-->

# عنصر SVGFEDistantLightElement في JavaScript: دليل شامل

## ملخص
يعتبر عنصر SVGFEDistantLightElement جزءًا من واجهة برمجة التطبيقات SVG في JavaScript، ويستخدم لتحديد مصدر ضوء بعيد في رسومات SVG، مما يتيح تأثيرات إضاءة واقعية.

## الوثائق
### الغرض
يستخدم عنصر SVGFEDistantLightElement لتحديد اتجاه مصدر الضوء في تأثيرات الإضاءة في رسومات SVG. يمكن استخدامه مع عناصر الفلتر مثل <feDiffuseLighting> لتطبيق تأثيرات الإضاءة على الأشكال.

### الاستخدام
يمكن استخدام SVGFEDistantLightElement داخل عنصر <feDiffuseLighting> لتحديد اتجاه الضوء. يتطلب تحديد الموقع بواسطة السمات `azimuth` و `elevation`، حيث يعبر `azimuth` عن الاتجاه الأفقي و `elevation` عن الزاوية الرأسية.

### التفاصيل
- **السمات**:
  - `azimuth`: زاوية الاتجاه الأفقي للضوء (بالدرجات).
  - `elevation`: زاوية الاتجاه الرأسي للضوء (بالدرجات).
  
- **الهيكل**:
```xml
<feDiffuseLighting in="SourceGraphic" surfaceScale="1">
  <feDistantLight azimuth="45" elevation="30"/>
</feDiffuseLighting>
```

## الأمثلة
### مثال 1: تأثير الإضاءة البسيط
```html
<svg width="200" height="200">
  <defs>
    <filter id="lighting">
      <feDiffuseLighting in="SourceGraphic" surfaceScale="1">
        <feDistantLight azimuth="45" elevation="30"/>
      </feDiffuseLighting>
    </filter>
  </defs>
  <rect width="100%" height="100%" fill="lightblue" filter="url(#lighting)"/>
</svg>
```

### مثال 2: استخدام زوايا مختلفة
```html
<svg width="200" height="200">
  <defs>
    <filter id="lighting">
      <feDiffuseLighting in="SourceGraphic" surfaceScale="1">
        <feDistantLight azimuth="90" elevation="60"/>
      </feDiffuseLighting>
    </filter>
  </defs>
  <circle cx="100" cy="100" r="80" fill="orange" filter="url(#lighting)"/>
</svg>
```

## الشرح
### الأخطاء الشائعة
- **تحديد الزوايا بشكل غير صحيح**: التأكد من استخدام الزوايا الصحيحة لـ `azimuth` و `elevation` لتحقيق التأثير المطلوب. الزوايا يجب أن تكون بين 0 و 360 درجة.
- **عدم استخدام الفلتر**: يجب أن يكون عنصر SVGFEDistantLightElement داخل عنصر <feDiffuseLighting> لكي يعمل بشكل صحيح.
- **تجربة القيم المختلفة**: قد يؤدي استخدام القيم الافتراضية إلى نتائج غير مرضية، لذا من المهم التجربة.

## ملخص جملة واحدة
يتيح عنصر SVGFEDistantLightElement في JavaScript تحديد مصدر ضوء بعيد لتحسين التأثيرات الضوئية في رسومات SVG.