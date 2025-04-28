<!--
Meta Description: # SVGTransform في JavaScript: فهم التحويلات في الرسوم المتجهة ## ملخص تحويلات SVG (SVGTransform) تعد جزءًا أساسيًا من التعامل مع الرسوم المتجهة في Jav...
Meta Keywords: svg, rect, svgtransform, javascript, على
-->

# SVGTransform في JavaScript: فهم التحويلات في الرسوم المتجهة

## ملخص
تحويلات SVG (SVGTransform) تعد جزءًا أساسيًا من التعامل مع الرسوم المتجهة في JavaScript، حيث تسمح بتعديل موقع، حجم، وزاوية العناصر المتجهة بشكل ديناميكي.

## الوثائق
**الغرض**: 
تستخدم SVGTransform لتطبيق التحويلات مثل الترجمة، التدوير، والتكبير على العناصر داخل وثيقة SVG. يمكن استخدامها لتعديل شكل العناصر بطريقة تفاعلية.

**الاستخدام**:
يمكن الوصول إلى كائنات SVGTransform من خلال واجهة البرمجة الخاصة بـ SVG. يتضمن ذلك إنشاء كائن SVGTransform جديد أو تعديل تحويلات موجودة.

### خصائص التحويل:
- **translate(tx, ty)**: لنقل العنصر بمقدار محدد في اتجاه المحور السيني والمحور الصادي.
- **rotate(angle, cx, cy)**: لتدوير العنصر حول نقطة معينة.
- **scale(sx, sy)**: لتغيير حجم العنصر.
- **skewX(angle)** و **skewY(angle)**: لتشويه العنصر في الاتجاهات الأفقية والعمودية.

### الاستخدام:
```javascript
// إنشاء عنصر SVG
let svg = document.createElementNS("http://www.w3.org/2000/svg", "svg");
let rect = document.createElementNS("http://www.w3.org/2000/svg", "rect");
rect.setAttribute("width", "100");
rect.setAttribute("height", "100");
rect.setAttribute("fill", "blue");
svg.appendChild(rect);
document.body.appendChild(svg);

// تطبيق تحويل
let transform = svg.createSVGTransform();
transform.setTranslate(50, 50);
rect.transform.baseVal.appendItem(transform);
```

## الأمثلة
### مثال 1: تطبيق الترجمة
```javascript
// نقل مستطيل بمقدار 30 وحدة على المحور السيني و20 وحدة على المحور الصادي
let translateTransform = svg.createSVGTransform();
translateTransform.setTranslate(30, 20);
rect.transform.baseVal.appendItem(translateTransform);
```

### مثال 2: تطبيق التدوير
```javascript
// تدوير المستطيل بزاوية 45 درجة حول نقطة المركز
let rotateTransform = svg.createSVGTransform();
rotateTransform.setRotate(45, 50, 50); // 50, 50 هي نقطة التدوير
rect.transform.baseVal.appendItem(rotateTransform);
```

### مثال 3: تطبيق التكبير
```javascript
// تكبير المستطيل بمقدار 2 على كلا المحورين
let scaleTransform = svg.createSVGTransform();
scaleTransform.setScale(2, 2);
rect.transform.baseVal.appendItem(scaleTransform);
```

## الشرح
عند استخدام SVGTransform، يجب الانتباه إلى بعض الأمور الشائعة:
- **السلسلة**: يمكن تطبيق عدة تحويلات على نفس العنصر، لكن يجب أن تكون مرتبة بشكل صحيح لأن كل تحويل يؤثر على التحويلات التي تليه.
- **توافق المتصفح**: تأكد من أن المتصفح يدعم SVG وواجهة SVGTransform، خاصةً عند العمل مع ميزات جديدة أو غير مدعومة.
- **الأداء**: التحويلات المعقدة قد تؤثر على أداء الرسوم المتجهة، لذا يُفضل استخدام التحويلات البسيطة عند الإمكان.

## ملخص بسيط
SVGTransform في JavaScript يتيح لك تطبيق وتحويل العناصر الرسومية بشكل ديناميكي وفعال.