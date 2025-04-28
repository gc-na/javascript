<!--
Meta Description: # SVGLengthList في JavaScript: دليل شامل ## ملخص تعد `SVGLengthList` نوعًا مهمًا في JavaScript يستخدم لإدارة مجموعة من القيم الطولية في SVG (Scalable ...
Meta Keywords: svglengthlist, svg, إلى, javascript, القائمة
-->

# SVGLengthList في JavaScript: دليل شامل

## ملخص
تعد `SVGLengthList` نوعًا مهمًا في JavaScript يستخدم لإدارة مجموعة من القيم الطولية في SVG (Scalable Vector Graphics). يوفر هذا النوع واجهة سهلة للتعامل مع الطول، مما يجعله أداة قوية للمطورين الذين يعملون على الرسومات المتجهة.

## الوثائق
### الغرض
`SVGLengthList` هو كائن يستخدم لتخزين قائمة من الطوليات (lengths) التي تُستخدم في عناصر SVG المختلفة. يمكن استخدامه لتحديد أبعاد الأشكال، مثل العرض والارتفاع، بطريقة ديناميكية.

### الاستخدام
يتم استخدام `SVGLengthList` عادةً مع خصائص معينة في عناصر SVG مثل `stroke-dasharray` و`pathLength`. يتيح لك هذا النوع إضافة، حذف، وتعديل الطوليات بسهولة.

### التفاصيل
- **الإنشاء**: يتم إنشاء كائن `SVGLengthList` بشكل تلقائي عند الحاجة إلى تخزين مجموعة من الطوليات في سياق SVG.
- **الخصائص**:
  - `numberOfItems`: تعيد عدد العناصر في القائمة.
  - `appendItem()`: تضيف عنصرًا جديدًا إلى القائمة.
  - `removeItem()`: تزيل عنصرًا من القائمة بناءً على الفهرس المحدد.
  - `getItem()`: تعيد العنصر الموجود في فهرس معين.
  - `clear()`: تزيل جميع العناصر من القائمة.

## الأمثلة
### مثال 1: إضافة طول إلى SVGLengthList
```javascript
// إنشاء عنصر SVG
let svgElement = document.createElementNS("http://www.w3.org/2000/svg", "svg");

// إنشاء SVGLengthList
let lengthList = svgElement.getTotalLength();

// إضافة طول
lengthList.appendItem(svgElement.createSVGLength());
```

### مثال 2: الحصول على طول معين
```javascript
// الحصول على الطول الأول من القائمة
let firstLength = lengthList.getItem(0);
console.log(firstLength.value); // طباعة قيمة الطول
```

### مثال 3: إزالة طول من القائمة
```javascript
// إزالة الطول الأول
lengthList.removeItem(0);
console.log(lengthList.numberOfItems); // طباعة عدد العناصر المتبقية
```

## الشرح
غالبًا ما يواجه المطورون بعض التحديات عند العمل مع `SVGLengthList`. من المهم الانتباه إلى أن محاولات الوصول إلى فهرس غير موجود ستؤدي إلى أخطاء. أيضًا، يجب التأكد من أن القيم المدخلة صحيحة، حيث أن إدخال قيم غير مناسبة قد يؤدي إلى سلوك غير متوقع في الرسومات.

## ملخص جملة واحدة
`SVGLengthList` هو نوع في JavaScript يُستخدم لتخزين وإدارة مجموعة من القيم الطولية في عناصر SVG بشكل فعال.