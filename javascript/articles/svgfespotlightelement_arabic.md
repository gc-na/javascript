<!--
Meta Description: # عنصر SVGFESpotLightElement في JavaScript: دليل شامل ## ملخص يعد عنصر SVGFESpotLightElement جزءًا من واجهة برمجة التطبيقات لـ SVG في JavaScript، ويست...
Meta Keywords: الضوء, على, svg, filter, تحدد
-->

# عنصر SVGFESpotLightElement في JavaScript: دليل شامل

## ملخص
يعد عنصر SVGFESpotLightElement جزءًا من واجهة برمجة التطبيقات لـ SVG في JavaScript، ويستخدم لإنشاء تأثيرات الإضاءة البؤرية في الرسوميات المتجهة.

## الوثائق
### الغرض
يستخدم عنصر SVGFESpotLightElement لتحديد مصدر الضوء البؤري في الرسوميات المتجهة. يمكن استخدامه لإضافة تأثيرات ضوئية واقعية على الأشكال الرسومية، مما يعزز من جاذبيتها البصرية.

### الاستخدام
يتم استخدام SVGFESpotLightElement عادةً داخل عناصر `<filter>` في SVG. يتم تعريف خصائص الضوء مثل الموقع والاتجاه واللون والشفافية من خلال سمات مختلفة.

### التفاصيل
- **السمات الأساسية:**
  - `x`: تحدد موضع مصدر الضوء على المحور السيني.
  - `y`: تحدد موضع مصدر الضوء على المحور الصادي.
  - `z`: تحدد موضع مصدر الضوء على المحور الزد.
  - `pointsAtX`: تحدد موقع النقطة التي يستهدفها الضوء على المحور السيني.
  - `pointsAtY`: تحدد موقع النقطة التي يستهدفها الضوء على المحور الصادي.
  - `pointsAtZ`: تحدد موقع النقطة التي يستهدفها الضوء على المحور الزد.
  - `specularExponent`: تحدد شدة اللمعان الناتج عن الضوء.
  - `limitingConeAngle`: تحدد زاوية مخروط الضوء.

## أمثلة
### مثال 1: استخدام SVGFESpotLightElement داخل عنصر `<filter>`
```html
<svg width="200" height="200">
  <defs>
    <filter id="light">
      <feSpotLight x="100" y="100" z="100" pointsAtX="100" pointsAtY="100" specularExponent="20" limitingConeAngle="30" />
    </filter>
  </defs>
  <circle cx="100" cy="100" r="40" fill="blue" filter="url(#light)" />
</svg>
```

### مثال 2: تعديل خصائص الضوء
```html
<svg width="300" height="300">
  <defs>
    <filter id="spotlight">
      <feSpotLight x="150" y="150" z="200" pointsAtX="150" pointsAtY="150" specularExponent="10" limitingConeAngle="45" />
    </filter>
  </defs>
  <rect x="50" y="50" width="200" height="200" fill="red" filter="url(#spotlight)" />
</svg>
```

## الشرح
### العثرات الشائعة
- **عدم رؤية تأثير الضوء:** تأكد من تحديد خصائص الضوء بشكل صحيح، مثل موضعه وزاويته. إذا كان الضوء بعيدًا جدًا أو موجهًا بعيدًا عن الهدف، فلن يتم رؤية التأثير.
- **خصائص غير صحيحة:** تأكد من استخدام القيم الصحيحة للسمات مثل `specularExponent` و `limitingConeAngle`، حيث يمكن أن تؤثر هذه القيم على المظهر النهائي.

### ملاحظات إضافية
- يمكن دمج SVGFESpotLightElement مع عناصر SVG الأخرى مثل `feDiffuseLighting` لتحقيق تأثيرات ضوئية معقدة.
- قد تختلف نتائج التأثيرات الضوئية بناءً على متصفح الويب المستخدم، لذا يُفضل اختبار الرسوميات عبر متصفحات متعددة.

## ملخص جملة واحدة
SVGFESpotLightElement هو عنصر SVG يستخدم في JavaScript لإنشاء تأثيرات إضاءة بؤرية ديناميكية تعزز من جاذبية الرسوميات المتجهة.