<!--
Meta Description: # عنصر SVGRadialGradientElement في JavaScript: دليل شامل ## ملخص يعتبر SVGRadialGradientElement عنصرًا مهمًا في SVG (Scalable Vector Graphics) يُستخدم...
Meta Keywords: stop, svg, setattribute, radialgradient, التدرج
-->

# عنصر SVGRadialGradientElement في JavaScript: دليل شامل

## ملخص
يعتبر SVGRadialGradientElement عنصرًا مهمًا في SVG (Scalable Vector Graphics) يُستخدم لإنشاء تدرجات شعاعية في الرسومات. يتيح لك هذا العنصر تحديد تأثيرات تدرج متعددة الألوان بشكل مرن.

## الوثائق
### الغرض
SVGRadialGradientElement يُستخدم لتحديد تدرجات شعاعية في الرسومات المتجهة القابلة للتغيير. يمكن استخدامه لتزيين الأشكال مثل الدوائر والمربعات، مما يضيف عمقًا وجمالية إلى التصميمات.

### الاستخدام
يتم إنشاء عنصر SVGRadialGradientElement داخل عنصر `<defs>` في SVG. يمكن تحديد خصائص متعددة مثل:
- **cx**: مركز التدرج على المحور X.
- **cy**: مركز التدرج على المحور Y.
- **r**: نصف قطر التدرج.
- **fx**: مركز التدرج المضيء على المحور X.
- **fy**: مركز التدرج المضيء على المحور Y.

### التفاصيل
يتم استخدام SVGRadialGradientElement لتوفير تأثيرات تدرج شعاعية، مما يعني أن الألوان تتدرج من نقطة مركزية إلى الخارج. يمكن دمج SVGRadialGradientElement مع عناصر SVG الأخرى مثل `<circle>` أو `<rect>` لتطبيق التدرج عليها.

```javascript
const svgNamespace = "http://www.w3.org/2000/svg";

// إنشاء عنصر SVG 
const svg = document.createElementNS(svgNamespace, "svg");
svg.setAttribute("width", "200");
svg.setAttribute("height", "200");

// إنشاء تدرج شعاعي
const radialGradient = document.createElementNS(svgNamespace, "radialGradient");
radialGradient.setAttribute("id", "myGradient");
radialGradient.setAttribute("cx", "50%");
radialGradient.setAttribute("cy", "50%");
radialGradient.setAttribute("r", "50%");

// إضافة الألوان إلى التدرج
const stop1 = document.createElementNS(svgNamespace, "stop");
stop1.setAttribute("offset", "0%");
stop1.setAttribute("stop-color", "yellow");

const stop2 = document.createElementNS(svgNamespace, "stop");
stop2.setAttribute("offset", "100%");
stop2.setAttribute("stop-color", "red");

radialGradient.appendChild(stop1);
radialGradient.appendChild(stop2);
svg.appendChild(radialGradient);

// إنشاء دائرة باستخدام التدرج
const circle = document.createElementNS(svgNamespace, "circle");
circle.setAttribute("cx", "100");
circle.setAttribute("cy", "100");
circle.setAttribute("r", "80");
circle.setAttribute("fill", "url(#myGradient)");

svg.appendChild(circle);
document.body.appendChild(svg);
```

## الأمثلة
### مثال 1: تدرج شعاعي بسيط
```javascript
<svg width="200" height="200">
  <defs>
    <radialGradient id="grad1" cx="50%" cy="50%" r="50%">
      <stop offset="0%" style="stop-color:blue; stop-opacity:1" />
      <stop offset="100%" style="stop-color:white; stop-opacity:1" />
    </radialGradient>
  </defs>
  <circle cx="100" cy="100" r="80" fill="url(#grad1)" />
</svg>
```

### مثال 2: تدرج شعاعي متعدد الألوان
```javascript
<svg width="200" height="200">
  <defs>
    <radialGradient id="grad2" cx="50%" cy="50%" r="50%">
      <stop offset="0%" style="stop-color:red; stop-opacity:1" />
      <stop offset="50%" style="stop-color:green; stop-opacity:1" />
      <stop offset="100%" style="stop-color:blue; stop-opacity:1" />
    </radialGradient>
  </defs>
  <rect width="200" height="200" fill="url(#grad2)" />
</svg>
```

## الشرح
### الأخطاء الشائعة
- **عدم تحديد مركز التدرج**: تأكد من تعيين `cx` و `cy` بشكل صحيح، حيث يؤدي عدم ذلك إلى تدرج غير متوقع.
- **عدم استخدام `url(#gradientId)`**: يجب استخدام صيغة `url(#id)` عند تعيين اللون للتدرج.

### ملاحظات إضافية
- يعزز استخدام التدرجات الشعاعية من جمالية الرسومات، لكن يجب استخدامها بحذر لتجنب تشويش التصميم.
- يمكن استخدام `SVGFilters` مع SVGRadialGradientElement للحصول على تأثيرات إضافية.

## ملخص جملة واحدة
SVGRadialGradientElement هو عنصر SVG يستخدم لإنشاء تدرجات شعاعية، مما يضيف تأثيرات جمالية للرسومات في JavaScript.