<!--
Meta Description: # WakeLockSentinel في JavaScript: الحفاظ على نشاط الشاشة ## ملخص WakeLockSentinel هو واجهة برمجية في JavaScript تهدف إلى الحفاظ على تشغيل الشاشة في ال...
Meta Keywords: wakelock, wake, lock, القفل, على
-->

# WakeLockSentinel في JavaScript: الحفاظ على نشاط الشاشة

## ملخص
WakeLockSentinel هو واجهة برمجية في JavaScript تهدف إلى الحفاظ على تشغيل الشاشة في الأجهزة المحمولة أو الأجهزة اللوحية، مما يمنع نظام التشغيل من إدخال الشاشة في وضع السكون.

## الوثائق
### الغرض
تستخدم واجهة WakeLockSentinel لتجنب إيقاف تشغيل الشاشة أثناء تنفيذ مهام معينة مثل مشاهدة الفيديو أو إجراء مكالمات الفيديو، حيث أن إيقاف تشغيل الشاشة يمكن أن يؤثر سلبًا على تجربة المستخدم.

### الاستخدام
يمكن استخدام واجهة WakeLockSentinel من خلال واجهة `Screen Wake Lock API`. لإنشاء Wake Lock، تحتاج إلى استدعاء `navigator.wakeLock.request()`، ثم يمكنك استخدام الكائن الذي يتم إرجاعه للتحكم في الحالة.

### التفاصيل
- **طلب القفل**: يمكنك طلب Wake Lock باستخدام `navigator.wakeLock.request('screen')`.
- **إطلاق القفل**: يمكنك تحرير القفل باستخدام الطريقة `release()` على الكائن المرتجع.
- **الخطط المستقبلية**: يجب مراقبة التغييرات في حالة القفل حيث قد يتم تحريره تلقائيًا من قبل النظام.

## الأمثلة
### مثال 1: طلب Wake Lock
```javascript
async function requestWakeLock() {
    try {
        const wakeLock = await navigator.wakeLock.request('screen');
        console.log('Wake Lock نشط');

        // تنفيذ الكود الخاص بك هنا
        
        // عند الانتهاء، يمكنك تحرير القفل
        await wakeLock.release();
        console.log('Wake Lock تم تحريره');
    } catch (err) {
        console.error(`${err.name}, ${err.message}`);
    }
}

requestWakeLock();
```

### مثال 2: التعامل مع الأحداث
```javascript
let wakeLock = null;

async function toggleWakeLock() {
    if (wakeLock === null) {
        wakeLock = await navigator.wakeLock.request('screen');
        console.log('Wake Lock نشط');
    } else {
        await wakeLock.release();
        wakeLock = null;
        console.log('Wake Lock تم تحريره');
    }
}

toggleWakeLock();
```

## الشرح
### الفخاخ الشائعة
- **التوافق**: تأكد من أن المتصفح يدعم واجهة Wake Lock API. تحقق من توافق المتصفحات قبل البدء في الاستخدام.
- **الإفراج عن القفل**: إذا نسيت تحرير القفل، قد يؤدي ذلك إلى استنزاف عمر البطارية.
- **التعامل مع الأخطاء**: يجب عليك دائمًا معالجة الأخطاء عند طلب Wake Lock، حيث قد يفشل الطلب لأسباب متعددة.

## ملخص جملة واحدة
WakeLockSentinel في JavaScript يوفر طريقة للحفاظ على تشغيل الشاشة، مما يساهم في تحسين تجربة المستخدم أثناء تنفيذ المهام المهمة على الأجهزة المحمولة.