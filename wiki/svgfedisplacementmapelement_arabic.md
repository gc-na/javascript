<!--
Meta Description: # عنصر SVGFEDisplacementMapElement في JavaScript ## ملخص يُعتبر عنصر SVGFEDisplacementMapElement جزءًا من واجهة برمجة التطبيقات SVG في JavaScript، ويُ...
Meta Keywords: svg, filter, svgfedisplacementmapelement, تأثيرات, على
-->

# عنصر SVGFEDisplacementMapElement في JavaScript

## ملخص
يُعتبر عنصر SVGFEDisplacementMapElement جزءًا من واجهة برمجة التطبيقات SVG في JavaScript، ويُستخدم لتطبيق تأثيرات التحويل على الرسومات المتجهة باستخدام خريطة إزاحة.

## الوثائق
### الهدف
يهدف SVGFEDisplacementMapElement إلى تعديل تأثيرات الصورة عبر تطبيق خريطة إزاحة. يمكن استخدامه لإنشاء تأثيرات بصرية مذهلة في الرسوم المتجهة، مثل تشويه الصور أو خلق تأثيرات ثلاثية الأبعاد.

### الاستخدام
يمكن استخدام SVGFEDisplacementMapElement ضمن عناصر SVG لتطبيق تأثيرات على الأشكال. يتم استخدامه بشكل خاص مع عناصر مثل `<filter>` و`<feImage>`.

### التفاصيل
- **الخصائص**:
  - `in1`: يُحدد مصدر الإدخال الأول.
  - `in2`: يُحدد مصدر الإدخال الثاني، عادةً ما يكون صورة تستخدم كخريطة إزاحة.
  - `scale`: يُحدد مقدار الإزاحة.
  - `xChannelSelector`: يُحدد قناة اللون المستخدمة في الإزاحة على المحور السيني.
  - `yChannelSelector`: يُحدد قناة اللون المستخدمة في الإزاحة على المحور الصادي.

- **الصيغة**:
```xml
<feDisplacementMap in="SourceGraphic" in2="displacementMap" scale="30" xChannelSelector="R" yChannelSelector="G" />
```

## الأمثلة
### مثال 1: تطبيق خريطة إزاحة بسيطة
```html
<svg width="400" height="200">
    <defs>
        <filter id="displacementFilter">
            <feImage xlink:href="map.png" result="displacementMap" />
            <feDisplacementMap in="SourceGraphic" in2="displacementMap" scale="30" />
        </filter>
    </defs>
    <rect width="100%" height="100%" fill="lightblue" filter="url(#displacementFilter)" />
</svg>
```

### مثال 2: استخدام قنوات الألوان
```html
<svg width="400" height="200">
    <defs>
        <filter id="displacementFilter">
            <feImage xlink:href="map.png" result="displacementMap" />
            <feDisplacementMap in="SourceGraphic" in2="displacementMap" scale="20" xChannelSelector="R" yChannelSelector="B" />
        </filter>
    </defs>
    <circle cx="200" cy="100" r="80" fill="red" filter="url(#displacementFilter)" />
</svg>
```

## الشرح
قد يواجه المطورون بعض التحديات عند استخدام SVGFEDisplacementMapElement:
- **تحديد مصادر الإدخال**: تأكد من أن مصادر الإدخال صحيحة ومتاحة.
- **تحديد الإزاحة**: قد تؤدي القيم المرتفعة في `scale` إلى تشويهات غير مرغوب فيها.
- **قنوات الألوان**: قم بالتأكد من اختيار القنوات الصحيحة، حيث يمكن أن تؤثر على النتائج بشكل كبير.

## ملخص جملة واحدة
SVGFEDisplacementMapElement هو عنصر SVG يستخدم في JavaScript لتطبيق تأثيرات الإزاحة على الأشكال باستخدام خرائط الإزاحة.