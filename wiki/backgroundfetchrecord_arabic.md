<!--
Meta Description: # سجل التحميل الخلفي (BackgroundFetchRecord) في جافا سكريبت ## الملخص سجل التحميل الخلفي (BackgroundFetchRecord) هو واجهة برمجة تطبيقات (API) في جافا ...
Meta Keywords: التحميل, backgroundfetchrecord, التي, registration, fetch
-->

# سجل التحميل الخلفي (BackgroundFetchRecord) في جافا سكريبت

## الملخص
سجل التحميل الخلفي (BackgroundFetchRecord) هو واجهة برمجة تطبيقات (API) في جافا سكريبت مصممة لتسهيل تحميل الموارد بشكل غير متزامن في الخلفية، مما يسمح للتطبيقات بتحسين تجربة المستخدم من خلال تحميل البيانات في الخلفية.

## الوثائق
### الغرض
تتيح واجهة BackgroundFetchRecord للمطورين التعامل مع عمليات التحميل التي تتم في الخلفية، حيث يمكن استخدام هذه الواجهة لتتبع حالة التحميل، وإدارة الموارد التي يتم تحميلها، والتفاعل معها بطريقة مرنة.

### الاستخدام
يتم استخدام BackgroundFetchRecord كجزء من واجهة Background Fetch API، وتوفر معلومات حول التحميلات الجارية في الخلفية. يمكن أن تحتوي هذه الواجهة على خصائص مثل `id`, `uploadTotal`, `uploadTransferred`, `downloadTotal`, و `downloadTransferred`.

### التفاصيل
- **الخصائص**:
  - `id`: معرف فريد لجلسة التحميل الخلفي.
  - `uploadTotal`: إجمالي البيانات التي يجب تحميلها.
  - `uploadTransferred`: البيانات التي تم تحميلها بالفعل.
  - `downloadTotal`: إجمالي البيانات التي يجب تنزيلها.
  - `downloadTransferred`: البيانات التي تم تنزيلها بالفعل.
  
- **الوظائف**: يمكن استخدام `BackgroundFetchRecord` لمراقبة تقدم التحميل، واسترجاع المعلومات المتعلقة بالموارد، وإدارة الأخطاء التي قد تحدث أثناء عملية التحميل.

## الأمثلة
### مثال بسيط لاستخدام BackgroundFetchRecord
```javascript
if ('backgroundFetch' in self) {
  const registration = await backgroundFetch.fetch('my-fetch', ['/example.jpg'], {
    title: 'Downloading Example',
    icons: [{ src: '/icon.png', sizes: '192x192', type: 'image/png' }],
  });

  registration.addEventListener('progress', () => {
    console.log(`Downloaded ${registration.downloadTransferred} of ${registration.downloadTotal} bytes.`);
  });
}
```

### مثال على التحقق من حالة التحميل
```javascript
async function checkBackgroundFetch() {
  const registrations = await backgroundFetch.get('my-fetch');
  registrations.forEach(registration => {
    console.log(`Fetch ID: ${registration.id}`);
    console.log(`Progress: ${registration.downloadTransferred}/${registration.downloadTotal}`);
  });
}
```

## الشرح
### الأخطاء الشائعة
- **عدم دعم API**: يجب التأكد من أن المتصفح يدعم Background Fetch API قبل استخدامها.
- **إدارة الحالة**: يجب الانتباه إلى إدارة حالات التحميل بشكل صحيح، خاصةً عند التعامل مع التحميلات الكبيرة أو المترابطة.
- **التعامل مع الأخطاء**: قد تحدث أخطاء أثناء عملية التحميل، لذلك من المهم تضمين آلية للتعامل مع الأخطاء.

### ملاحظات إضافية
- BackgroundFetchRecord مفيدة بشكل خاص في التطبيقات التي تتطلب تحميل محتوى كبير مثل الصور أو الملفات.
- يجب مراعاة الاستخدام النشط لهذه الواجهة لتجنب استهلاك غير ضروري للموارد.

## ملخص من جملة واحدة
سجل التحميل الخلفي (BackgroundFetchRecord) في جافا سكريبت هو واجهة مفيدة لتحسين تحميل الموارد بشكل غير متزامن في الخلفية، مما يعزز تجربة المستخدم.