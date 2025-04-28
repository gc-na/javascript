<!--
Meta Description: # عنصر SVGAnimateElement في JavaScript: دليل شامل ## ملخص يُعتبر عنصر SVGAnimateElement جزءًا مهمًا من واجهة برمجة التطبيقات لـ SVG في JavaScript، حيث...
Meta Keywords: svg, svganimateelement, عنصر, الرسوم, المتحركة
-->

# عنصر SVGAnimateElement في JavaScript: دليل شامل

## ملخص
يُعتبر عنصر SVGAnimateElement جزءًا مهمًا من واجهة برمجة التطبيقات لـ SVG في JavaScript، حيث يُستخدم لإنشاء الرسوم المتحركة داخل مستندات SVG.

## الوثائق
### الغرض
يُستخدم عنصر SVGAnimateElement لتحديد الرسوم المتحركة في عناصر SVG. يتيح لك هذا العنصر التحكم في خصائص العناصر مثل الموضع، الحجم، اللون، وغيرها من الخصائص عبر الزمن.

### الاستخدام
يتطلب استخدام SVGAnimateElement أن يتم تضمينه داخل عنصر SVG. يمكن أن يتواجد داخل عناصر مثل `<rect>`, `<circle>`, أو `<path>`. يمكن أن يتم تحريكه أو تغيير خصائصه بناءً على خصائص مثل `begin`, `dur`, و `repeatCount`.

#### التركيب الأساسي
```html
<animate attributeName="attribute" from="value1" to="value2" dur="duration" repeatCount="value" />
```

### التفاصيل
- **attributeName**: يُحدد اسم الخاصية التي سيتم تحريكها.
- **from**: القيمة الابتدائية للخاصية.
- **to**: القيمة النهائية للخاصية.
- **dur**: مدة الرسوم المتحركة.
- **repeatCount**: عدد مرات تكرار الرسوم المتحركة (يمكن أن يكون قيمة عددية أو "indefinite" للتكرار اللانهائي).

## أمثلة
### مثال 1: تغيير لون مربع
```html
<svg width="100" height="100">
    <rect width="100" height="100" fill="red">
        <animate attributeName="fill" from="red" to="blue" dur="2s" repeatCount="indefinite" />
    </rect>
</svg>
```

### مثال 2: تحريك دائرة
```html
<svg width="200" height="200">
    <circle cx="50" cy="50" r="40" fill="green">
        <animate attributeName="cx" from="50" to="150" dur="3s" repeatCount="indefinite" />
    </circle>
</svg>
```

## الشرح
### الأخطاء الشائعة
- **عدم تحديد الخاصية بشكل صحيح**: تأكد من أن الاسم الموجود في `attributeName` هو اسم صحيح وصالح للعنصر المستهدف.
- **نسيان وضع العنصر داخل SVG**: يجب أن يتم إدراج عنصر SVGAnimateElement داخل عنصر SVG، وإلا فلن تعمل الرسوم المتحركة.

### ملاحظات إضافية
- يعتبر SVGAnimateElement جزءًا من معايير SVG 1.1، لذا تأكد من استخدام المتصفحات التي تدعم هذه المعايير.
- يمكن دمج SVGAnimateElement مع JavaScript لمزيد من التحكم في الرسوم المتحركة، مثل استخدام الأحداث أو التفاعلات.

## ملخص جملة واحدة
يستخدم عنصر SVGAnimateElement في JavaScript لإنشاء رسوم متحركة ديناميكية داخل مستندات SVG، مما يعزز تجربة المستخدم ويضيف لمسة جمالية.