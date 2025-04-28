<!--
Meta Description: # عنصر SVGPolylineElement في JavaScript: دليل شامل ## الملخص يعد عنصر SVGPolylineElement جزءًا من واجهة SVG في JavaScript، ويستخدم لرسم مضلعات متعددة ...
Meta Keywords: svg, svgpolylineelement, javascript, polyline, stroke
-->

# عنصر SVGPolylineElement في JavaScript: دليل شامل

## الملخص
يعد عنصر SVGPolylineElement جزءًا من واجهة SVG في JavaScript، ويستخدم لرسم مضلعات متعددة الخطوط على صفحات الويب.

## الوثائق
### الغرض
يستخدم SVGPolylineElement لإنشاء أشكال متعددة الخطوط (polylines) في مستندات SVG، مما يسمح للمطورين برسم أشكال معقدة تتكون من مجموعة من النقاط المتصلة.

### الاستخدام
يتم استخدام عنصر SVGPolylineElement من خلال واجهة SVG في JavaScript. يمكن إنشاؤه باستخدام الدالة `createElementNS`، أو يمكن إضافته مباشرة إلى مستند SVG باستخدام HTML.

### التفاصيل
- **الخصائص**:
  - `points`: خاصية تحتوي على مجموعة من النقاط التي تحدد شكل المضلع.
  - `fill`: تحدد لون التعبئة.
  - `stroke`: تحدد لون الحدود.
  - `stroke-width`: تحدد سمك الحدود.
  
- **الأحداث**: يدعم عنصر SVGPolylineElement الأحداث القياسية مثل `click` و`mouseover`.

## الأمثلة
### مثال أساسي على استخدام SVGPolylineElement
```html
<svg width="200" height="200">
  <polyline points="50,150 100,50 150,150" style="fill:none; stroke:black; stroke-width:2" />
</svg>
```

### مثال على استخدام JavaScript لإنشاء Polyline
```javascript
const svgNamespace = "http://www.w3.org/2000/svg";
const polyline = document.createElementNS(svgNamespace, "polyline");

polyline.setAttribute("points", "50,150 100,50 150,150");
polyline.setAttribute("style", "fill:none; stroke:black; stroke-width:2");

document.querySelector("svg").appendChild(polyline);
```

## الشرح
### نقاط يجب الانتباه إليها
- تأكد من استخدام نظام الأسماء الصحيح (`http://www.w3.org/2000/svg`) عند إنشاء عناصر SVG باستخدام JavaScript.
- قد لا تظهر المضلع إذا كانت النقاط غير صحيحة أو غير متصلة بشكل صحيح.
- تذكر أن القيم المستخدمة في خاصية `points` يجب أن تكون مفصولة بفواصل.

### ملاحظات إضافية
- يمكن استخدام CSS لتنسيق العنصر بشكل أكبر.
- تأكد من أن العنصر موجود داخل عنصر SVG للحصول على العرض الصحيح.

## ملخص من جملة واحدة
يعد SVGPolylineElement أداة قوية في JavaScript لرسم أشكال متعددة الخطوط باستخدام مستندات SVG.