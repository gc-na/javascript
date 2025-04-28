<!--
Meta Description: # SVGAnimatedNumber في JavaScript: كل ما تحتاج معرفته ## الملخص تعتبر خاصية `SVGAnimatedNumber` جزءًا مهمًا من واجهة برمجة التطبيقات (API) الخاصة بـ S...
Meta Keywords: المتحركة, svg, svganimatednumber, الرسوم, animval
-->

# SVGAnimatedNumber في JavaScript: كل ما تحتاج معرفته

## الملخص
تعتبر خاصية `SVGAnimatedNumber` جزءًا مهمًا من واجهة برمجة التطبيقات (API) الخاصة بـ SVG في JavaScript، حيث تتيح للمطورين التعامل مع الأعداد المتحركة في الرسوميات المتجهة.

## الوثائق
### الوصف
`SVGAnimatedNumber` هو نوع بيانات يستخدم في SVG لتمثيل الأعداد المتحركة. يُستخدم هذا النوع بشكل شائع في الرسوم المتحركة للخصائص العددية للعنصر، مثل الأبعاد والموضع. يتكون من خاصيتين: `baseVal` و`animVal`.

- **baseVal**: القيمة الأساسية للعدد.
- **animVal**: القيمة المتحركة التي يتم تحديثها خلال الرسوم المتحركة.

### الاستخدام
يمكن استخدام `SVGAnimatedNumber` في العديد من العناصر SVG التي تحتاج إلى خصائص عددية، مثل `<circle>`, `<rect>`, و`<line>`. يتم تحديث `animVal` تلقائيًا أثناء تشغيل الرسوم المتحركة، بينما تبقى `baseVal` ثابتة.

### التفاصيل
- **المدعومة في**: جميع المتصفحات الحديثة.
- **المتطلبات**: يجب أن يكون العنصر SVG موجودًا في DOM.
  
## أمثلة
### مثال 1: استخدام `SVGAnimatedNumber` في دائرة
```html
<svg width="100" height="100">
  <circle id="myCircle" cx="50" cy="50" r="40" fill="red">
    <animate attributeName="r" from="40" to="10" dur="1s" repeatCount="indefinite" />
  </circle>
</svg>

<script>
  const circle = document.getElementById('myCircle').r;
  console.log(circle.baseVal); // 40
  // ستتغير قيمة animVal أثناء الرسوم المتحركة
</script>
```

### مثال 2: استخدام `SVGAnimatedNumber` مع مستطيل
```html
<svg width="200" height="200">
  <rect id="myRect" width="100" height="100" fill="blue">
    <animate attributeName="width" from="100" to="200" dur="2s" repeatCount="indefinite" />
  </rect>
</svg>

<script>
  const rect = document.getElementById('myRect').width;
  console.log(rect.baseVal); // 100
  // ستتغير قيمة animVal أثناء الرسوم المتحركة
</script>
```

## الشرح
### النقاط الشائعة
- **عدم تحديث القيم**: تأكد من أن العنصر SVG يتم تحميله بالكامل قبل محاولة الوصول إلى `baseVal` و`animVal`.
- **الاعتماد على الرسوم المتحركة**: إذا كانت الرسوم المتحركة غير نشطة، ستظل `animVal` تساوي `baseVal`.

### الملاحظات
- `SVGAnimatedNumber` لا يدعم العمليات الحسابية مباشرة، لذا يجب عليك تحويله إلى قيمة عددية عند الحاجة.
- كن حذرًا من استخدام `animVal` في الأحداث التي تعتمد على الوقت، حيث يمكن أن تتغير القيم بشكل غير متوقع.

## ملخص من سطر واحد
`SVGAnimatedNumber` هو نوع بيانات في JavaScript يستخدم لتمثيل الأعداد المتحركة في الرسوميات المتجهة، مما يتيح التحكم في الخصائص العددية للعنصر أثناء الرسوم المتحركة.