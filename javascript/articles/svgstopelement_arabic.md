<!--
Meta Description: # عنصر SVGStopElement في جافا سكريبت: دليل شامل ## ملخص عنصر SVGStopElement هو جزء من واجهة برمجة التطبيقات SVG (Scalable Vector Graphics) في جافا سكر...
Meta Keywords: stop, svg, color, offset, 100
-->

# عنصر SVGStopElement في جافا سكريبت: دليل شامل

## ملخص
عنصر SVGStopElement هو جزء من واجهة برمجة التطبيقات SVG (Scalable Vector Graphics) في جافا سكريبت، حيث يمثل نقطة توقف في تدرج الألوان. يُستخدم هذا العنصر بشكل شائع لتعريف الألوان عند نقاط معينة داخل تدرجات الألوان.

## الوثائق
### الغرض
يُستخدم عنصر SVGStopElement لتحديد الألوان عند نقاط معينة في تدرج لوني داخل رسم SVG. يُعتبر هذا العنصر جزءًا أساسيًا من عناصر تدرجات SVG، مثل `<linearGradient>` و`<radialGradient>`.

### الاستخدام
يتم تعريف عنصر SVGStopElement داخل عناصر تدرج الألوان. يتطلب هذا العنصر قيمتين رئيسيتين:
- **stop-color**: تحدد لون التوقف عند النقطة المحددة.
- **offset**: تحدد موضع التوقف في التدرج، ويجب أن تكون قيمة رقمية بين 0% و100%.

#### التركيب
```html
<svg>
    <defs>
        <linearGradient id="gradientExample">
            <stop offset="0%" stop-color="red" />
            <stop offset="100%" stop-color="blue" />
        </linearGradient>
    </defs>
    <rect width="100" height="100" fill="url(#gradientExample)" />
</svg>
```

## الأمثلة
### مثال 1: تدرج لوني بسيط
```html
<svg width="200" height="100">
    <defs>
        <linearGradient id="simpleGradient">
            <stop offset="0%" stop-color="yellow"/>
            <stop offset="100%" stop-color="orange"/>
        </linearGradient>
    </defs>
    <rect width="200" height="100" fill="url(#simpleGradient)" />
</svg>
```

### مثال 2: تدرج مع عدة نقاط توقف
```html
<svg width="200" height="100">
    <defs>
        <linearGradient id="multiStopGradient">
            <stop offset="0%" stop-color="green"/>
            <stop offset="50%" stop-color="blue"/>
            <stop offset="100%" stop-color="purple"/>
        </linearGradient>
    </defs>
    <rect width="200" height="100" fill="url(#multiStopGradient)" />
</svg>
```

## الشرح
### المشاكل الشائعة
- **عدم وضوح الألوان**: تأكد من أن القيم المستخدمة في `stop-color` صحيحة ومطابقة لألوان CSS.
- **تحديد الإزاحة**: يجب أن تكون قيمة `offset` نسبة مئوية صحيحة، وإلا قد يؤدي ذلك إلى عدم ظهور اللون كما هو متوقع.
- **تداخل العناصر**: تأكد من أن تعريفات التدرجات داخل `<defs>` وأنها متصلة بشكل صحيح بالعناصر التي تستخدمها.

## ملخص جملة واحدة
عنصر SVGStopElement هو عنصر أساسي في SVG يُستخدم لتحديد الألوان عند نقاط معينة في تدرجات الألوان، مما يساعد في إنشاء تصاميم رسومية غنية وتفاعلية.