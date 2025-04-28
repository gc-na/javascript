<!--
Meta Description: # حدث BeforeInstallPromptEvent في JavaScript: فهم واستخدام ## ملخص يعد حدث `BeforeInstallPromptEvent` جزءًا من واجهة برمجة تطبيقات الويب Progressive W...
Meta Keywords: التثبيت, نافذة, عرض, beforeinstallpromptevent, الحدث
-->

# حدث BeforeInstallPromptEvent في JavaScript: فهم واستخدام

## ملخص
يعد حدث `BeforeInstallPromptEvent` جزءًا من واجهة برمجة تطبيقات الويب Progressive Web Apps (PWAs) في JavaScript، ويستخدم لإدارة عرض نافذة التثبيت لمواقع الويب التي تم تحسينها كتطبيقات.

## الوثائق
### الغرض
يهدف `BeforeInstallPromptEvent` إلى توفير واجهة للمطورين للتحكم في عرض نافذة التثبيت لمواقع الويب. يحدث هذا الحدث قبل أن يُظهر المتصفح نافذة تثبيت PWA، مما يمنح المطورين الفرصة لإظهار عناصر واجهة المستخدم المخصصة أو رسائل الإشعار.

### الاستخدام
يمكن الاستماع لحدث `beforeinstallprompt` من خلال إضافة مستمع للأحداث إلى الكائن `window`. عند حدوث هذا الحدث، يمكن للمطورين إلغاء العرض التلقائي لنافذة التثبيت واستبداله بعرض مخصص.

```javascript
let deferredPrompt;

window.addEventListener('beforeinstallprompt', (e) => {
  // منع العرض التلقائي
  e.preventDefault();
  // تخزين الحدث للتعامل معه لاحقًا
  deferredPrompt = e;
  
  // عرض زر التثبيت المخصص
  showInstallButton();
});

// وظيفة لإظهار زر التثبيت
function showInstallButton() {
  const installButton = document.getElementById('installButton');
  installButton.style.display = 'block';
  
  installButton.addEventListener('click', async () => {
    // إظهار نافذة التثبيت
    deferredPrompt.prompt();
    
    // انتظار استجابة المستخدم
    const { outcome } = await deferredPrompt.userChoice;
    if (outcome === 'accepted') {
      console.log('المستخدم قام بالتثبيت');
    } else {
      console.log('المستخدم رفض التثبيت');
    }
    deferredPrompt = null; // إعادة تعيين المتغير
  });
}
```

## الأمثلة
### مثال أساسي
```javascript
window.addEventListener('beforeinstallprompt', (e) => {
  e.preventDefault(); // منع العرض التلقائي
  let installPromptEvent = e; // حفظ الحدث
  // عرض زر التثبيت
  document.getElementById('installButton').style.display = 'block';
});
```

### استخدام مع زر التثبيت
```javascript
document.getElementById('installButton').addEventListener('click', () => {
  installPromptEvent.prompt(); // عرض نافذة التثبيت
});
```

## الشرح
### الأخطاء الشائعة
- **عدم منع العرض التلقائي**: يجب دائمًا منع العرض التلقائي للنافذة باستخدام `e.preventDefault()`، وإلا فإن نافذة التثبيت ستظهر دون أي تفاعل من المستخدم.
- **عدم تخزين الحدث**: إذا لم يتم تخزين `BeforeInstallPromptEvent`، فلن تتمكن من عرض نافذة التثبيت لاحقًا.

### ملاحظات إضافية
- لا يتم دعم `BeforeInstallPromptEvent` في جميع المتصفحات، لذا تأكد من اختبار التطبيق على المتصفحات المستهدفة.
- يجب أن يكون التطبيق متوافقًا مع معايير PWA ليظهر هذا الحدث، بما في ذلك وجود ملف `manifest.json` و HTTPS.

## ملخص بجملة واحدة
يتيح حدث `BeforeInstallPromptEvent` للمطورين التحكم في عرض نافذة التثبيت لتطبيقات الويب التقدمية، مما يوفر تجربة مخصصة للمستخدم.