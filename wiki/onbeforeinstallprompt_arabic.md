<!--
Meta Description: # حدث onbeforeinstallprompt في JavaScript: دليلك الشامل ## ملخص يُعد حدث `onbeforeinstallprompt` في JavaScript ميزة مهمة تسهل للمطورين استجابة المستخد...
Meta Keywords: التطبيق, الحدث, المستخدم, التثبيت, مربع
-->

# حدث onbeforeinstallprompt في JavaScript: دليلك الشامل

## ملخص
يُعد حدث `onbeforeinstallprompt` في JavaScript ميزة مهمة تسهل للمطورين استجابة المستخدمين عندما يكون التطبيق جاهزًا للتثبيت كـ PWA (تطبيق ويب تقدمي).

## الوثائق
### الغرض
يستخدم حدث `onbeforeinstallprompt` لإعلام المطورين بأن التطبيق الويب يمكن تثبيته كـ PWA. يُعتبر هذا الحدث فرصة لجعل تجربة المستخدم أكثر سلاسة من خلال تقديم واجهة مستخدم مخصصة للتفاعل مع المستخدم حول عملية التثبيت.

### الاستخدام
يتم التعامل مع هذا الحدث عندما يكون لدى المتصفح إمكانية تثبيت التطبيق. يجب على المطورين إضافة مستمع لهذا الحدث، حيث يمكنهم التحكم في كيفية ومتى يظهر مربع الحوار لتثبيت التطبيق.

### التفاصيل
- **الحدث**: `beforeinstallprompt`
- **نوع الحدث**: مخصص (Custom Event)
- **الخصائص**:
  - `prompt()`: وظيفة تستدعي مربع حوار التثبيت.
  - `userChoice`: تعدد الخيارات التي يختارها المستخدم بخصوص التثبيت (مُعد مسبقًا).
  
### كيفية الاستخدام
```javascript
let deferredPrompt;

window.addEventListener('beforeinstallprompt', (e) => {
    // منع ظهور مربع الحوار الافتراضي
    e.preventDefault();
    // حفظ الحدث ليتم استخدامه لاحقًا
    deferredPrompt = e;
    // عرض زر التثبيت للمستخدم
    showInstallButton();
});

// عندما ينقر المستخدم على زر التثبيت
installButton.addEventListener('click', async () => {
    // إظهار مربع الحوار التثبيت
    deferredPrompt.prompt();
    // انتظار اختيار المستخدم
    const { outcome } = await deferredPrompt.userChoice;
    if (outcome === 'accepted') {
        console.log('تم تثبيت التطبيق');
    } else {
        console.log('تم رفض التثبيت');
    }
    deferredPrompt = null;
});
```

## أمثلة
### مثال بسيط
في المثال التالي، يتم إعداد مستمع للحدث `beforeinstallprompt`، والذي يظهر زر لتثبيت التطبيق عند توفره.
```javascript
let installButton = document.getElementById('installButton');

window.addEventListener('beforeinstallprompt', (e) => {
    e.preventDefault();
    installButton.style.display = 'block'; // عرض الزر
});

installButton.addEventListener('click', async () => {
    deferredPrompt.prompt(); // عرض مربع الحوار
    const { outcome } = await deferredPrompt.userChoice;
    if (outcome === 'accepted') {
        console.log('تم تثبيت التطبيق');
    }
});
```

## الشرح
- **العقبات الشائعة**: 
  - يجب التأكد من أن `onbeforeinstallprompt` لا يظهر إلا مرة واحدة. إذا تم استدعاء `prompt()` عدة مرات، فسيؤدي ذلك إلى إرباك المستخدم.
  - ليس كل المتصفحات تدعم هذا الحدث، لذا تأكد من اختبار التطبيق عبر البيئات المختلفة.
  
- **ملاحظات إضافية**:
  - يتم تفعيل هذا الحدث فقط عند استخدام تطبيق ويب تقدمي (PWA) والذي تم نشره عبر HTTPS.
  - تأكد من تقديم تجربة مستخدم جيدة عند إظهار مربع الحوار، حيث يجب أن يكون للمستخدم خيار واضح سواء بالموافقة أو الرفض.

## ملخص بسط
حدث `onbeforeinstallprompt` في JavaScript يتيح للمطورين التحكم في كيفية ظهور مربع الحوار لتثبيت التطبيق الويب التقدمي، مما يحسن من تجربة المستخدم.