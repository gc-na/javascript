<!--
Meta Description: # SVGRect في JavaScript: رسم مستطيلات باستخدام SVG ## ملخص SVGRect هو كائن في JavaScript يُستخدم لرسم المستطيلات داخل رسومات SVG (Scalable Vector Grap...
Meta Keywords: svg, svgrect, rect, المستطيل, setattribute
-->

# SVGRect في JavaScript: رسم مستطيلات باستخدام SVG

## ملخص
SVGRect هو كائن في JavaScript يُستخدم لرسم المستطيلات داخل رسومات SVG (Scalable Vector Graphics). يوفر هذا الكائن واجهة لتحديد حجم وموقع المستطيل بسهولة.

## الوثائق
### الغرض
يستخدم SVGRect لتحديد خصائص مستطيل في رسومات SVG، مما يسمح للمطورين بإنشاء أشكال هندسية بدقة.

### الاستخدام
يمكن استخدام SVGRect بعدة طرق، ولكن غالبًا ما يكون ذلك بالتعاون مع كائنات SVG مثل `<svg>` و`<rect>`. يتم إنشاء كائن SVGRect باستخدام دالة `createSVGRect()` الموجودة في كائن SVG.

### التفاصيل
- **الخصائص الأساسية**:
  - `x`: إحداثيات المحور السيني لزاوية المستطيل العليا اليسرى.
  - `y`: إحداثيات المحور الصادي لزاوية المستطيل العليا اليسرى.
  - `width`: عرض المستطيل.
  - `height`: ارتفاع المستطيل.

- **مثال على الاستخدام**:
  لإنشاء مستطيل باستخدام SVGRect، يجب أولاً إنشاء عنصر SVG ثم استخدام كائن SVGRect لتحديد خصائص المستطيل.

## الأمثلة
### مثال 1: إنشاء مستطيل بسيط
```javascript
// إنشاء عنصر SVG
const svgNamespace = "http://www.w3.org/2000/svg";
const svg = document.createElementNS(svgNamespace, "svg");
svg.setAttribute("width", "200");
svg.setAttribute("height", "200");
document.body.appendChild(svg);

// إنشاء مستطيل باستخدام SVGRect
const rect = document.createElementNS(svgNamespace, "rect");
rect.setAttribute("x", "10");
rect.setAttribute("y", "10");
rect.setAttribute("width", "100");
rect.setAttribute("height", "50");
rect.setAttribute("fill", "blue");

// إضافة المستطيل إلى عنصر SVG
svg.appendChild(rect);
```

### مثال 2: تعديل خصائص المستطيل
```javascript
// تعديل خصائص المستطيل
rect.setAttribute("width", "150");
rect.setAttribute("fill", "red");
```

## الشرح
### الأخطاء الشائعة
- **عدم تحديد مساحة SVG**: تأكد من أن لديك مساحة SVG محددة قبل محاولة إضافة مستطيل.
- **تجاهل تنسيق الأبعاد**: تأكد من أن القيم المستخدمة في `width` و`height` صحيحة ومناسبة لتجنب الأخطاء في العرض.
- **استعمال إحداثيات سلبية**: قد يؤدي استخدام إحداثيات سلبية لـ `x` و `y` إلى عدم ظهور المستطيل في مساحة العرض المحددة.

### ملاحظات إضافية
- يمكن استخدام SVGRect مع أنماط CSS لتخصيص المظهر بشكل أكبر.
- SVGRect يدعم الرسوم المتحركة والتفاعلية، مما يجعله خيارًا مثاليًا للتطبيقات التفاعلية.

## ملخص جملة واحدة
SVGRect هو كائن في JavaScript يُستخدم لرسم المستطيلات بدقة داخل رسومات SVG، مما يوفر أدوات قوية لإنشاء أشكال هندسية.