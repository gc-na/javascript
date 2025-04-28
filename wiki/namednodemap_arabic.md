<!--
Meta Description: # NamedNodeMap في JavaScript: فهم الاستخدامات والوظائف ## ملخص NamedNodeMap هو كائن في JavaScript يُستخدم لتمثيل مجموعة من الخصائص (العناصر) المرتبطة ...
Meta Keywords: attributes, namednodemap, element, javascript, إلى
-->

# NamedNodeMap في JavaScript: فهم الاستخدامات والوظائف

## ملخص
NamedNodeMap هو كائن في JavaScript يُستخدم لتمثيل مجموعة من الخصائص (العناصر) المرتبطة بعقدة معينة في نموذج كائن الوثيقة (DOM). يمثل هذا الكائن قائمة من العقد، حيث تسمح بالوصول إلى العناصر من خلال أسماءها.

## الوثائق
### الغرض
NamedNodeMap يُستخدم بشكل أساسي للتعامل مع سمات (Attributes) عنصر في DOM. يمكن الوصول إلى السمات بواسطة اسمها، مما يسهل عملية القراءة والتعديل.

### الاستخدام
يتم الحصول على NamedNodeMap من خلال استدعاء `attributes` من عنصر HTML. على سبيل المثال:

```javascript
const element = document.getElementById('myElement');
const attributes = element.attributes;
```

### التفاصيل
- **الخصائص**: يمثل NamedNodeMap مجموعة من كائنات Node، حيث يتيح لك التعامل مع السمات كما لو كانت مصفوفة من العناصر.
- **الطرق**: يمكنك استخدام الطرق مثل `getNamedItem(name)` للحصول على سمة معينة، أو `item(index)` للوصول إلى سمة بناءً على موقعها.
- **الطول**: خاصية `length` تعطي عدد السمات الموجودة في NamedNodeMap.

## أمثلة
### مثال 1: الوصول إلى السمات
```javascript
const element = document.createElement('div');
element.setAttribute('id', 'myDiv');
element.setAttribute('class', 'myClass');

const attributes = element.attributes;

for (let i = 0; i < attributes.length; i++) {
    console.log(attributes[i].name + ': ' + attributes[i].value);
}
```

### مثال 2: استخدام getNamedItem
```javascript
const element = document.getElementById('myElement');
const attr = element.attributes.getNamedItem('class');
console.log(attr.value); // طباعة قيمة السمة class
```

## الشرح
### العثرات الشائعة
- **عدم وجود سمات**: إذا حاولت الوصول إلى سمة غير موجودة، سيعيد `getNamedItem` قيمة `null`.
- **التكرار**: NamedNodeMap ليس مصفوفة حقيقية، لذا لا يمكنك استخدام دوال المصفوفة مثل `forEach` مباشرة. يجب استخدام حلقات `for` التقليدية.
- **تغيير السمات**: إذا قمت بتغيير سمة من خلال NamedNodeMap، سيتم تحديث العنصر في DOM. ولكن، تأكد من أن التغييرات تعكس ما تريده بالضبط.

## ملخص جملة واحدة
NamedNodeMap في JavaScript هو كائن يمكّنك من الوصول إلى وإدارة سمات عناصر DOM بطريقة سهلة وفعالة.