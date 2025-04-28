<!--
Meta Description: # حدث onsecuritypolicyviolation في جافا سكريبت: كل ما تحتاج معرفته ## ملخص حدث `onsecuritypolicyviolation` في جافا سكريبت يُستخدم للإبلاغ عن انتهاكات ...
Meta Keywords: onsecuritypolicyviolation, الحدث, event, حدث, الأمان
-->

# حدث onsecuritypolicyviolation في جافا سكريبت: كل ما تحتاج معرفته

## ملخص
حدث `onsecuritypolicyviolation` في جافا سكريبت يُستخدم للإبلاغ عن انتهاكات سياسة الأمان المحتوى (Content Security Policy - CSP)، وهو يُعتبر جزءًا هامًا من تحسين أمان التطبيقات ويعمل على حماية المواقع من الهجمات المختلفة.

## التوثيق
### الغرض
يهدف حدث `onsecuritypolicyviolation` إلى تقديم معلومات حول انتهاكات سياسة الأمان المحتوى، مما يساعد المطورين على فهم نقاط الضعف في تطبيقاتهم وإجراء التحسينات اللازمة.

### الاستخدام
يتم استخدام هذا الحدث كجزء من واجهة `Window` أو كجزء من عنصر معين في الصفحة. يتم تفعيله تلقائيًا عندما يحدث انتهاك لسياسة الأمان المحتوى، ويقوم بإرسال معلومات عن الانتهاك إلى الدالة المعينة.

### التفاصيل
- **الحدث**: `onsecuritypolicyviolation`
- **نوع الحدث**: `SecurityPolicyViolationEvent`
- **الخصائص**:
  - `blockedURI`: URI الذي تم حظره.
  - `effectiveDirective`: التوجيه الفعال الذي تم انتهاك سياسة الأمان بسببه.
  - `sourceFile`: ملف المصدر الذي تسبب في الانتهاك.
  - `lineNumber`: رقم السطر في الملف المصدر.
  
### كيفية الإعداد
لتفعيل هذا الحدث، يمكنك استخدام الكود التالي:

```javascript
window.onsecuritypolicyviolation = function(event) {
    console.log("حدث انتهاك سياسة الأمان:", event);
};
```

## أمثلة
### مثال أساسي
```javascript
// إعداد حدث onsecuritypolicyviolation
window.onsecuritypolicyviolation = function(event) {
    alert(`تم حظر المحتوى من: ${event.blockedURI}`);
};
```

### مثال متقدم
```javascript
// إعداد حدث onsecuritypolicyviolation مع معالجة معلومات إضافية
window.onsecuritypolicyviolation = function(event) {
    console.error(`انتهاك في ${event.sourceFile} في السطر ${event.lineNumber}`);
    console.warn(`التوجيه الفعال: ${event.effectiveDirective}`);
};
```

## الشرح
### النقاط الشائعة
- **عدم معالجة الحدث**: عدم وجود دالة لمعالجة الحدث قد يؤدي إلى فقدان معلومات قيمة حول الانتهاكات.
- **التجاهل**: يمكن أن يؤدي تجاهل هذه الانتهاكات إلى ثغرات أمنية في التطبيق.
- **تكوين CSP**: يجب التأكد من تكوين سياسة الأمان بشكل صحيح، حيث أن التكوين الخاطئ يمكن أن يؤدي إلى انتهاكات متكررة.

### ملاحظات إضافية
- لا تنسَ اختبار تطبيقك على مختلف المتصفحات، حيث قد يختلف دعم الحدث بين المتصفحات.
- يجب استخدام الحدث في بيئات الإنتاج لتحديد المشاكل المحتملة بشكل أفضل.

## ملخص جملة واحدة
حدث `onsecuritypolicyviolation` في جافا سكريبت هو أداة مهمة للكشف عن انتهاكات سياسة الأمان المحتوى وتحسين أمان التطبيقات.