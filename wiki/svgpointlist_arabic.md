<!--
Meta Description: # قائمة النقاط في SVG (SVGPointList) في JavaScript ## الملخص تُستخدم `SVGPointList` في JavaScript لإدارة مجموعة من النقاط داخل رسم SVG، مما يسهل العمل...
Meta Keywords: svg, النقاط, points, polyline, نقطة
-->

# قائمة النقاط في SVG (SVGPointList) في JavaScript

## الملخص
تُستخدم `SVGPointList` في JavaScript لإدارة مجموعة من النقاط داخل رسم SVG، مما يسهل العمل مع الرسومات المتجهة.

## الوثائق
### الغرض
`SVGPointList` هو كائن يُستخدم لتمثيل قائمة من النقاط (النقاط الثنائية الأبعاد) في مساحة رسم SVG. تُستخدم هذه النقاط في العديد من التطبيقات، مثل رسم الأشكال والمخططات.

### الاستخدام
يمكن إنشاء كائن `SVGPointList` باستخدام خاصية `points` لأشكال SVG مثل `polyline` و`polygon`. يوفر هذا الكائن واجهة للتعامل مع النقاط، بما في ذلك إضافة، حذف، والوصول إلى النقاط.

### التفاصيل
- **الخصائص**:
  - `numberOfItems`: عدد النقاط في القائمة.
  
- **الطرق**:
  - `appendItem()`: لإضافة نقطة جديدة إلى نهاية القائمة.
  - `clear()`: لمسح جميع النقاط في القائمة.
  - `getItem(index)`: للحصول على نقطة معينة من القائمة.
  - `insertItemBefore(newItem, index)`: لإضافة نقطة جديدة قبل نقطة معينة.
  - `removeItem(index)`: لحذف نقطة من القائمة.
  - `replaceItem(newItem, index)`: لاستبدال نقطة موجودة بأخرى جديدة.

## الأمثلة
### مثال 1: إنشاء قائمة نقاط وإضافة نقاط
```javascript
let svg = document.createElementNS("http://www.w3.org/2000/svg", "svg");
let polyline = document.createElementNS("http://www.w3.org/2000/svg", "polyline");
polyline.setAttribute("points", "0,0 100,100");
svg.appendChild(polyline);

let points = polyline.points;
let newPoint = svg.createSVGPoint();
newPoint.x = 150;
newPoint.y = 150;
points.appendItem(newPoint);

console.log(points.numberOfItems); // 3
```

### مثال 2: الوصول إلى نقطة معينة
```javascript
let firstPoint = polyline.points.getItem(0);
console.log(`X: ${firstPoint.x}, Y: ${firstPoint.y}`); // X: 0, Y: 0
```

## الشرح
من الأخطاء الشائعة عند العمل مع `SVGPointList` هو عدم الانتباه إلى إحداثيات النقاط. يجب التأكد من استخدام نظام الإحداثيات الصحيح. أيضًا، يجب التأكيد على أن أي تعديلات على القائمة لا تُحدث تغييرات مباشرة على عناصر الـ SVG في الصفحة حتى يتم تحديثها.

## ملخص بجملة واحدة
تُستخدم `SVGPointList` في JavaScript لإدارة قائمة من النقاط في رسومات SVG مما يسهل عمليات الرسم والتعديل.