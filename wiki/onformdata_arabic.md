<!--
Meta Description: # onformdata في JavaScript: دليلك الشامل ## ملخص `onformdata` هي حدث يتم استخدامه في JavaScript للتعامل مع بيانات نموذج يتم جمعها عند إرسال النموذج. ي...
Meta Keywords: formdata, onformdata, form, البيانات, بيانات
-->

# onformdata في JavaScript: دليلك الشامل

## ملخص
`onformdata` هي حدث يتم استخدامه في JavaScript للتعامل مع بيانات نموذج يتم جمعها عند إرسال النموذج. يوفر هذا الحدث وسيلة للتفاعل مع البيانات قبل إرسالها، مما يسمح للمطورين بمعالجة البيانات أو تعديلها حسب الحاجة.

## الوثائق
### الغرض
يُستخدم حدث `onformdata` لتوفير وسيلة للمطورين للتفاعل مع بيانات النموذج في JavaScript. يمكن استخدامه لتعديل البيانات المرسلة، وإضافة معلومات إضافية، أو حتى منع عملية الإرسال بناءً على شروط معينة.

### الاستخدام
يمكن استخدام `onformdata` مع نماذج HTML لتوفير تحكم دقيق في البيانات المرسلة. يتم تفعيله عند إنشاء كائن `FormData` من عنصر النموذج، وعادةً ما يُستخدم في سياق التعامل مع الأحداث مثل `submit`.

### التفاصيل
- **نوع الحدث**: `onformdata` هو حدث مخصص يتم تفعيله عند إنشاء كائن FormData.
- **الحدث**: يتم تفعيله تلقائيًا عند استدعاء `new FormData(formElement)`.
- **البيانات**: يمكن تعديل بيانات النموذج أو إضافة بيانات جديدة باستخدام كائن FormData.

## الأمثلة
### مثال 1: استخدام onformdata مع نموذج بسيط
```html
<form id="myForm">
  <input type="text" name="username" value="JohnDoe">
  <input type="submit" value="إرسال">
</form>

<script>
  const form = document.getElementById('myForm');
  
  form.addEventListener('submit', function(event) {
    const formData = new FormData(form);
    
    // تفعيل حدث onformdata
    formData.onformdata = function() {
      console.log('تم إنشاء كائن FormData:', formData);
    };
    
    formData.onformdata();
  });
</script>
```

### مثال 2: إضافة بيانات إضافية إلى FormData
```html
<form id="myForm">
  <input type="text" name="username" value="JohnDoe">
  <input type="submit" value="إرسال">
</form>

<script>
  const form = document.getElementById('myForm');
  
  form.addEventListener('submit', function(event) {
    const formData = new FormData(form);
    
    // إضافة بيانات إضافية
    formData.append('age', '30');
    
    console.log('البيانات المرسلة:', Array.from(formData.entries()));
  });
</script>
```

## الشرح
- **المزالق الشائعة**: يمكن أن يكون هناك لبس بين `onformdata` وأحداث أخرى مثل `submit`. يجب التأكد من استخدام `onformdata` بعد إنشاء كائن FormData.
- **ملاحظات إضافية**: تأكد من أن البيانات التي تضيفها إلى FormData تتوافق مع متطلبات النموذج. إذا كان هناك بيانات مفقودة، قد يؤدي ذلك إلى أخطاء في معالجة البيانات.

## ملخص جملة واحدة
`onformdata` هو حدث في JavaScript يتيح لك التفاعل مع بيانات النموذج قبل إرسالها، مما يوفر تحكمًا كاملاً في البيانات المرسلة.