<!--
Meta Description: # عنصر SVGMarkerElement في JavaScript: دليلك الشامل ## ملخص يتعلق عنصر SVGMarkerElement في JavaScript بتعريف العلامات (Markers) المستخدمة في رسومات SV...
Meta Keywords: marker, setattribute, svg, const, svgns
-->

# عنصر SVGMarkerElement في JavaScript: دليلك الشامل

## ملخص
يتعلق عنصر SVGMarkerElement في JavaScript بتعريف العلامات (Markers) المستخدمة في رسومات SVG، والتي تُستخدم لتحديد شكل النقاط أو الرموز على المسارات.

## الوثائق
### الغرض
يُستخدم SVGMarkerElement لإضافة علامات إلى المسارات في SVG، مما يتيح لك تحسين الرسومات بطرق متنوعة. يمكنك استخدام العلامات لتحديد شكل النقاط، مثل الأسهم أو الدوائر، التي تظهر في نهايات أو على طول المسار.

### الاستخدام
لإنشاء عنصر SVGMarkerElement، يمكن استخدام الكود التالي:

```javascript
const svgNS = "http://www.w3.org/2000/svg"; 
const marker = document.createElementNS(svgNS, "marker");
```

### التفاصيل
- **الخصائص**:
  - `id`: يحدد معرف العلامة.
  - `markerUnits`: يحدد كيفية قياس العلامة (مثل: "userSpaceOnUse" أو "strokeWidth").
  - `markerWidth`: يحدد عرض العلامة.
  - `markerHeight`: يحدد ارتفاع العلامة.
  - `refX` و `refY`: تحدد نقطة المرجع للعلامة بالنسبة للنقطة التي سيتم وضعها فيها.

- **طرق الاستخدام**:
  يتم ربط العلامات مع المسارات باستخدام خاصية `marker-start`, `marker-mid`, أو `marker-end` لتحديد مكان ظهور العلامة.

## الأمثلة
### مثال بسيط لإنشاء علامة
```javascript
const svgNS = "http://www.w3.org/2000/svg"; 
const svg = document.createElementNS(svgNS, "svg");
const marker = document.createElementNS(svgNS, "marker");

marker.setAttribute("id", "arrow");
marker.setAttribute("markerWidth", "10");
marker.setAttribute("markerHeight", "10");
marker.setAttribute("refX", "5");
marker.setAttribute("refY", "5");
marker.setAttribute("orient", "auto");

const path = document.createElementNS(svgNS, "path");
path.setAttribute("d", "M10 10 L50 50");
path.setAttribute("stroke", "black");
path.setAttribute("stroke-width", "2");
path.setAttribute("marker-end", "url(#arrow)");

svg.appendChild(marker);
svg.appendChild(path);
document.body.appendChild(svg);
```

### علامة مع شكل مخصص
```javascript
const circle = document.createElementNS(svgNS, "circle");
circle.setAttribute("cx", "5");
circle.setAttribute("cy", "5");
circle.setAttribute("r", "5");
circle.setAttribute("fill", "red");
marker.appendChild(circle);
```

## الشرح
### الفخاخ الشائعة والملاحظات
- تأكد من استخدام `createElementNS` بدلاً من `createElement` عند إنشاء عناصر SVG. 
- تحقق من أن لديك تعريف كامل للعلامة في الـ SVG قبل استخدامها، أو قد لا تظهر كما هو متوقع.
- يجب أن تكون الخصائص مثل `refX` و `refY` متناسبة مع أبعاد العلامة لضمان العرض الصحيح.

## ملخص جملة واحدة
يعد عنصر SVGMarkerElement أداة قوية في JavaScript لتخصيص العلامات في رسومات SVG، مما يعزز من جمالية ووضوح الرسومات.