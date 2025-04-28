<!--
Meta Description: # FileList في JavaScript: كل ما تحتاج معرفته ## ملخص FileList هو كائن في JavaScript يمثل مجموعة من كائنات File، ويستخدم بشكل رئيسي في التعامل مع الملف...
Meta Keywords: filelist, input, الملفات, file, كائن
-->

# FileList في JavaScript: كل ما تحتاج معرفته

## ملخص
FileList هو كائن في JavaScript يمثل مجموعة من كائنات File، ويستخدم بشكل رئيسي في التعامل مع الملفات المرفوعة من قبل المستخدم عبر واجهة المستخدم (UI) في متصفحات الويب.

## الوثائق
### الغرض
يستخدم كائن FileList لتخزين مجموعة من الملفات التي يقوم المستخدم بتحميلها من جهازه المحلي. يتم استرجاعه عادةً من عنصر `<input>` من النوع `file`.

### الاستخدام
يتم الوصول إلى كائن FileList عن طريق خاصية `files` في عنصر إدخال الملفات. يمكن أن يحتوي عنصر الإدخال على ملف واحد أو أكثر حسب إعدادات `multiple`.

### التفاصيل
- **النوع**: كائن
- **التركيب**: `FileList` يحتوي على قائمة من كائنات `File`.
- **الخصائص**:
  - `length`: عدد الملفات في الكائن.
- **الطرق**: لا يحتوي FileList على طرق محددة، ولكن يمكن الوصول إلى كائنات File باستخدام الفهرس.

## الأمثلة
### مثال 1: تحميل ملف واحد
```html
<input type="file" id="fileInput">
<script>
  const input = document.getElementById('fileInput');
  input.addEventListener('change', function() {
    const fileList = input.files;
    console.log(fileList[0]); // عرض أول ملف
  });
</script>
```

### مثال 2: تحميل ملفات متعددة
```html
<input type="file" id="fileInput" multiple>
<script>
  const input = document.getElementById('fileInput');
  input.addEventListener('change', function() {
    const fileList = input.files;
    for (let i = 0; i < fileList.length; i++) {
      console.log(fileList[i].name); // عرض أسماء جميع الملفات
    }
  });
</script>
```

## الشرح
### العقبات الشائعة
- **عدم التحقق من نوع الملف**: يجب التأكد من أن الملفات التي يتم تحميلها هي من النوع المتوقع (مثل الصور أو المستندات) لتجنب الأخطاء.
- **الحد من حجم الملف**: يجب أن يتم التحقق من حجم الملفات قبل التحميل لتجنب تحميل ملفات كبيرة جداً.
- **عدم دعم المتصفح**: تأكد من أن المستخدم يستخدم متصفحًا يدعم واجهة برمجة التطبيقات الخاصة بـ FileList (مثل Chrome، Firefox، Safari).

## ملخص جملة واحدة
يعتبر FileList كائنًا مفيدًا في JavaScript لتمثيل مجموعة من الملفات المرفوعة من قبل المستخدم، مما يسهل التعامل معها في تطبيقات الويب.