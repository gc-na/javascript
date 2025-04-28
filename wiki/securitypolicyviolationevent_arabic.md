<!--
Meta Description: # حدث SecurityPolicyViolationEvent في JavaScript ## ملخص حدث SecurityPolicyViolationEvent هو جزء من واجهة برمجة التطبيقات (API) في JavaScript التي تُس...
Meta Keywords: الأمان, حدث, سياسة, securitypolicyviolationevent, إلى
-->

# حدث SecurityPolicyViolationEvent في JavaScript

## ملخص
حدث SecurityPolicyViolationEvent هو جزء من واجهة برمجة التطبيقات (API) في JavaScript التي تُستخدم للكشف عن الانتهاكات التي تحدث نتيجة لسياسة الأمان المحتوى (CSP) في تطبيقات الويب. يتيح هذا الحدث للمطورين مراقبة أي محاولات غير مصرح بها لتحميل الموارد أو تنفيذ التعليمات البرمجية.

## الوثائق
### الغرض
يتم استخدام حدث SecurityPolicyViolationEvent للإشارة إلى وجود انتهاك لسياسة الأمان المحتوى، مما يساعد في تعزيز أمان التطبيقات عن طريق تنبيه المطورين بأي نشاط غير مقبول.

### الاستخدام
يتم تنشيط هذا الحدث عندما تُخفق محاولة لتحميل مورد أو تنفيذ كود بسبب قيود سياسة الأمان. يمكن التقاطه باستخدام مستمعي الأحداث (event listeners) على كائن `window`.

### التفاصيل
- **الخصائص**:
  - `blockedURI`: يحدد URI للموارد المحظورة.
  - `documentURI`: يحدد URI للمستند الذي حدث فيه الانتهاك.
  - `effectiveDirective`: يوضح التوجيه الفعلي الذي تسبب في الانتهاك.
  - `originalPolicy`: يعرض سياسة الأمان الأصلية التي تم تطبيقها.
  - `sourceFile`: يشير إلى ملف المصدر الذي يتسبب في الانتهاك.
  - `lineNumber`: يُظهر رقم السطر في ملف المصدر حيث وقع الانتهاك.

## الأمثلة
### مثال 1: التعامل مع حدث الانتهاك
```javascript
window.addEventListener('securitypolicyviolation', (event) => {
    console.log('انتُهكت سياسة الأمان:');
    console.log('URI المحظور:', event.blockedURI);
    console.log('URI المستند:', event.documentURI);
    console.log('التوجيه الفعلي:', event.effectiveDirective);
});
```

### مثال 2: سياسة أمان المحتوى
```html
<meta http-equiv="Content-Security-Policy" content="script-src 'self';">
<script src="https://example.com/untrusted.js"></script>
```
في هذا المثال، ستؤدي محاولة تحميل `untrusted.js` إلى إطلاق حدث SecurityPolicyViolationEvent.

## الشرح
### العقبات الشائعة
- **تقليل مستوى الأمان**: قد يرغب المطورون في تقليل قيود سياسة الأمان لأغراض الاختبار، ولكن هذا يمكن أن يؤدي إلى مخاطر أمنية.
- **إغفال بعض التوجيهات**: عدم تضمين جميع التوجيهات المطلوبة في سياسة الأمان قد يؤدي إلى الانتهاكات.
- **التعامل مع بيانات حساسة**: يجب تجنب تسريب المعلومات الحساسة من خلال تسجيل الأحداث.

## ملخص جملة واحدة
يُعتبر حدث SecurityPolicyViolationEvent أداة قوية لمراقبة الانتهاكات في سياسة الأمان المحتوى في تطبيقات JavaScript، مما يساعد على تعزيز الأمان ومراقبة النشاطات غير المصرح بها.