<!--
Meta Description: # حدث MIDIMessageEvent في جافاسكريبت: كل ما تحتاج معرفته ## الملخص حدث `MIDIMessageEvent` في جافاسكريبت يُستخدم للإشارة إلى رسالة MIDI يتم تلقيها عبر ...
Meta Keywords: midi, function, inputs, event, note
-->

# حدث MIDIMessageEvent في جافاسكريبت: كل ما تحتاج معرفته

## الملخص
حدث `MIDIMessageEvent` في جافاسكريبت يُستخدم للإشارة إلى رسالة MIDI يتم تلقيها عبر واجهة Web MIDI API. يوفر هذا الحدث معلومات حول الرسالة، مما يتيح للمطورين التفاعل مع أجهزة MIDI بسهولة.

## الوثائق
### الغرض
تم تصميم `MIDIMessageEvent` لتمكين تطبيقات الويب من تلقي رسائل MIDI من أجهزة MIDI، مما يسمح بتطوير تطبيقات موسيقية وتفاعلية.

### الاستخدام
يتم استخدام `MIDIMessageEvent` في سياق واجهة `MIDIInput`، حيث يمكن للمطورين إضافة مستمعين للأحداث للتفاعل مع الرسائل الواردة.

### التفاصيل
- **الخصائص**:
  - `data`: مصفوفة من القيم العددية تمثل بيانات الرسالة MIDI.
  - `receivedTime`: الوقت الذي تم فيه تلقي الرسالة، بالتوقيت الزمني.
  
- **مثال على استخدام `MIDIMessageEvent`**:
  ```javascript
  navigator.requestMIDIAccess().then(function(midiAccess) {
      const inputs = midiAccess.inputs;
      inputs.forEach(function(input) {
          input.onmidimessage = function(event) {
              console.log(event.data); // البيانات الواردة من جهاز MIDI
              console.log(event.receivedTime); // الوقت المستلم
          };
      });
  });
  ```

## الأمثلة
### مثال أساسي
```javascript
navigator.requestMIDIAccess().then(function(midiAccess) {
    const inputs = midiAccess.inputs;
    inputs.forEach(function(input) {
        input.onmidimessage = function(event) {
            console.log("Received MIDI message:", event.data);
        };
    });
});
```

### إدارة البيانات MIDI
```javascript
navigator.requestMIDIAccess().then(function(midiAccess) {
    const inputs = midiAccess.inputs;
    inputs.forEach(function(input) {
        input.onmidimessage = function(event) {
            const [status, note, velocity] = event.data;
            // معالجة الرسالة MIDI
            if (status === 144 && velocity > 0) { // Note On
                console.log(`Note On: ${note} with velocity ${velocity}`);
            } else if (status === 128 || (status === 144 && velocity === 0)) { // Note Off
                console.log(`Note Off: ${note}`);
            }
        };
    });
});
```

## الشرح
### الأخطاء الشائعة
- **عدم دعم المتصفح**: تأكد من أن المتصفح يدعم واجهة Web MIDI API، حيث قد لا تعمل في بعض البيئات.
- **إهمال معالجة الأخطاء**: من المهم إضافة معالجة الأخطاء عند طلب الوصول إلى MIDI لضمان تجربة مستخدم سلسة.

### ملاحظات إضافية
- قد يتطلب استخدام واجهة Web MIDI API إذن المستخدم، لذا تأكد من معالجة أي سيناريوهات تتعلق بالرفض.

## ملخص من جملة واحدة
يتيح حدث `MIDIMessageEvent` في جافاسكريبت للمطورين تلقي رسائل MIDI من أجهزة MIDI، مما يسهل تطوير تطبيقات موسيقية تفاعلية.