<!--
Meta Description: # خاصية isSecureContext في JavaScript: فهم واستخدامات ## ملخص خاصية `isSecureContext` في JavaScript تستخدم لتحديد ما إذا كان السياق الحالي (مثل صفحة ا...
Meta Keywords: issecurecontext, إذا, بيئة, آمنة, كانت
-->

# خاصية isSecureContext في JavaScript: فهم واستخدامات

## ملخص
خاصية `isSecureContext` في JavaScript تستخدم لتحديد ما إذا كان السياق الحالي (مثل صفحة الويب) يتم تشغيله في بيئة آمنة أم لا، مما يؤثر على الوصول إلى بعض الميزات الحساسة.

## الوثائق
### الغرض
تساعد خاصية `isSecureContext` المطورين في التأكد مما إذا كانت بيئة التشغيل آمنة. يتم اعتبار البيئة آمنة إذا كانت الصفحة محملة عبر HTTPS أو إذا كانت في بيئة محلية.

### الاستخدام
يمكن الوصول إلى خاصية `isSecureContext` من خلال الكائن العالمي `window`. تعيد هذه الخاصية قيمة من نوع Boolean، حيث تعيد `true` إذا كانت الصفحة في سياق آمن، و`false` إذا لم تكن كذلك.

### التفاصيل
- **الأنواع المدعومة**: `Boolean`
- **القيمة المرجعة**: 
  - `true` إذا كانت الصفحة تعمل على بروتوكول HTTPS أو في بيئة محلية.
  - `false` إذا كانت الصفحة تعمل على بروتوكول HTTP أو في بيئة غير آمنة.

## الأمثلة
### مثال 1: التحقق من أمان السياق
```javascript
if (window.isSecureContext) {
    console.log("السياق آمن.");
} else {
    console.log("السياق غير آمن.");
}
```

### مثال 2: استخدام isSecureContext في ميزات الـ Web APIs
```javascript
if (window.isSecureContext) {
    // استخدام ميزات مثل Web Bluetooth أو Web USB
    console.log("يمكن استخدام ميزات الويب الحساسة.");
} else {
    console.log("لا يمكن استخدام ميزات الويب الحساسة.");
}
```

## الشرح
### الأخطاء الشائعة
- **عدم فهم الفرق بين HTTP و HTTPS**: يعتبر الكثيرون أن أي نوع من أنواع الاتصال هو آمن، ولكن يجب التأكد من استخدام HTTPS.
- **التطبيقات المحلية**: قد يعتقد البعض أن التطبيقات المحلية (مثل تلك التي يتم تشغيلها من الملفات المحلية) غير آمنة، لكن في الواقع، تعتبر بيئة محلية آمنة.

### ملاحظات إضافية
- يتم استخدام `isSecureContext` بشكل متزايد في ميزات الويب الحديثة، وخاصة تلك المتعلقة بالأمان مثل WebRTC.
- ينصح باستخدام هذه الخاصية في جميع التطبيقات التي تتطلب الأمان لضمان استفادة المستخدمين من مزايا الأمان المتاحة.

## ملخص جملة واحدة
خاصية `isSecureContext` في JavaScript تحدد ما إذا كان السياق الحالي يعمل في بيئة آمنة، مما يؤثر على إمكانية الوصول إلى ميزات الويب الحساسة.