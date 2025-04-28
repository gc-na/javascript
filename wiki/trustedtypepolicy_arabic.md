<!--
Meta Description: # TrustedTypePolicy في JavaScript: حماية ضد هجمات XSS ## ملخص TrustedTypePolicy هو واجهة برمجية في JavaScript تهدف إلى تحسين أمان تطبيقات الويب من خلا...
Meta Keywords: trustedtypepolicy, javascript, xss, استخدام, القيم
-->

# TrustedTypePolicy في JavaScript: حماية ضد هجمات XSS

## ملخص
TrustedTypePolicy هو واجهة برمجية في JavaScript تهدف إلى تحسين أمان تطبيقات الويب من خلال منع هجمات XSS (Cross-Site Scripting) عن طريق التحكم في كيفية تعيين القيم إلى عناصر DOM.

## الوثائق
تعتبر TrustedTypePolicy جزءًا من واجهة Trusted Types، وهي مجموعة من القواعد التي تسمح للمطورين بإنشاء سياسات للتحكم في كيفية إنشاء القيم الموثوقة التي يمكن إدراجها في العناصر DOM. يتم استخدام TrustedTypePolicy لتحديد كيفية التعامل مع النصوص والقيم التي قد تكون عرضة للهجمات.

### الغرض
يهدف TrustedTypePolicy إلى:
- تقليل مخاطر هجمات XSS عن طريق تصفية القيم غير الموثوقة.
- توفير واجهة برمجية واضحة للمطورين لإنشاء سياسات تخص القيم الموثوقة.

### الاستخدام
لإنشاء سياسة موثوقة، يمكنك استخدام الأمر `TrustedTypePolicy` كما يلي:

```javascript
const policy = trustedTypes.createPolicy('myPolicy', {
  createHTML: (input) => {
    // معالجة المدخلات هنا
    return sanitizedHTML; // القيمة المصفاة والموثوقة
  },
});
```

## الأمثلة
### مثال 1: إنشاء سياسة موثوقة
```javascript
const policy = trustedTypes.createPolicy('myPolicy', {
  createHTML: (input) => {
    // تأمين المدخلات
    return input.replace(/</g, '&lt;').replace(/>/g, '&gt;');
  },
});

// استخدام السياسة
const safeHTML = policy.createHTML('<div>Hello World</div>');
document.body.innerHTML = safeHTML; // سيتم إدراج HTML المصفى
```

### مثال 2: استخدام السياسة مع دالة `innerHTML`
```javascript
const userInput = '<script>alert("XSS Attack")</script>';
const safeHTML = policy.createHTML(userInput);
document.body.innerHTML = safeHTML; // لن يتم تنفيذ السكربت
```

## الشرح
### العثرات الشائعة
- **عدم تصفية المدخلات بشكل صحيح**: يجب التأكد من أن المدخلات تتم معالجتها بشكل صحيح قبل إدراجها في DOM.
- **عدم استخدام السياسة**: عندما تستخدم متغيرات مباشرة في `innerHTML` دون تطبيق السياسة، فإنك تعرض تطبيقك لهجمات XSS.
- **عدم التحقق من دعم المتصفح**: تأكد من أن المتصفح يدعم Trusted Types قبل استخدامه، حيث أن بعض المتصفحات قد لا تدعمه.

### ملاحظات إضافية
- يجب استخدام `TrustedTypePolicy` في التطبيقات التي تتعامل مع إدخال المستخدم.
- يجب توخي الحذر عند العمل مع مكتبات أخرى قد تتداخل مع إدارة الأمان.

## ملخص جملة واحدة
TrustedTypePolicy في JavaScript هو وسيلة فعالة لحماية تطبيقات الويب من هجمات XSS من خلال التحكم في القيم المدخلة إلى عناصر DOM.