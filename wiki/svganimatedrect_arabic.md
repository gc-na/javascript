<!--
Meta Description: # SVGAnimatedRect في JavaScript: التعامل مع عناصر SVG المتحركة ## ملخص SVGAnimatedRect هو واجهة في JavaScript تُستخدم للتعامل مع مستطيلات SVG المتحركة...
Meta Keywords: svg, rect, baseval, المتحركة, svganimatedrect
-->

# SVGAnimatedRect في JavaScript: التعامل مع عناصر SVG المتحركة

## ملخص
SVGAnimatedRect هو واجهة في JavaScript تُستخدم للتعامل مع مستطيلات SVG المتحركة. تتيح هذه الواجهة للمطورين التحكم في خصائص المستطيلات مثل العرض والارتفاع والموقع بشكل ديناميكي.

## الوثائق
### الغرض
تُستخدم SVGAnimatedRect لتوفير واجهة برمجية للتحكم في مستطيلات SVG بطريقة متحركة. يتضمن ذلك خصائص مثل `x`, `y`, `width`, و`height`، مما يجعل من السهل إنشاء رسوم متحركة ديناميكية تستجيب لأحداث المستخدم أو التغييرات في البيانات.

### الاستخدام
يمكن استخدام SVGAnimatedRect في أي عنصر SVG مستطيل. يتم إنشاؤه عادةً باستخدام عنصر `<rect>` في مستند SVG. يتم تمثيل الخصائص المتحركة بشكل خاص باستخدام `baseVal` و`animVal`، مما يسمح بالتحكم في القيم الأساسية والقيم المتحركة.

### التفاصيل
- **baseVal**: القيمة الأساسية للخاصية.
- **animVal**: القيمة المتحركة الحالية للخاصية.
- يمكن الوصول إلى هذه الخصائص وتعديلها باستخدام JavaScript، مما يسهل إنشاء تفاعلات بصرية متقدمة.

## الأمثلة
### مثال 1: إنشاء مستطيل متحرك بسيط
```html
<svg width="200" height="200">
  <rect id="myRect" x="10" y="10" width="100" height="50" fill="blue">
    <animate attributeName="x" from="10" to="150" dur="2s" repeatCount="indefinite" />
  </rect>
</svg>

<script>
  const rect = document.getElementById("myRect");
  console.log(rect.x.baseVal.value); // 10
  rect.x.baseVal.value = 50; // تغيير موقع المستطيل
</script>
```

### مثال 2: تغيير أبعاد المستطيل
```html
<svg width="200" height="200">
  <rect id="myRect" x="10" y="10" width="100" height="50" fill="green"></rect>
</svg>

<script>
  const rect = document.getElementById("myRect");
  rect.width.baseVal.value = 150; // تغيير عرض المستطيل
  rect.height.baseVal.value = 75;  // تغيير ارتفاع المستطيل
</script>
```

## الشرح
### الأخطاء الشائعة والملاحظات
- **التحكم في القيم المتحركة**: من المهم فهم الفرق بين `baseVal` و`animVal`. التغييرات على `baseVal` ستؤثر على القيمة المتحركة، ولكن `animVal` قد لا تعكس ذلك مباشرة إذا كانت هناك رسوم متحركة نشطة.
- **التوافق مع المتصفحات**: تأكد من اختبار كود SVGAnimatedRect في مختلف المتصفحات، حيث قد تختلف طريقة دعم SVG بين المتصفحات.

## ملخص جملة واحدة
SVGAnimatedRect هي واجهة JavaScript تتيح التحكم الديناميكي في خصائص مستطيلات SVG، مما يسهل إنشاء رسوم متحركة تفاعلية.