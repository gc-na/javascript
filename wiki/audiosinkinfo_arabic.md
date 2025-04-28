<!--
Meta Description: # معلومات عن AudioSinkInfo في JavaScript ## ملخص AudioSinkInfo هو كائن يستخدم في JavaScript لتعريف معلومات حول وجهات إخراج الصوت المتاحة، مما يتيح للم...
Meta Keywords: الصوت, معلومات, audiosinkinfo, الأجهزة, javascript
-->

# معلومات عن AudioSinkInfo في JavaScript

## ملخص
AudioSinkInfo هو كائن يستخدم في JavaScript لتعريف معلومات حول وجهات إخراج الصوت المتاحة، مما يتيح للمطورين التحكم في كيفية تشغيل الصوت على الأجهزة المختلفة.

## الوثائق
### الغرض
يهدف AudioSinkInfo إلى تقديم معلومات تفصيلية حول وجهات إخراج الصوت، مثل الأجهزة الصوتية المتصلة، وأنواع الملفات المدعومة، وخصائص الصوت.

### الاستخدام
يمكن استخدام AudioSinkInfo في تطبيقات الويب التي تحتاج إلى إدارة تدفقات الصوت، مثل تطبيقات الموسيقى أو الألعاب. يتم استخدام هذا الكائن في سياق واجهة برمجة التطبيقات (API) الخاصة بالصوت.

### التفاصيل
- **الخصائص**:
  - **deviceId**: معرف الجهاز الصوتي.
  - **kind**: نوع الوجهة (مثل "audiooutput").
  - **label**: اسم الجهاز الصوتي المعروض للمستخدم.

- **طرق الاستخدام**:
  يمكن الوصول إلى معلومات AudioSinkInfo من خلال استدعاء API الصوت. يجب على المطورين التأكد من أن لديهم الأذونات اللازمة للوصول إلى الأجهزة الصوتية.

## أمثلة
### المثال 1: استرداد معلومات وجهة الصوت
```javascript
navigator.mediaDevices.enumerateDevices()
  .then(devices => {
    devices.forEach(device => {
      if (device.kind === 'audiooutput') {
        console.log(`Device ID: ${device.deviceId}, Label: ${device.label}`);
      }
    });
  })
  .catch(err => {
    console.error(`Error: ${err}`);
  });
```

### المثال 2: تغيير وجهة الإخراج
```javascript
const audioElement = document.querySelector('audio');
const audioSinkId = 'معرف_الجهاز_المرغوب_فيه'; // استبدل بمعرف الجهاز الفعلي
audioElement.setSinkId(audioSinkId)
  .then(() => {
    console.log(`Audio output set to ${audioSinkId}`);
  })
  .catch(err => {
    console.error(`Error setting audio output: ${err}`);
  });
```

## الشرح
### النقاط الشائعة
- تأكد من أن لديك الأذونات المناسبة للوصول إلى الأجهزة الصوتية، حيث يمكن أن يكون هناك قيود على بعض المتصفحات.
- قد لا تظهر جميع الأجهزة في قائمة الوجهات المتاحة، خاصةً إذا لم يتم توصيلها أو تم تعطيلها.
- عند تغيير الوجهة، تأكد من التعامل مع الأخطاء بشكل صحيح، مثل الأجهزة غير المتوافقة.

## ملخص جملة واحدة
AudioSinkInfo في JavaScript يوفر معلومات مهمة حول وجهات إخراج الصوت، مما يمكّن المطورين من تحسين تجربة الصوت في تطبيقاتهم.