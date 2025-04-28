<!--
Meta Description: # عنصر SVGAnimateMotionElement في JavaScript: الدليل الشامل ## ملخص يعتبر عنصر `SVGAnimateMotionElement` جزءًا من تقنية SVG (Scalable Vector Graphics)...
Meta Keywords: svg, عنصر, path, الحركة, svganimatemotionelement
-->

# عنصر SVGAnimateMotionElement في JavaScript: الدليل الشامل

## ملخص
يعتبر عنصر `SVGAnimateMotionElement` جزءًا من تقنية SVG (Scalable Vector Graphics) التي تتيح للمطورين إنشاء حركات متحركة للأشكال في صفحات الويب باستخدام JavaScript.

## الوثائق
### الغرض
`SVGAnimateMotionElement` يتيح لك إضافة حركة إلى العناصر الرسومية في SVG. يمكن استخدامه لتحريك العناصر على مسار محدد، مما يضيف بعدًا ديناميكيًا وجذابًا لتجارب المستخدم.

### الاستخدام
يتم استخدام `SVGAnimateMotionElement` كعنصر ضمن عناصر SVG لتحديد حركة عنصر معين. يمكن أن يكون العنصر المتحرك أي شكل SVG مثل الدوائر أو المستطيلات أو المسارات. يتطلب استخدام هذا العنصر تحديد مسار الحركة باستخدام عنصر `<mpath>`.

### التفاصيل
- **الخصائص**:
  - `begin`: يحدد متى تبدأ الحركة.
  - `dur`: يحدد مدة الحركة.
  - `repeatCount`: يحدد عدد مرات تكرار الحركة.
  
- **المميزات**:
  - يدعم الرسوم المتحركة التلقائية.
  - يمكن دمجها بسهولة مع JavaScript لتخصيص سلوك الحركة بناءً على تفاعلات المستخدم.

## أمثلة

### مثال 1: حركة بسيطة
```html
<svg width="200" height="200">
  <circle cx="50" cy="50" r="20" fill="red">
    <animateMotion dur="2s" repeatCount="indefinite">
      <mpath href="#path" />
    </animateMotion>
  </circle>
  <path id="path" d="M 50 50 C 100 0, 100 100, 50 50" stroke="none" fill="none"/>
</svg>
```

### مثال 2: حركة متكررة
```html
<svg width="300" height="300">
  <rect x="10" y="10" width="30" height="30" fill="blue">
    <animateMotion dur="1s" repeatCount="5">
      <mpath href="#path" />
    </animateMotion>
  </rect>
  <path id="path" d="M 10 10 L 200 10 L 200 200 Z" stroke="none" fill="none"/>
</svg>
```

## الشرح
### الأخطاء الشائعة
- **عدم تعريف المسار**: يجب التأكد من وجود عنصر `<path>` معرف بشكل صحيح، وإلا لن تعمل الحركة بشكل صحيح.
- **القيم غير الصحيحة**: استخدام قيم غير صحيحة في الخصائص مثل `dur` أو `repeatCount` قد يؤدي إلى سلوك غير متوقع.
- **تداخل العناصر**: في حالة وجود عناصر متعددة متداخلة، تأكد من أن كل عنصر له خصائصه الخاصة دون تداخل.

## ملخص بجملة واحدة
`SVGAnimateMotionElement` هو عنصر SVG يمكّن المطورين من إضافة حركات ديناميكية على العناصر باستخدام مسارات محددة، مما يعزز تجربة المستخدم في تطبيقات الويب.