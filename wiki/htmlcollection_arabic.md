<!--
Meta Description: # HTMLCollection في جافا سكريبت: كل ما تحتاج معرفته ## ملخص HTMLCollection هو كائن في جافا سكريبت يمثل مجموعة من عناصر HTML، ويتم استخدامه بشكل رئيسي ...
Meta Keywords: htmlcollection, إلى, العناصر, استخدام, مجموعة
-->

# HTMLCollection في جافا سكريبت: كل ما تحتاج معرفته

## ملخص
HTMLCollection هو كائن في جافا سكريبت يمثل مجموعة من عناصر HTML، ويتم استخدامه بشكل رئيسي للتفاعل مع عناصر الصفحة في مستندات HTML.

## الوثائق
### الغرض
HTMLCollection هو نوع من الكائنات الحية (live collection) في جافا سكريبت، يُستخدم لتمثيل مجموعة من العناصر التي تم العثور عليها في مستند HTML. يتم تحديث HTMLCollection تلقائيًا عندما يتم تغيير DOM، مما يجعله مثاليًا للتفاعل مع العناصر الديناميكية في صفحات الويب.

### الاستخدام
يمكن الوصول إلى HTMLCollection من خلال مجموعة من الطرق، بما في ذلك:
- **document.getElementsByTagName()**: لاسترجاع كل العناصر التي تحمل علامة معينة.
- **document.getElementsByClassName()**: لاسترجاع كل العناصر التي تحمل اسم فئة معين.
- **document.getElementsByName()**: لاسترجاع جميع العناصر التي تحمل اسم معين في خاصية `name`.

تدعم HTMLCollection الطرق الأساسية مثل `length` للوصول إلى عدد العناصر، و `item()` للوصول إلى عنصر معين باستخدام الفهرسة.

### تفاصيل
- **طبيعة الكائن**: HTMLCollection هو كائن حي (live), مما يعني أنه يتغير تلقائيًا إذا تم تعديل DOM.
- **الفهرسة**: يمكن الوصول إلى عناصر HTMLCollection باستخدام الفهرسة (indexing) بدءًا من 0.
- **عدم التكرار**: يمكن أن تحتوي HTMLCollection على عناصر مكررة، لذلك يجب أن تكون حذرًا عند استخدام هذه المجموعة.

## أمثلة
### مثال 1: استخدام getElementsByTagName
```javascript
let paragraphs = document.getElementsByTagName('p');
console.log(paragraphs.length); // عدد الفقرات في المستند
```

### مثال 2: استخدام getElementsByClassName
```javascript
let items = document.getElementsByClassName('item');
console.log(items[0]); // الوصول إلى أول عنصر في المجموعة
```

### مثال 3: استخدام getElementsByName
```javascript
let radios = document.getElementsByName('gender');
console.log(radios.length); // عدد عناصر الاختيار في مجموعة معينة
```

## الشرح
### الأخطاء الشائعة
- **عدم فهم طبيعة الكائن الحي**: قد يعتقد المطورون أن HTMLCollection ثابتة، ولكنها تتغير تلقائيًا مع تغييرات DOM، مما قد يؤدي إلى ارتباك.
- **استخدام الفهرسة بشكل غير صحيح**: تذكر أن الفهرسة تبدأ من 0، لذا تأكد من عدم تجاوز الحدود عند الوصول إلى العناصر.

### ملاحظات إضافية
- HTMLCollection ليست مصفوفة حقيقية، لذا لا يمكنك استخدام جميع طرق المصفوفات معها. إذا كنت بحاجة إلى استخدام طرق المصفوفة، يمكنك تحويلها إلى مصفوفة باستخدام `Array.from()`.
- يُفضل استخدام `querySelectorAll()` إذا كنت بحاجة إلى مجموعة ثابتة من العناصر، حيث تعيد NodeList بدلًا من HTMLCollection.

## ملخص في جملة واحدة
HTMLCollection هو كائن في جافا سكريبت يمثل مجموعة حية من عناصر HTML، مما يسهل التفاعل مع مستندات الويب.