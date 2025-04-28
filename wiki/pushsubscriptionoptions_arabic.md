<!--
Meta Description: # خيارات الاشتراك في الدفع (PushSubscriptionOptions) في JavaScript ## ملخص تعتبر خيارات الاشتراك في الدفع (PushSubscriptionOptions) جزءًا أساسيًا من و...
Meta Keywords: الاشتراك, الدفع, خيارات, javascript, pushsubscriptionoptions
-->

# خيارات الاشتراك في الدفع (PushSubscriptionOptions) في JavaScript

## ملخص
تعتبر خيارات الاشتراك في الدفع (PushSubscriptionOptions) جزءًا أساسيًا من واجهة برمجة التطبيقات لإشعارات الويب (Web Notifications API) في JavaScript. تمكن هذه الخيارات المطورين من تخصيص إعدادات الاشتراك الخاص بالرسائل الفورية.

## الوثائق
خيارات الاشتراك في الدفع (PushSubscriptionOptions) هي كائن يستخدم لتحديد الخصائص المتعلقة بالاشتراك في الدفع. يتم استخدام هذه الخيارات عند طلب الاشتراك في خدمة الدفع لاستقبال الإشعارات.

### الغرض
الغرض من خيارات الاشتراك في الدفع هو منح المطورين السيطرة على كيفية تلقي الرسائل، بما في ذلك إعدادات مثل تنسيق الرسالة وأولوياتها.

### الاستخدام
يتم استخدام خيارات الاشتراك في الدفع عند استدعاء `subscribe` على كائن `PushManager`. يمكن أن تشمل الخيارات المعلمات التالية:
- `userVisibleOnly`: قيمة منطقية تحدد ما إذا كانت الرسالة مرئية للمستخدم.
- `applicationServerKey`: مفتاح الخادم المستخدم لتوثيق الاشتراكات.

### التفاصيل
```javascript
const options = {
  userVisibleOnly: true,
  applicationServerKey: urlB64ToUint8Array('YOUR_PUBLIC_VAPID_KEY')
};
```

## أمثلة
### الاشتراك مع خيارات
```javascript
navigator.serviceWorker.ready.then(function(registration) {
  const options = {
    userVisibleOnly: true,
    applicationServerKey: urlB64ToUint8Array('YOUR_PUBLIC_VAPID_KEY')
  };

  return registration.pushManager.subscribe('push', options);
}).then(function(subscription) {
  console.log('تم الاشتراك بنجاح:', subscription);
}).catch(function(error) {
  console.error('فشل الاشتراك:', error);
});
```

## الشرح
### العثرات الشائعة
- **عدم توفر الخدمة**: قد لا تتوفر خدمة العمل (Service Worker) مما يؤدي إلى فشل الاشتراك.
- **المفتاح غير صحيح**: تأكد من أن مفتاح VAPID العمومي صحيح. استخدام مفتاح خاطئ قد يؤدي إلى أخطاء في الاشتراك.
- **عدم قبول المستخدم**: يجب أن يوافق المستخدم على تلقي الإشعارات، وإذا لم يتم ذلك سيتم رفض الاشتراك.

### ملاحظات إضافية
تأكد من أن لديك خدمة عملية تعمل وتدعم HTTPS، حيث أن إشعارات الويب تحتاج إلى بيئة آمنة.

## ملخص جملة واحدة
خيارات الاشتراك في الدفع (PushSubscriptionOptions) في JavaScript تتيح للمطورين تخصيص إعدادات الاشتراك لتلقي الإشعارات الفورية بشكل فعال.