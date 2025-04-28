<!--
Meta Description: # ShadowRoot في JavaScript: كل ما تحتاج لمعرفته ## ملخص `ShadowRoot` هو واجهة في JavaScript تُستخدم لإنشاء شجرة ظل (Shadow Tree) لعناصر الويب، مما يتي...
Meta Keywords: shadowroot, شجرة, myelement, إلى, dom
-->

# ShadowRoot في JavaScript: كل ما تحتاج لمعرفته

## ملخص
`ShadowRoot` هو واجهة في JavaScript تُستخدم لإنشاء شجرة ظل (Shadow Tree) لعناصر الويب، مما يتيح لك بناء مكونات قابلة لإعادة الاستخدام مع عزل الـ CSS والـ DOM.

## الوثائق
### الغرض
تُستخدم `ShadowRoot` لإنشاء شجرة ظل لعناصر الويب، مما يسمح بتغليف المحتوى الخاص بك مع الحفاظ على نمط CSS الخاص بك معزولاً عن بقية الصفحة. هذا يُساعد في تجنب التصادمات بين الأنماط ويسمح بتطوير مكونات واجهة مستخدم أكثر تنظيماً.

### الاستخدام
لإنشاء شجرة ظل، يجب أولاً استخدام `attachShadow` على عنصر HTML. بعد ذلك، يمكنك إضافة عناصر إلى شجرة الظل باستخدام DOM.

#### طريقة `attachShadow`
```javascript
let shadowRoot = element.attachShadow({ mode: 'open' });
```

- **mode**: يشير إلى وضع الشجرة، وهو إما `open` أو `closed`. في وضع `open`، يمكن الوصول إلى الشجرة من خلال `element.shadowRoot`.

### التفاصيل
- **الوضع المفتوح (open)**: يمكن الوصول إلى شجرة الظل من خلال `element.shadowRoot`.
- **الوضع المغلق (closed)**: لا يمكن الوصول إلى شجرة الظل من خلال `element.shadowRoot`، مما يوفر عزلًا أقوى.

## الأمثلة
### مثال 1: إنشاء شجرة ظل مفتوحة
```html
<div id="myElement"></div>
<script>
  const myElement = document.getElementById('myElement');
  const shadowRoot = myElement.attachShadow({ mode: 'open' });
  shadowRoot.innerHTML = `<style>p { color: blue; }</style><p>Hello Shadow DOM!</p>`;
</script>
```

### مثال 2: إنشاء شجرة ظل مغلقة
```html
<div id="myElement"></div>
<script>
  const myElement = document.getElementById('myElement');
  const shadowRoot = myElement.attachShadow({ mode: 'closed' });
  shadowRoot.innerHTML = `<style>p { color: red; }</style><p>Hello Shadow DOM!</p>`;
  console.log(myElement.shadowRoot); // undefined
</script>
```

## الشرح
### الأخطاء الشائعة
- **عدم الوصول إلى شجرة الظل**: في حالة استخدام الوضع المغلق، لن تتمكن من الوصول إلى `shadowRoot` من العنصر، لذا تأكد من اختيار الوضع الصحيح حسب احتياجاتك.
- **نمط CSS غير معزول**: تأكد من إضافة الأنماط داخل شجرة الظل للحصول على التأثير المطلوب، حيث لن تؤثر الأنماط الموجودة في الصفحة الرئيسية على شجرة الظل.

### ملاحظات إضافية
- تأكد من أن المتصفح يدعم `Shadow DOM`، حيث قد لا تعمل هذه الميزة في بعض المتصفحات القديمة.
- استخدم `ShadowRoot` بحذر عند العمل مع مكتبات أو أطر عمل خارجية، حيث قد تتعارض مع نمط CSS الخاص بك.

## ملخص في جملة واحدة
`ShadowRoot` في JavaScript يتيح لك إنشاء شجرة ظل لعناصر الويب، مما يوفر عزلًا فعالًا للـ CSS والـ DOM.