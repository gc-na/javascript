<!--
Meta Description: # TrustedScriptURL في JavaScript: فهم الآلية وأهميتها ## ملخص TrustedScriptURL هو نوع من البيانات في JavaScript يتيح للمطورين إنشاء روابط موثوقة للبرم...
Meta Keywords: trustedscripturl, موثوقة, javascript, إنشاء, يتم
-->

# TrustedScriptURL في JavaScript: فهم الآلية وأهميتها

## ملخص
TrustedScriptURL هو نوع من البيانات في JavaScript يتيح للمطورين إنشاء روابط موثوقة للبرمجيات النصية، مما يعزز الأمان عند التعامل مع المحتوى الديناميكي.

## الوثائق
### الغرض
تم تصميم TrustedScriptURL لتحسين أمان التطبيقات التي تستخدم JavaScript، خصوصًا عند إدارة محتوى ديناميكي أو إدراج برمجيات نصية من مصادر غير موثوقة. يضمن هذا النوع من البيانات أن يتم تنفيذ البرمجيات النصية فقط إذا كانت موثوقة.

### الاستخدام
يتم استخدام TrustedScriptURL عادةً في بيئات مثل Web APIs حيث يتطلب الأمر ضمان عدم تنفيذ برمجيات نصية ضارة. يتم إنشاؤه عادة عبر واجهات برمجة التطبيقات المعتمدة (API) التي تدعم إنشاء هذا النوع من البيانات.

### التفاصيل
- **إنشاء TrustedScriptURL**: يتم إنشاء هذا النوع من الكائنات باستخدام واجهات برمجة التطبيقات المخصصة مثل `TrustedTypes.createPolicy`.
- **تحقق الموثوقية**: يمكن استخدام TrustedScriptURL فقط إذا تم التحقق من أنه ينتمي إلى سياسة موثوقة، مما يمنع تنفيذ البرمجيات النصية غير المصرح بها.

## أمثلة
### مثال بسيط لإنشاء TrustedScriptURL
```javascript
// إنشاء سياسة موثوقة
const policy = trustedTypes.createPolicy('default', {
  createScriptURL: (input) => {
    return input; // تأكد من أن الإدخال موثوق
  }
});

// استخدام TrustedScriptURL
const scriptURL = policy.createScriptURL('https://example.com/script.js');
console.log(scriptURL); // https://example.com/script.js
```

### مثال على الاستخدام في عنصر <script>
```javascript
const scriptElement = document.createElement('script');
scriptElement.src = scriptURL; // تعيين مصدر سكريبت موثوق
document.head.appendChild(scriptElement);
```

## الشرح
### الفخاخ الشائعة
- **إدخال غير موثوق**: إذا تم تمرير إدخال غير موثوق إلى `createScriptURL`، فقد يؤدي ذلك إلى تنفيذ برمجيات نصية ضارة.
- **عدم وجود سياسة موثوقة**: يجب أن يتم التأكد من وجود سياسة موثوقة قبل محاولة إنشاء TrustedScriptURL، وإلا قد يتم تجاهل الطلب.

### ملاحظات إضافية
- **التوافق**: تأكد من أن المتصفحات التي تستهدفها تدعم Trusted Types، حيث لا تتوفر هذه الميزة في جميع البيئات.
- **الأداء**: يساهم استخدام TrustedScriptURL في تحسين الأداء والأمان عن طريق تقليل الحاجة لفحص البرمجيات النصية بشكل متكرر.

## ملخص من جملة واحدة
TrustedScriptURL هو نوع بيانات في JavaScript يضمن أمان البرمجيات النصية من خلال توفير روابط موثوقة ومحمية.