<!--
Meta Description: # عنصر SVGGradientElement في JavaScript ## ملخص يعتبر عنصر `SVGGradientElement` جزءاً من واجهة برمجة التطبيقات لرسومات SVG في JavaScript، حيث يتيح للم...
Meta Keywords: stop, svg, التدرج, defs, svggradientelement
-->

# عنصر SVGGradientElement في JavaScript

## ملخص
يعتبر عنصر `SVGGradientElement` جزءاً من واجهة برمجة التطبيقات لرسومات SVG في JavaScript، حيث يتيح للمطورين إنشاء تدرجات لونية تستخدم في رسم الأشكال والتصاميم الجرافيكية على صفحات الويب.

## الوثائق
### الغرض
`SVGGradientElement` هو نوع من الكائنات في SVG يستخدم لتعريف التدرجات اللونية، سواء كانت تدرجات خطية (`linear gradients`) أو تدرجات دائرية (`radial gradients`). يمكن استخدامه لتغيير مظهر الأشكال مثل المستطيلات والدوائر والمضلعات.

### الاستخدام
لإنشاء تدرج لوني باستخدام `SVGGradientElement`، تحتاج إلى تحديد نوع التدرج (خطّي أو دائري) باستخدام العناصر المناسبة (`<linearGradient>` أو `<radialGradient>`) داخل عنصر `<defs>`. 
يمكنك بعد ذلك استخدام معرف التدرج (ID) في خاصية `fill` أو `stroke` للأشكال.

### التفاصيل
- **الخصائص:** يمكن تحديد خصائص مثل `x1`, `y1`, `x2`, `y2` لتحديد اتجاه التدرج، وأيضًا `cx`, `cy`, `r` لتحديد مركز ونصف قطر التدرج الدائري.
- **الإضافات:** يمكن إضافة نقاط توقف (`<stop>`) داخل التدرج لتحديد الألوان المختلفة والمواقع الخاصة بها.
- **التوافق:** `SVGGradientElement` مدعوم بشكل جيد في جميع المتصفحات الحديثة.

## أمثلة
### مثال 1: تدرج خطي
```html
<svg width="200" height="200">
  <defs>
    <linearGradient id="grad1" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:rgb(255,255,0);stop-opacity:1" />
      <stop offset="100%" style="stop-color:rgb(255,0,0);stop-opacity:1" />
    </linearGradient>
  </defs>
  <rect width="200" height="200" fill="url(#grad1)" />
</svg>
```

### مثال 2: تدرج دائري
```html
<svg width="200" height="200">
  <defs>
    <radialGradient id="grad2" cx="50%" cy="50%" r="50%" fx="50%" fy="50%">
      <stop offset="0%" style="stop-color:rgb(0,255,0);stop-opacity:1" />
      <stop offset="100%" style="stop-color:rgb(0,0,255);stop-opacity:1" />
    </radialGradient>
  </defs>
  <circle cx="100" cy="100" r="80" fill="url(#grad2)" />
</svg>
```

## الشرح
### الأخطاء الشائعة
- **نسيان تعريف `<defs>`:** يجب أن يتم تعريف التدرج داخل عنصر `<defs>`، وإلا فلن يتم التعرف عليه.
- **عدم استخدام المعرف:** تأكد من استخدام المعرف الصحيح للتدرج في خاصية `fill` أو `stroke`.
- **عدم توافق الألوان:** استخدام ألوان غير مدعومة أو غير صحيحة قد يؤدي إلى عدم ظهور التدرج كما هو متوقع.

## ملخص جملة واحدة
`SVGGradientElement` هو عنصر في SVG يسمح بإنشاء تدرجات لونية لتعزيز المظهر الجرافيكي للأشكال باستخدام JavaScript.