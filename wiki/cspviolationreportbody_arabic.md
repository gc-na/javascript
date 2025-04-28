<!--
Meta Description: # CSPViolationReportBody: فهم شامل لتقارير انتهاك سياسة المحتوى في JavaScript ## الملخص CSPViolationReportBody هو كائن يستخدم في JavaScript لتوفير معل...
Meta Keywords: csp, المحتوى, uri, cspviolationreportbody, سياسة
-->

# CSPViolationReportBody: فهم شامل لتقارير انتهاك سياسة المحتوى في JavaScript

## الملخص
CSPViolationReportBody هو كائن يستخدم في JavaScript لتوفير معلومات مفصلة حول انتهاكات سياسة المحتوى (CSP) التي تحدث في تطبيقات الويب. يسهل تحليل هذه الانتهاكات من قبل المطورين لضمان أمان التطبيقات.

## الوثائق
CSP (Content Security Policy) هي آلية أمان تهدف إلى منع مجموعة من الهجمات مثل XSS (Cross-Site Scripting) و البيانات المتلاعبة. يتم استخدام CSPViolationReportBody في سياق تقارير انتهاك CSP التي تُرسل إلى الخادم عندما يحدث انتهاك للسياسة المحددة.

### الغرض
يهدف CSPViolationReportBody إلى توفير معلومات دقيقة حول نوع الانتهاك، والعناصر المتأثرة، وأسباب الانتهاك. يمكن استخدام هذه المعلومات لتحليل الثغرات الأمنية وتحسين سياسة المحتوى.

### الاستخدام
عند تفعيل تقارير CSP في تطبيق ويب، يتم إنشاء كائن CSPViolationReportBody تلقائيًا وإرساله إلى عنوان URL المخصص لتلقي التقارير. يتضمن الكائن تفاصيل مثل:
- `document-uri`: URI الصفحة التي حدث فيها الانتهاك.
- `referrer`: عنوان الصفحة المحال.
- `blocked-uri`: URI العنصر الممنوع.
- `violated-directive`: السياسة التي تم انتهاكها.

### التفاصيل
تتضمن العناصر الأساسية لـ CSPViolationReportBody:
- **document-uri**: يحدد الموقع الذي حدث فيه الانتهاك.
- **referrer**: يوضح المصدر الذي جاء منه الطلب.
- **block-uri**: يوضح URI العنصر الذي تم حظره.
- **violated-directive**: يحدد السياسة التي تم انتهاكها.

## الأمثلة
### مثال 1: إنشاء تقرير انتهاك CSP
```javascript
// إعداد سياسة المحتوى مع تفعيل التقارير
const cspPolicy = "default-src 'self'; report-uri /csp-report-endpoint";

// إضافة سياسة المحتوى إلى الرأس
document.addEventListener('DOMContentLoaded', () => {
    document.head.appendChild(createCSPMetaTag(cspPolicy));
});

// وظيفة لإنشاء علامة ميتا لسياسة المحتوى
function createCSPMetaTag(policy) {
    const meta = document.createElement('meta');
    meta.httpEquiv = 'Content-Security-Policy';
    meta.content = policy;
    return meta;
}
```

### مثال 2: تحليل تقرير انتهاك
```javascript
// إعداد خادم لتلقي تقارير انتهاك CSP
app.post('/csp-report-endpoint', (req, res) => {
    const report = req.body;
    console.log('CSP Violation Report:', report);
    res.status(204).send(); // إرسال استجابة فارغة
});
```

## الشرح
### الأخطاء الشائعة
- **عدم تفعيل تقارير CSP**: يجب التأكد من أن سياسة المحتوى تم تكوينها بشكل صحيح لتفعيل التقارير.
- **عدم معالجة التقارير بشكل صحيح**: يجب على المطورين التأكد من أن الخادم مهيأ لاستقبال ومعالجة تقارير CSP بشكل صحيح.

### ملاحظات إضافية
- من الضروري مراجعة تقارير CSP بانتظام لفهم الأنماط الشائعة في الانتهاكات.
- يمكن استخدام أدوات مثل Google Chrome DevTools لمراقبة انتهاكات CSP أثناء تطوير التطبيقات.

## ملخص بجملة واحدة
CSPViolationReportBody هو كائن JavaScript يقدم معلومات مفصلة حول انتهاكات سياسة المحتوى، مما يساعد المطورين على تعزيز أمان تطبيقاتهم.