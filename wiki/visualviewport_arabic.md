<!--
Meta Description: # visualViewport: ميزات وإمكانيات في JavaScript ## ملخص `visualViewport` هو واجهة برمجية في JavaScript توفر معلومات حول viewport المرئي للمستخدم، مما ...
Meta Keywords: viewport, visualviewport, javascript, المرئي, على
-->

# visualViewport: ميزات وإمكانيات في JavaScript

## ملخص
`visualViewport` هو واجهة برمجية في JavaScript توفر معلومات حول viewport المرئي للمستخدم، مما يسمح للمطورين بتطوير تطبيقات الويب بشكل أفضل تتلاءم مع شاشات الأجهزة المختلفة.

## الوثائق
### الغرض
تساعد واجهة `visualViewport` المطورين في فهم كيف يتفاعل المستخدم مع شاشة العرض، بما في ذلك قياسات viewport، والتحركات، والتكبير. هذه المعلومات هامة لضمان تجربة مستخدم سلسة، خاصة على الأجهزة المحمولة.

### الاستخدام
يمكن الوصول إلى `visualViewport` من خلال الكائن `window`. تتضمن الواجهة الخصائص والأحداث التالية:

- **الخصائص:**
  - `width`: عرض viewport المرئي.
  - `height`: ارتفاع viewport المرئي.
  - `offsetLeft`: المسافة بين بداية viewport وبدء الصفحة.
  - `offsetTop`: المسافة بين بداية viewport وبدء الصفحة.
  - `scale`: نسبة التكبير الحالية.

- **الأحداث:**
  - `resize`: يُطلق عند تغيير حجم viewport.
  - `scroll`: يُطلق عند تغيير موضع التمرير.

### تفاصيل
يتوفر `visualViewport` في معظم المتصفحات الحديثة. يجب على المطورين التأكد من أن التطبيق الخاص بهم يعالج التغيرات في الحجم والتمرير بشكل صحيح لتحسين تجربة المستخدم.

## الأمثلة
### مثال 1: عرض أبعاد viewport
```javascript
console.log('عرض viewport: ', visualViewport.width);
console.log('ارتفاع viewport: ', visualViewport.height);
```

### مثال 2: استخدام حدث resize
```javascript
visualViewport.addEventListener('resize', () => {
    console.log('تم تغيير حجم viewport!');
});
```

### مثال 3: الحصول على نسبة التكبير
```javascript
console.log('نسبة التكبير الحالية: ', visualViewport.scale);
```

## التفسير
من الشائع أن يواجه المطورون بعض التحديات عند العمل مع `visualViewport`، مثل عدم دعم بعض المتصفحات الأقدم أو عدم وجود تغييرات في القياسات عند التمرير. لذلك، من المهم اختبار التطبيق عبر مجموعة متنوعة من الأجهزة والمتصفحات للتأكد من التوافق.

## ملخص جملة واحدة
`visualViewport` هو واجهة برمجية في JavaScript توفر معلومات دقيقة حول viewport المرئي للمستخدم، مما يساعد في تحسين تجربة المستخدم على الويب.