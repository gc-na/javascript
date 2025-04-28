<!--
Meta Description: # DOMStringMap في JavaScript: دليل شامل ## الملخص تعتبر `DOMStringMap` واجهة في JavaScript تستخدم لتخزين البيانات المخصصة المرتبطة بالعناصر في نموذج ك...
Meta Keywords: domstringmap, element, data, dataset, البيانات
-->

# DOMStringMap في JavaScript: دليل شامل

## الملخص
تعتبر `DOMStringMap` واجهة في JavaScript تستخدم لتخزين البيانات المخصصة المرتبطة بالعناصر في نموذج كائن المستند (DOM). تسهل هذه الواجهة إدارة البيانات المخصصة بشكل فعال.

## الوثائق
### الغرض
`DOMStringMap` هو كائن يستخدم لتخزين أزواج القيم المفتاحية، حيث المفتاح هو اسم السمة المخصصة التي تبدأ بـ `data-`، والقيمة هي القيمة المرتبطة بهذا المفتاح. يسهل ذلك على المطورين إضافة بيانات إضافية للعناصر دون الحاجة لتعديل الهيكل الأساسي للـ HTML.

### الاستخدام
يمكن الوصول إلى `DOMStringMap` من خلال خاصية `dataset` لعناصر الـ HTML. يتم استخدامه بشكل شائع لتخزين معلومات إضافية يتم استخدامها بواسطة جافا سكريبت، حيث يمكن للمطورين الوصول إليها وتعديلها بسهولة.

### التفاصيل
- يتم إنشاء خصائص `DOMStringMap` تلقائيًا عند استخدام سمات `data-` في العناصر.
- كل خاصية في `DOMStringMap` يتم تحويلها إلى صيغة camelCase.
- القيم تكون دائمًا عبارة عن سلسلة نصية، لذا يجب تحويل الأنواع الأخرى إذا لزم الأمر.

## الأمثلة
### مثال 1: الوصول إلى البيانات
```html
<div id="myElement" data-user-id="123" data-user-name="Ali"></div>

<script>
    const element = document.getElementById('myElement');
    console.log(element.dataset.userId); // 123
    console.log(element.dataset.userName); // Ali
</script>
```

### مثال 2: تعديل البيانات
```html
<div id="myElement" data-user-id="123"></div>

<script>
    const element = document.getElementById('myElement');
    element.dataset.userId = '456';
    console.log(element.dataset.userId); // 456
</script>
```

### مثال 3: إضافة سمات جديدة
```html
<div id="myElement"></div>

<script>
    const element = document.getElementById('myElement');
    element.dataset.newAttribute = 'New Value';
    console.log(element.dataset.newAttribute); // New Value
</script>
```

## الشرح
### الأخطاء الشائعة
- **عدم استخدام prefix `data-`**: يجب أن تبدأ أسماء السمات المخصصة بـ `data-` ليتم التعرف عليها كخصائص في `DOMStringMap`.
- **تجاهل صيغة camelCase**: يجب تذكر تحويل أسماء السمات إلى صيغة camelCase عند الوصول إليها في JavaScript.
- **فهم القيم كنصوص**: كل القيم في `DOMStringMap` تكون نصوصًا، لذلك يجب الحذر عند التعامل مع الأنواع الأخرى مثل الأعداد.

## ملخص جملة واحدة
`DOMStringMap` هو كائن في JavaScript يستخدم لتخزين البيانات المخصصة المرتبطة بالعناصر في الـ DOM، مما يسهل إدارة هذه البيانات بشكل فعال.