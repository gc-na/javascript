<!--
Meta Description: # SVGAnimatedInteger في JavaScript: كل ما تحتاج معرفته ## ملخص تُعتبر خاصية `SVGAnimatedInteger` جزءًا من واجهة SVG في JavaScript، وتستخدم لتمثيل الأع...
Meta Keywords: svg, rect, baseval, width, svganimatedinteger
-->

# SVGAnimatedInteger في JavaScript: كل ما تحتاج معرفته

## ملخص
تُعتبر خاصية `SVGAnimatedInteger` جزءًا من واجهة SVG في JavaScript، وتستخدم لتمثيل الأعداد الصحيحة التي يمكن أن تتغير بمرور الوقت في عناصر SVG.

## الوثائق
تُستخدم `SVGAnimatedInteger` بشكل رئيسي في SVG (Scalable Vector Graphics) لتمثيل القيم العددية التي يمكن أن تتغير. هذه الخصائص تتكون من قيمتين: قيمة أساسية `baseVal` وقيمة متحركة `animVal`. 

### الغرض
الغرض من `SVGAnimatedInteger` هو توفير واجهة لتتبع القيم العددية التي يمكن أن تتغير، مثل تلك التي تنتج عن الرسوم المتحركة أو التفاعلات.

### الاستخدام
يمكن استخدام `SVGAnimatedInteger` في أي عنصر SVG يحتوي على خاصية عددية مثل `width` أو `height` أو `x` أو `y`. على سبيل المثال:

```javascript
let rect = document.createElementNS("http://www.w3.org/2000/svg", "rect");
rect.setAttribute("width", "100");
rect.setAttribute("height", "100");
```

### التفاصيل
- **baseVal**: تمثل القيمة الأساسية للعدد.
- **animVal**: تمثل القيمة الحالية التي يمكن أن تتغير نتيجة لرسوم متحركة أو تفاعلات أخرى.

## الأمثلة
### مثال 1: استخدام `SVGAnimatedInteger` مع مستطيل
```javascript
let svg = document.createElementNS("http://www.w3.org/2000/svg", "svg");
let rect = document.createElementNS("http://www.w3.org/2000/svg", "rect");
rect.setAttribute("width", "100");
rect.setAttribute("height", "100");
svg.appendChild(rect);
document.body.appendChild(svg);

// الوصول إلى خاصية width
let width = rect.width.baseVal.value; // 100
console.log(width);
```

### مثال 2: تغيير القيمة باستخدام `baseVal`
```javascript
rect.width.baseVal.value = 200; // تغيير عرض المستطيل
console.log(rect.width.baseVal.value); // 200
```

## الشرح
### الأخطاء الشائعة
1. **عدم استخدام مساحة الأسماء الصحيحة**: عند إنشاء عناصر SVG، تأكد من استخدام `createElementNS` مع النطاق الصحيح (`http://www.w3.org/2000/svg`).
2. **خلط بين `baseVal` و `animVal`**: `baseVal` تمثل القيمة الأصلية، بينما `animVal` تمثل القيمة الناتجة عن الرسوم المتحركة، لذا تأكد من استخدام الخاصية الصحيحة حسب السياق.

### ملاحظات إضافية
`SVGAnimatedInteger` مفيدة جدًا في الرسوم المتحركة، حيث تتيح لك تتبع القيم المتغيرة بسهولة. تأكد من فهم كيفية استخدام كل من `baseVal` و `animVal` لتحقيق أقصى استفادة.

## ملخص من جملة واحدة
`SVGAnimatedInteger` هي واجهة في JavaScript تسمح بتتبع القيم العددية المتغيرة في عناصر SVG، مما يسهل التعامل مع الرسوم المتحركة والتفاعلات.