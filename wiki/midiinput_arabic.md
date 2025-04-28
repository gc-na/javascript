<!--
Meta Description: # MIDIInput في JavaScript: التعامل مع إدخالات MIDI ## الملخص MIDIInput هو واجهة ضمن واجهة برمجة التطبيقات Web MIDI التي تسمح لمطوري JavaScript بالتفاع...
Meta Keywords: midi, midiinput, message, javascript, inputs
-->

# MIDIInput في JavaScript: التعامل مع إدخالات MIDI

## الملخص
MIDIInput هو واجهة ضمن واجهة برمجة التطبيقات Web MIDI التي تسمح لمطوري JavaScript بالتفاعل مع أجهزة MIDI، مما يتيح لهم استلام بيانات MIDI من الأجهزة المتصلة.

## الوثائق
### الغرض
MIDIInput تهدف إلى تمكين تطبيقات الويب من استيعاب بيانات MIDI من أجهزة MIDI مثل لوحات المفاتيح، الآلات الموسيقية، أو أجهزة التحكم الأخرى. من خلال هذه الواجهة، يمكن للمطورين إنشاء تطبيقات موسيقية تفاعلية، أو أدوات للتأليف الموسيقي، أو حتى ألعاب تعتمد على إدخالات MIDI.

### الاستخدام
لتتمكن من استخدام MIDIInput في JavaScript، يجب أولاً التأكد من أن المتصفح يدعم واجهة برمجة تطبيقات Web MIDI. يمكنك استخدام `navigator.requestMIDIAccess()` للحصول على الوصول إلى الأجهزة MIDI المتصلة. بعد ذلك، يتم استخدام كائنات MIDIInput للتعامل مع البيانات.

### التفاصيل
- **MIDIInput**: تمثل جهاز MIDI واحد يمكنه إرسال بيانات MIDI.
- **تحديد الوظائف**: تحتوي واجهة MIDIInput على دالة `onmidimessage` التي يمكن تعيينها للاستجابة عند استلام رسالة MIDI.
- **البيانات**: الرسائل التي يتم استقبالها يمكن أن تكون من أنواع مختلفة مثل Note On, Note Off, Control Change وغيرها.

## الأمثلة
### مثال بسيط لقراءة إدخال MIDI
```javascript
navigator.requestMIDIAccess().then((midiAccess) => {
    const inputs = midiAccess.inputs;
    inputs.forEach((input) => {
        input.onmidimessage = (message) => {
            console.log(`Received message: ${message.data}`);
        };
    });
});
```

### مثال على التعامل مع رسالة Note On
```javascript
navigator.requestMIDIAccess().then((midiAccess) => {
    const inputs = midiAccess.inputs;
    inputs.forEach((input) => {
        input.onmidimessage = (message) => {
            if (message.data[0] === 144) { // Note On message
                console.log(`Note On: ${message.data[1]} Velocity: ${message.data[2]}`);
            }
        };
    });
});
```

## الشرح
- **التوافق**: تأكد من أن المتصفح يدعم Web MIDI. المتصفحات الحديثة مثل Chrome وOpera تدعم هذه الواجهة، بينما قد لا تدعمها متصفحات أخرى.
- **التعامل مع الأجهزة المتعددة**: إذا كان لديك أكثر من جهاز MIDI متصل، تأكد من تحديد الجهاز الصحيح عند التعامل مع إدخالات MIDI.
- **الأمان**: قد تتطلب بعض المتصفحات إذن المستخدم لاستخدام MIDI. تأكد من التعامل مع هذا بشكل صحيح.

## ملخص بجملة واحدة
MIDIInput في JavaScript يمكّن المطورين من استقبال ومعالجة بيانات MIDI من الأجهزة المتصلة بسهولة وفعالية.