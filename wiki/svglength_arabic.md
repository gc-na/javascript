<!--
Meta Description: # SVGLength في JavaScript: فهم واستخدام ## الملخص تعتبر خاصية SVGLength جزءًا أساسيًا من واجهة برمجة تطبيقات الرسوميات المتجهة القابلة للتوسع (SVG) في...
Meta Keywords: svglength, svg, javascript, على, تعيين
-->

# SVGLength في JavaScript: فهم واستخدام

## الملخص
تعتبر خاصية SVGLength جزءًا أساسيًا من واجهة برمجة تطبيقات الرسوميات المتجهة القابلة للتوسع (SVG) في JavaScript، حيث توفر طريقة للتعامل مع الأطوال في وحدات مختلفة مثل البكسل أو النسبة المئوية.

## الوثائق
### الغرض
تستخدم خاصية SVGLength لتمثيل قيمة طولية في SVG. يمكن أن تكون هذه القيم ذات وحدات مختلفة، مما يجعلها مفيدة في تصميم الرسوميات المتجهة وتعديلها بشكل ديناميكي باستخدام JavaScript.

### الاستخدام
تتضمن واجهة SVGLength عدة خصائص وطرق تتيح لك العمل مع الأطوال، مثل:
- `value`: للحصول على أو تعيين القيمة الرقمية للطول.
- `unitType`: للحصول على نوع الوحدة المستخدمة (مثل `SVG_LENGTHTYPE_UNKNOWN`, `SVG_LENGTHTYPE_NUMBER`, `SVG_LENGTHTYPE_PERCENTAGE`).
- `valueInSpecifiedUnits`: للحصول على القيمة في الوحدات المحددة.
- `convertToSpecifiedUnits()`: لتحويل القيمة إلى وحدة معينة.

### التفاصيل
عند استخدام SVGLength، يمكنك تحديد وحدات الطول كالتالي:
- **البكسل**: الوحدة الافتراضية.
- **النسبة المئوية**: تستخدم لتحديد الأطوال بالنسبة للأبعاد الأخرى في SVG.

## الأمثلة
### مثال 1: إنشاء عنصر SVG وتعيين طول
```javascript
let svgElement = document.createElementNS("http://www.w3.org/2000/svg", "rect");
let length = svgElement.width.baseVal; // الحصول على خاصية SVGLength
length.value = 100; // تعيين القيمة إلى 100 بكسل
```

### مثال 2: تحويل وحدة الطول
```javascript
let svgElement = document.createElementNS("http://www.w3.org/2000/svg", "line");
let length = svgElement.x1.baseVal;
length.value = 50; // تعيين القيمة
length.convertToSpecifiedUnits(SVGLength.SVG_LENGTHTYPE_PERCENTAGE); // تحويل إلى النسبة المئوية
```

## الشرح
### العوائق الشائعة
- **عدم فهم وحدات الطول**: قد يخلط المطورون بين الوحدات المستخدمة، مما يؤدي إلى نتائج غير صحيحة.
- **تعيين القيم بدون تحويل**: يجب أن تكون حذرًا عند تعيين القيم، خاصة إذا كنت تعمل على تحويلها بين الوحدات.

### ملاحظات إضافية
- تأكد من استخدام `createElementNS` عند إنشاء عناصر SVG في JavaScript لضمان التوافق.
- يمكن أن تكون بعض الخصائص غير متاحة في سياقات معينة، لذا يجب التحقق من وجودها قبل الاستخدام.

## ملخص بجملة واحدة
تعد خاصية SVGLength في JavaScript وسيلة قوية للتعامل مع الأطوال في SVG، مما يسهل تصميم وتعديل الرسوميات المتجهة.