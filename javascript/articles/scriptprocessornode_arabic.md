<!--
Meta Description: # Node معالجة النصوص (ScriptProcessorNode) في JavaScript: دليل شامل ## ملخص تُعتبر Node معالجة النصوص (ScriptProcessorNode) واحدة من المكونات الأساسية...
Meta Keywords: معالجة, scriptprocessornode, الصوت, audiocontext, const
-->

# Node معالجة النصوص (ScriptProcessorNode) في JavaScript: دليل شامل

## ملخص
تُعتبر Node معالجة النصوص (ScriptProcessorNode) واحدة من المكونات الأساسية في واجهة برمجة تطبيقات الويب للصوت (Web Audio API) والتي تسمح بتخصيص معالجة الصوت في المتصفح.

## الوثائق
تُستخدم Node معالجة النصوص (ScriptProcessorNode) لإنشاء وحدة معالجة صوتية مخصصة. تتيح هذه الوحدة للمطورين معالجة البيانات الصوتية التي تتدفق عبر النظام بشكل تفاعلي. يمكن استخدامها لإجراء تعديلات على الصوت، مثل إضافة تأثيرات أو تطبيق خوارزميات معينة على البيانات الصوتية.

### الغرض
- **معالجة الصوت:** تسمح للمطورين بإنشاء معالجة صوتية مخصصة.
- **تخصيص الأداء:** إمكانية التحكم الكامل في كيفية معالجة البيانات الصوتية.

### الاستخدام
لإنشاء Node معالجة النصوص، يجب أولاً إنشاء كائن من نوع AudioContext، ثم استخدام دالة `createScriptProcessor`:

```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const scriptProcessorNode = audioContext.createScriptProcessor(bufferSize, numberOfInputChannels, numberOfOutputChannels);
```

حيث:
- **bufferSize:** حجم البيانات الصوتية المراد معالجتها.
- **numberOfInputChannels:** عدد قنوات الإدخال.
- **numberOfOutputChannels:** عدد قنوات الإخراج.

## الأمثلة
### مثال بسيط لإنشاء Node معالجة النصوص
```javascript
const audioContext = new (window.AudioContext || window.webkitAudioContext)();
const scriptProcessorNode = audioContext.createScriptProcessor(4096, 1, 1);

scriptProcessorNode.onaudioprocess = function(event) {
    const inputBuffer = event.inputBuffer.getChannelData(0);
    const outputBuffer = event.outputBuffer.getChannelData(0);

    // معالجة البيانات الصوتية
    for (let i = 0; i < inputBuffer.length; i++) {
        outputBuffer[i] = inputBuffer[i]; // تمرير الصوت بدون تغيير
    }
};

scriptProcessorNode.connect(audioContext.destination);
```

### مثال لتطبيق تأثيرات على الصوت
```javascript
scriptProcessorNode.onaudioprocess = function(event) {
    const inputBuffer = event.inputBuffer.getChannelData(0);
    const outputBuffer = event.outputBuffer.getChannelData(0);

    for (let i = 0; i < inputBuffer.length; i++) {
        outputBuffer[i] = inputBuffer[i] * 0.5; // تخفيض مستوى الصوت
    }
};
```

## الشرح
### النقاط الشائعة
- **توقف دعم ScriptProcessorNode:** لاحظ أن Node معالجة النصوص (ScriptProcessorNode) قد تم استبداله في بعض الاستخدامات بـ AudioWorklet، والذي يوفر أداءً أفضل وميزات أكثر تقدمًا.
- **أداء المعالجة:** يجب تجنب معالجة البيانات الصوتية بشكل معقد داخل دالة `onaudioprocess`، حيث يمكن أن يؤدي ذلك إلى تأخير في الصوت. يُفضل الحفاظ على العمليات بسيطة لتحسين الأداء.
- **عدد القنوات:** يجب أن يتطابق عدد قنوات الإدخال والإخراج مع إعدادات المصدر الصوتي لتحقيق نتائج صحيحة.

## ملخص جملة واحدة
Node معالجة النصوص (ScriptProcessorNode) هي وحدة في واجهة برمجة تطبيقات الويب للصوت تُستخدم لمعالجة الصوت بشكل مخصص في تطبيقات JavaScript.