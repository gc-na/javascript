<!--
Meta Description: # AudioBufferSourceNode في جافا سكريبت: دليلك الشامل ## ملخص `AudioBufferSourceNode` هو واجهة في واجهة برمجة تطبيقات الصوت في جافا سكريبت (Web Audio A...
Meta Keywords: الصوت, audiocontext, source, تشغيل, audiobuffersourcenode
-->

# AudioBufferSourceNode في جافا سكريبت: دليلك الشامل

## ملخص
`AudioBufferSourceNode` هو واجهة في واجهة برمجة تطبيقات الصوت في جافا سكريبت (Web Audio API) تُستخدم لتشغيل الصوت من مصفوفة بيانات صوتية (AudioBuffer).

## الوثائق
### الغرض
`AudioBufferSourceNode` يُستخدم لتشغيل البيانات الصوتية المحفوظة في كائن `AudioBuffer`. يمكنك من خلاله تشغيل الصوت، والتحكم في خصائصه مثل مستوى الصوت، والتأخير، والتكرار.

### الاستخدام
لإنشاء كائن `AudioBufferSourceNode`، يجب أولاً إنشاء كائن `AudioContext`. بعد ذلك، يمكنك استخدام الدالة `createBufferSource()` لإنشاء المصدر. يجب عليك ربطه بمخرج صوتي (مثل `destination`) باستخدام `connect()`.

### التفاصيل
- **الخصائص**: 
  - `buffer`: يُحدد الـ `AudioBuffer` الذي يتم تشغيله.
  - `loop`: خاصية منطقية تُحدد ما إذا كان يجب تكرار تشغيل الصوت.
  - `loopEnd`: يُحدد نقطة نهاية التكرار.
  - `loopStart`: يُحدد نقطة بداية التكرار.
  
- **الدوال**:
  - `start()`: يبدأ تشغيل الصوت.
  - `stop()`: يوقف تشغيل الصوت.

## أمثلة
### مثال 1: تشغيل صوت بسيط
```javascript
// إنشاء كائن AudioContext
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// تحميل الصوت في AudioBuffer
fetch('path/to/audio/file.mp3')
  .then(response => response.arrayBuffer())
  .then(data => audioContext.decodeAudioData(data))
  .then(buffer => {
    // إنشاء AudioBufferSourceNode
    const source = audioContext.createBufferSource();
    source.buffer = buffer; // تعيين AudioBuffer
    source.connect(audioContext.destination); // ربط بالمخرج
    source.start(0); // بدء التشغيل
  });
```

### مثال 2: تشغيل صوت مع التكرار
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

fetch('path/to/audio/file.mp3')
  .then(response => response.arrayBuffer())
  .then(data => audioContext.decodeAudioData(data))
  .then(buffer => {
    const source = audioContext.createBufferSource();
    source.buffer = buffer;
    source.loop = true; // تفعيل التكرار
    source.connect(audioContext.destination);
    source.start(0);
  });
```

## الشرح
### المشاكل الشائعة
- **عدم تشغيل الصوت**: تأكد من أن المستخدم قد تفاعل مع الصفحة (مثل الضغط على زر) قبل بدء تشغيل الصوت، حيث أن معظم المتصفحات تمنع التشغيل التلقائي للصوت.
- **توقف الصوت بشكل غير متوقع**: تأكد من عدم استدعاء `stop()` قبل انتهاء التشغيل.

### ملاحظات إضافية
- `AudioBufferSourceNode` يمكن استخدامه مرة واحدة فقط. إذا كنت بحاجة لتشغيل نفس الصوت مرة أخرى، يجب عليك إنشاء كائن جديد.
- يُفضل إدارة الموارد بشكل جيد، مثل عدم تحميل ملفات الصوت الكبيرة بشكل متكرر دون الحاجة.

## ملخص جملة واحدة
`AudioBufferSourceNode` هو عنصر قوي في Web Audio API لتشغيل الصوت من بيانات صوتية مخزنة، مع إمكانية التحكم في خصائص التشغيل.