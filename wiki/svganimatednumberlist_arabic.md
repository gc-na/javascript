<!--
Meta Description: # SVGAnimatedNumberList في JavaScript: دليل شامل ## ملخص تعتبر `SVGAnimatedNumberList` نوعًا خاصًا من الأنواع في SVG (Scalable Vector Graphics) يتم اس...
Meta Keywords: القيمة, المتحركة, svganimatednumberlist, يمكن, javascript
-->

# SVGAnimatedNumberList في JavaScript: دليل شامل

## ملخص
تعتبر `SVGAnimatedNumberList` نوعًا خاصًا من الأنواع في SVG (Scalable Vector Graphics) يتم استخدامه في JavaScript للتعامل مع القوائم المتحركة من الأرقام. يمكن استخدامها لإجراء تغييرات ديناميكية على خصائص SVG المختلفة.

## الوثائق
`SVGAnimatedNumberList` هو كائن يُستخدم في SVG لتخزين قائمة من الأرقام التي يمكن أن تتغير بمرور الوقت. يتكون هذا الكائن من عنصرين رئيسيين:

1. **baseVal**: يمثل القيمة الأساسية للقائمة.
2. **animVal**: يمثل القيمة المتحركة للقائمة، والتي يمكن أن تتغير مع مرور الوقت أو نتيجة لتأثيرات الرسوم المتحركة.

### الاستخدام
يمكن استخدام `SVGAnimatedNumberList` في JavaScript للوصول إلى وتعديل القيم العددية التي تستخدم في خصائص SVG مثل `stroke-dasharray` أو `transform`. يمكن أن تكون هذه القيم متحركة، مما يعني أنها يمكن أن تتغير بمرور الوقت بناءً على الرسوم المتحركة أو التفاعلات.

### تفاصيل
- **الإنشاء**: يتم إنشاء `SVGAnimatedNumberList` تلقائيًا عند تعريف خاصية SVG تدعم القوائم العددية.
- **الخصائص**:
  - `baseVal`: يمكن الوصول إلى هذه القيمة وتعديلها مباشرة.
  - `animVal`: تمثل القيمة المتحركة وتُستخدم فقط للقراءة.

## أمثلة
### مثال 1: الوصول إلى `baseVal`
```javascript
let circle = document.getElementById('myCircle');
let radiusList = circle.r.animVal; // الحصول على القيمة المتحركة
console.log(radiusList); // طباعة القيمة
```

### مثال 2: تعديل `baseVal`
```javascript
let rect = document.getElementById('myRect');
let widthList = rect.width.baseVal; // الحصول على القيمة الأساسية
widthList.value = 100; // تغيير القيمة
```

## الشرح
عند التعامل مع `SVGAnimatedNumberList`, هناك بعض النقاط التي يجب الانتباه إليها:
- لا يتم تحديث `animVal` إلا إذا كانت هناك رسوم متحركة قيد التنفيذ؛ لذلك تأكد من أن الرسوم المتحركة فعالة عند محاولة الوصول إلى هذه القيمة.
- عند تعديل `baseVal`, قد تحتاج إلى إعادة رسم العنصر لضمان تطبيق التغييرات.

## ملخص بجملة واحدة
تُعتبر `SVGAnimatedNumberList` أداة قوية في JavaScript للتعامل مع القوائم المتحركة من الأرقام في SVG، مما يسمح بالتخصيص الديناميكي للرسومات.