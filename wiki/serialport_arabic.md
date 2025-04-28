<!--
Meta Description: # منفذ السلسلة (SerialPort) في جافا سكريبت: دليلك الشامل ## ملخص منفذ السلسلة (SerialPort) هو واجهة برمجة التطبيقات في جافا سكريبت التي تتيح للمطورين ...
Meta Keywords: data, serialport, port, console, السلسلة
-->

# منفذ السلسلة (SerialPort) في جافا سكريبت: دليلك الشامل

## ملخص
منفذ السلسلة (SerialPort) هو واجهة برمجة التطبيقات في جافا سكريبت التي تتيح للمطورين التفاعل مع أجهزة السلسلة المتصلة. يُستخدم بشكل شائع في تطبيقات إنترنت الأشياء (IoT) وتطبيقات التحكم في الأجهزة.

## الوثائق
### الغرض
تسهل مكتبة SerialPort في جافا سكريبت التواصل مع الأجهزة عبر منافذ السلسلة. تتيح لك هذه المكتبة قراءة البيانات من الأجهزة وإرسال الأوامر إليها.

### الاستخدام
لتثبيت المكتبة، يمكنك استخدام npm:
```bash
npm install serialport
```

### التفاصيل
بمجرد تثبيت المكتبة، يمكنك استخدامها كما يلي:

1. **استيراد المكتبة**:
   ```javascript
   const SerialPort = require('serialport');
   ```

2. **إنشاء كائن منفذ السلسلة**:
   ```javascript
   const port = new SerialPort({
     path: '/dev/tty-usbserial1', // استبدل بمسار الجهاز الخاص بك
     baudRate: 9600,              // معدل البود
   });
   ```

3. **فتح المنفذ والاستماع للبيانات**:
   ```javascript
   port.on('open', () => {
     console.log('Port opened');
   });

   port.on('data', (data) => {
     console.log('Data received: ' + data);
   });
   ```

4. **إرسال البيانات**:
   ```javascript
   port.write('Hello from JavaScript!', (err) => {
     if (err) {
       return console.error('Error on write: ', err.message);
     }
     console.log('Message sent');
   });
   ```

## الأمثلة
### مثال أساسي
```javascript
const SerialPort = require('serialport');

const port = new SerialPort({
  path: '/dev/tty-usbserial1',
  baudRate: 9600,
});

port.on('open', () => {
  console.log('Port opened successfully');
});

port.on('data', (data) => {
  console.log(`Received: ${data}`);
});

port.write('Test data', (err) => {
  if (err) {
    console.error('Failed to send data:', err);
  } else {
    console.log('Data sent successfully');
  }
});
```

### قراءة البيانات
```javascript
port.on('data', (data) => {
  console.log(`Received data: ${data.toString()}`);
});
```

## الشرح
### الأخطاء الشائعة
- **عدم فتح المنفذ**: تأكد من أن المنفذ صحيح ومفتوح قبل محاولة قراءة أو كتابة البيانات.
- **معدل البود غير متطابق**: تأكد من أن معدل البود المستخدم في برنامجك يتطابق مع الجهاز المتصل.

### ملاحظات إضافية
- تأكد من وجود الأذونات اللازمة للوصول إلى المنفذ على نظام التشغيل الخاص بك.
- إذا كنت تستخدم أنظمة تشغيل مختلفة، تأكد من استخدام المسار الصحيح للمنفذ (مثل `COM3` على Windows أو `/dev/ttyUSB0` على Linux).

## ملخص بعبارة واحدة
منفذ السلسلة (SerialPort) في جافا سكريبت يتيح التواصل السلس مع الأجهزة المتصلة عبر منافذ السلسلة.