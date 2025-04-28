<!--
Meta Description: # استخدام دالة fetch في JavaScript: كل ما تحتاج لمعرفته ## الملخص دالة `fetch` في JavaScript هي واجهة برمجة تطبيقات (API) تستخدم لإجراء طلبات الشبكة ب...
Meta Keywords: fetch, الطلب, error, دالة, response
-->

# استخدام دالة fetch في JavaScript: كل ما تحتاج لمعرفته

## الملخص
دالة `fetch` في JavaScript هي واجهة برمجة تطبيقات (API) تستخدم لإجراء طلبات الشبكة بطريقة سهلة ومرنة، مما يسمح بتبادل البيانات بين العميل والخادم.

## الوثائق
### الغرض
تستخدم دالة `fetch` لجلب الموارد من الشبكة باستخدام وعود (Promises)، مما يجعل من السهل التعامل مع الطلبات غير المتزامنة.

### الاستخدام
لإجراء طلب باستخدام دالة `fetch`، يمكنك استدعاءها مع عنوان URL كمعامل أول، ويمكنك أيضًا تمرير خيارات إضافية ككائن في المعامل الثاني.

#### الصيغة الأساسية
```javascript
fetch(url, options)
```

- `url`: عنوان المورد الذي ترغب في الوصول إليه.
- `options` (اختياري): كائن يحتوي على إعدادات مثل الطريقة (GET، POST، وغيرها)، ورؤوس الطلب، وجسم الطلب، وغيرها من الإعدادات.

### الخيارات الشائعة
- **method**: لتحديد نوع الطلب (GET، POST، PUT، DELETE).
- **headers**: لتحديد رؤوس الطلب مثل نوع المحتوى.
- **body**: لتحديد جسم الطلب (يجب أن يكون سلسلة نصية في حال كانت طريقة POST).

## الأمثلة
### مثال 1: إجراء طلب GET
```javascript
fetch('https://api.example.com/data')
  .then(response => {
    if (!response.ok) {
      throw new Error('Network response was not ok');
    }
    return response.json();
  })
  .then(data => console.log(data))
  .catch(error => console.error('There was a problem with the fetch operation:', error));
```

### مثال 2: إجراء طلب POST
```javascript
fetch('https://api.example.com/data', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({ name: 'John', age: 30 })
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

## الشرح
### النقاط الشائعة والأخطاء
- **التعامل مع الأخطاء**: من الضروري التحقق من `response.ok` للتأكد من أن الطلب تم بنجاح. إذا كان هناك خطأ، يجب التعامل معه بشكل مناسب.
- **رؤوس الطلب**: تأكد من تحديد رؤوس الطلب الصحيحة، خاصة عند إرسال بيانات JSON.
- **الاستجابة**: يجب تحويل الاستجابة إلى صيغة مناسبة (مثل JSON) قبل استخدامها.

### ملاحظات إضافية
- دالة `fetch` لا تدعم طلبات CORS بشكل افتراضي، لذا تأكد من إعداد الخادم بشكل صحيح للسماح بذلك.
- يمكن أن تكون دالة `fetch` غير متوافقة مع بعض المتصفحات القديمة، لذا تأكد من التحقق من التوافق.

## ملخص جملة واحدة
دالة `fetch` في JavaScript تتيح لك إجراء طلبات الشبكة بسهولة باستخدام واجهة برمجة التطبيقات الحديثة، مما يسهل التعامل مع البيانات غير المتزامنة.