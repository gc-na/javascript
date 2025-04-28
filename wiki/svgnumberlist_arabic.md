<!--
Meta Description: # قائمة الأعداد في SVG (SVGNumberList) في JavaScript ## ملخص تُستخدم قائمة الأعداد في SVG (SVGNumberList) لتخزين مجموعة من القيم العددية التي تُستخدم ...
Meta Keywords: svg, svgnumberlist, widthlist, عدد, الأعداد
-->

# قائمة الأعداد في SVG (SVGNumberList) في JavaScript

## ملخص
تُستخدم قائمة الأعداد في SVG (SVGNumberList) لتخزين مجموعة من القيم العددية التي تُستخدم غالبًا في خصائص SVG، مثل الأبعاد أو الإحداثيات. تتيح هذه القائمة التعامل مع الأعداد بطريقة منظمة وسهلة.

## الوثائق
### الغرض
تُستخدم `SVGNumberList` لتمثيل مجموعة من الأعداد التي تُستخدم في عناصر SVG. تُعتبر هذه القائمة مفيدة عند الحاجة لتخزين أعداد متكررة مثل الأبعاد في الرسوم البيانية أو الإحداثيات في الأشكال.

### الاستخدام
تُستخدم `SVGNumberList` كجزء من واجهة برمجة التطبيقات (API) الخاصة بـ SVG في JavaScript. يمكن الوصول إليها من خلال خاصية `numberList` لعناصر مثل `SVGAnimatedLength`.

### التفاصيل
- **إنشاء قائمة أعداد جديدة**: لا يمكن إنشاء `SVGNumberList` مباشرةً باستخدام الباني. بدلاً من ذلك، يتم الحصول عليها من عناصر SVG الموجودة.
- **الخصائص**:
  - `length`: تُرجع عدد العناصر في القائمة.
  - `appendItem()`: تُضيف عددًا جديدًا إلى النهاية.
  - `removeItem()`: تُزيل عددًا من القائمة وفقًا للفهرس المحدد.
  - `getItem()`: تُرجع العدد الموجود في الفهرس المحدد.
  - `replaceItem()`: تُستبدل قيمة العدد في الفهرس المحدد.

## الأمثلة
### مثال 1: إنشاء SVGNumberList
```javascript
let svgElement = document.createElementNS("http://www.w3.org/2000/svg", "circle");
let radiusList = svgElement.r.baseVal;

// إضافة عدد إلى القائمة
radiusList.appendItem(50);
console.log(radiusList.getItem(0).value); // 50
```

### مثال 2: تعديل عناصر SVGNumberList
```javascript
let svgElement = document.createElementNS("http://www.w3.org/2000/svg", "rect");
let widthList = svgElement.width.baseVal;

// إضافة أعداد جديدة
widthList.appendItem(100);
widthList.appendItem(200);
console.log(widthList.length); // 2

// استبدال عدد
widthList.replaceItem(150, 0);
console.log(widthList.getItem(0).value); // 150

// إزالة عدد
widthList.removeItem(1);
console.log(widthList.length); // 1
```

## الشرح
### الأخطاء الشائعة
- **عدم وجود دعم في المتصفحات**: تأكد من أن المتصفح يدعم `SVGNumberList`، حيث أن بعض المتصفحات القديمة قد لا توفر دعمًا كاملًا لخصائص SVG.
- **فهم الفهارس**: تذكر أن الفهارس تبدأ من 0، لذا يجب توخي الحذر عند تحديد الفهرس في الوظائف مثل `getItem()` أو `removeItem()`.

### ملاحظات إضافية
- تعتبر `SVGNumberList` مفيدة عند العمل مع الرسوم المتحركة أو الرسوم البيانية الديناميكية، حيث يمكن تعديل القيم العددية بسهولة في الوقت الحقيقي.
- تجنب إنشاء `SVGNumberList` بشكل غير ضروري لتفادي استهلاك الموارد.

## ملخص من جملة واحدة
قائمة الأعداد في SVG (SVGNumberList) في JavaScript توفر وسيلة فعالة لتخزين وإدارة مجموعة من القيم العددية المستخدمة في عناصر SVG.