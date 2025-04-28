<!--
Meta Description: # واجهة برمجة التطبيقات WakeLock في JavaScript: الحفاظ على توازن الطاقة في تطبيقات الويب ## ملخص واجهة برمجة التطبيقات WakeLock في JavaScript توفر وسي...
Meta Keywords: wakelock, wake, lock, javascript, على
-->

# واجهة برمجة التطبيقات WakeLock في JavaScript: الحفاظ على توازن الطاقة في تطبيقات الويب

## ملخص
واجهة برمجة التطبيقات WakeLock في JavaScript توفر وسيلة للمطورين للحفاظ على تشغيل الشاشة في الأجهزة المحمولة، مما يمنعها من الدخول في وضع السكون أثناء تنفيذ العمليات الهامة، مثل مشاهدة الفيديو أو قراءة المحتوى.

## الوثائق
### الغرض
تهدف واجهة WakeLock إلى تحسين تجربة المستخدم من خلال منع شاشة الجهاز من الإغلاق أثناء تفاعل المستخدم مع المحتوى. هذه الواجهة مفيدة بشكل خاص في تطبيقات الويب التي تتطلب استمرارية العرض دون انقطاع.

### الاستخدام
يمكن استخدام WakeLock في JavaScript عبر استدعاء `navigator.wakeLock.request()`. يتيح لك هذا الأمر طلب قفل الشاشة، ويمكنك إلغاء هذا القفل باستخدام `wakeLock.release()`.

#### الخطوات:
1. **طلب Wake Lock:**
   ```javascript
   let wakeLock = null;

   async function requestWakeLock() {
       try {
           wakeLock = await navigator.wakeLock.request('screen');
           console.log('Wake Lock أُنشئ بنجاح');
       } catch (err) {
           console.error(`${err.name}, ${err.message}`);
       }
   }
   ```

2. **إلغاء Wake Lock:**
   ```javascript
   async function releaseWakeLock() {
       if (wakeLock !== null) {
           await wakeLock.release();
           wakeLock = null;
           console.log('Wake Lock أُلغى بنجاح');
       }
   }
   ```

### التفاصيل
- **الدعم:** يجب ملاحظة أن دعم WakeLock قد يختلف من متصفح لآخر، لذا يُفضل التحقق من دعم المتصفح قبل استخدام هذه الواجهة.
- **أنواع القفل:** يمكنك طلب نوعين من Wake Lock: `'screen'` و`'system'`. النوع الأول يمنع الشاشة من الانطفاء، بينما الثاني يؤثر على وضع السكون العام للجهاز.
- **الإصدار:** تأكد من التعامل مع الأخطاء عند الطلب أو إلغاء Wake Lock، حيث يمكن أن تفشل العملية إذا كان هناك قيود على الجهاز.

## أمثلة
### مثال بسيط على استخدام Wake Lock:
```javascript
// طلب Wake Lock عند الضغط على زر
document.getElementById('lockButton').addEventListener('click', requestWakeLock);

// إلغاء Wake Lock عند الضغط على زر آخر
document.getElementById('unlockButton').addEventListener('click', releaseWakeLock);
```

## الشرح
### الأمور التي يجب الانتباه إليها
- **التوافق:** تأكد من أن المتصفح يدعم واجهة WakeLock. قم بفحص `navigator.wakeLock` قبل الاستخدام.
- **استنزاف البطارية:** استخدام Wake Lock بشكل مفرط يمكن أن يؤدي إلى استنزاف البطارية بسرعة، لذا يجب استخدامه بحذر وفي الحالات الضرورية فقط.
- **التغيرات في حالة الجهاز:** يجب التعامل مع الحالات التي قد تؤدي إلى إلغاء Wake Lock تلقائيًا، مثل تغيير حالة الجهاز أو إيقاف تشغيله.

## ملخص في جملة واحدة
واجهة WakeLock في JavaScript تمنع الشاشة من الإغلاق خلال فترات الاستخدام الحرجة، مما يعزز تجربة المستخدم في تطبيقات الويب.