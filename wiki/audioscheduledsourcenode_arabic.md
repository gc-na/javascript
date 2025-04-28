<!--
Meta Description: # AudioScheduledSourceNode في JavaScript: دليلك الشامل ## ملخص AudioScheduledSourceNode هو كائن في واجهة برمجة تطبيقات Web Audio API يُستخدم لإنشاء صو...
Meta Keywords: الصوت, audiocontext, audioscheduledsourcenode, تشغيل, sourcenode
-->

# AudioScheduledSourceNode في JavaScript: دليلك الشامل

## ملخص
AudioScheduledSourceNode هو كائن في واجهة برمجة تطبيقات Web Audio API يُستخدم لإنشاء صوت يمكن جدولة تشغيله في وقت معين.

## الوثائق
AudioScheduledSourceNode هو كائن أساسي في Web Audio API، حيث يتيح للمطورين إنشاء مصادر صوتية يمكن التحكم بها بدقة من حيث التوقيت. يُستخدم هذا الكائن غالباً في التطبيقات الصوتية المتقدمة مثل الألعاب والتطبيقات الموسيقية.

### الأغراض
- **جدولة الصوت**: يتيح لك AudioScheduledSourceNode جدولة تشغيل الصوت في أوقات محددة، مما يجعله مثالياً لإنشاء تجارب تفاعلية سلسة.
- **التحكم في المعالجة**: يمكنك التحكم في معالجة الصوت باستخدام مجموعة متنوعة من التأثيرات والتعديلات.

### الاستخدام
يتم استخدام AudioScheduledSourceNode عادةً بالتزامن مع AudioBufferSourceNode أو MediaElementAudioSourceNode، حيث يمكنك تحميل الصوت وتحريكه عبر الزمن باستخدام واجهة برمجة التطبيقات.

### التفاصيل
- **الخصائص**: يحتوي على خصائص مثل `start`, `stop`, و `playbackRate` التي تساعد في التحكم في تشغيل الصوت.
- **طرق**:
  - `start(when)`: يبدأ تشغيل المصدر في الوقت المحدد.
  - `stop(when)`: يوقف تشغيل المصدر في الوقت المحدد.
  
## الأمثلة
### مثال 1: تشغيل صوت باستخدام AudioScheduledSourceNode
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const sourceNode = audioContext.createBufferSource();

fetch('path/to/audio/file.mp3')
  .then(response => response.arrayBuffer())
  .then(data => audioContext.decodeAudioData(data))
  .then(buffer => {
    sourceNode.buffer = buffer;
    sourceNode.connect(audioContext.destination);
    sourceNode.start(0); // يبدأ التشغيل على الفور
  })
  .catch(err => console.error(err));
```

### مثال 2: جدولة تشغيل الصوت في وقت محدد
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const sourceNode = audioContext.createBufferSource();

fetch('path/to/audio/file.mp3')
  .then(response => response.arrayBuffer())
  .then(data => audioContext.decodeAudioData(data))
  .then(buffer => {
    sourceNode.buffer = buffer;
    sourceNode.connect(audioContext.destination);
    const currentTime = audioContext.currentTime;
    sourceNode.start(currentTime + 2); // يبدأ التشغيل بعد ثانيتين
  })
  .catch(err => console.error(err));
```

## الشرح
### الأخطاء الشائعة
- **عدم تحميل الصوت بشكل صحيح**: تأكد من أن مسار الصوت صحيح وأن الخادم يدعم CORS إذا كان الصوت في خادم خارجي.
- **عدم استجابة واجهة برمجة التطبيقات**: تأكد من أن لديك إذنًا لتشغيل الصوت، حيث قد يتطلب الأمر تفاعل المستخدم (مثل نقر زر) قبل أن تتمكن من تشغيل الصوت.

### ملاحظات إضافية
- يُفضل دائمًا استخدام Web Audio API في بيئات تدعمها، وقد تكون لبعض المتصفحات قيود على تشغيل الصوت تلقائيًا.
- تأكد من إدارة الذاكرة بشكل جيد، خاصة عند استخدام عدة كائنات AudioScheduledSourceNode.

## ملخص بسيط
AudioScheduledSourceNode هو كائن في Web Audio API يُستخدم لجدولة الصوت بدقة في تطبيقات JavaScript.