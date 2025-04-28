<!--
Meta Description: # cancelAnimationFrame: كيفية إلغاء الإطارات المتحركة في JavaScript ## ملخص `cancelAnimationFrame` هو دالة في JavaScript تُستخدم لإلغاء الإطار المتحرك...
Meta Keywords: cancelanimationframe, المتحركة, الرسوم, الإطار, المتحرك
-->

# cancelAnimationFrame: كيفية إلغاء الإطارات المتحركة في JavaScript

## ملخص
`cancelAnimationFrame` هو دالة في JavaScript تُستخدم لإلغاء الإطار المتحرك الذي تم جدولة تنفيذه باستخدام `requestAnimationFrame`. تساعد هذه الدالة في إدارة الرسوم المتحركة بشكل فعال وتحسين أداء التطبيقات.

## الوثائق
### الغرض
يُستخدم `cancelAnimationFrame` لإلغاء طلب إطار متحرك تم تحديده مسبقًا. يُعتبر هذا مهمًا للحفاظ على أداء التطبيق، خاصةً عند توقف الرسوم المتحركة أو عند الخروج من صفحة ويب.

### الاستخدام
تقبل `cancelAnimationFrame` معرف الإطار المتحرك الذي تم إرجاعه من `requestAnimationFrame`.

### التركيب
```javascript
cancelAnimationFrame(id);
```

### المعاملات
- `id`: معرف الإطار المتحرك الذي تم جدولة تنفيذه، ويجب أن يكون من نوع Number.

### الملاحظات
- يجب استدعاء `cancelAnimationFrame` قبل أن يتم تنفيذ الإطار المتحرك المعني، وإلا فلن يؤثر ذلك.
- تعمل `cancelAnimationFrame` فقط على معرفات تم إنشاؤها باستخدام `requestAnimationFrame`.

## أمثلة
### مثال أساسي
```javascript
let animationId;

function animate() {
    // تنفيذ الرسوم المتحركة هنا
    animationId = requestAnimationFrame(animate);
}

// بدء الرسوم المتحركة
animate();

// إلغاء الرسوم المتحركة بعد 2 ثانية
setTimeout(() => {
    cancelAnimationFrame(animationId);
    console.log('تم إلغاء الرسوم المتحركة');
}, 2000);
```

## الشرح
### الأخطاء الشائعة
- **عدم إلغاء الإطار المتحرك**: إذا لم يتم تخزين معرف الإطار المتحرك بشكل صحيح، فلن تتمكن من إلغاءه، مما يمكن أن يؤدي إلى أداء ضعيف.
- **استدعاء `cancelAnimationFrame` بعد تنفيذ الإطار**: لن تؤثر الدالة على الإطارات التي تم تنفيذها بالفعل.

### ملاحظات إضافية
- يُفضل استخدام `requestAnimationFrame` مع `cancelAnimationFrame` لضمان إدارة الرسوم المتحركة بشكل متقن.
- يمكن استخدام هذه الدالة في ألعاب الويب والتطبيقات التفاعلية لتحسين الأداء وتقليل استخدام المعالج.

## ملخص جملة واحدة
`cancelAnimationFrame` هي دالة في JavaScript تستخدم لإلغاء طلبات الإطارات المتحركة، مما يساعد في تحسين أداء الرسوم المتحركة في التطبيقات.