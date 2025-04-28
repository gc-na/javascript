<!--
Meta Description: # NodeList في JavaScript: دليل شامل ## ملخص NodeList هو كائن في JavaScript يمثل مجموعة من العقد (Nodes) في شجرة DOM. يتم استخدامه بشكل شائع عند استرجا...
Meta Keywords: nodelist, javascript, const, العناصر, يمكن
-->

# NodeList في JavaScript: دليل شامل

## ملخص
NodeList هو كائن في JavaScript يمثل مجموعة من العقد (Nodes) في شجرة DOM. يتم استخدامه بشكل شائع عند استرجاع عناصر HTML من الصفحة، وهو مهم لفهم كيفية التعامل مع العناصر في واجهة المستخدم.

## الوثائق
### الغرض
NodeList هو كائن شبيه بالمصفوفة يحتوي على مجموعة من العقد التي تم استرجاعها من مستند HTML. يمكن أن يتضمن هذا الكائن عناصر مثل العناصر، النصوص، والتعليقات. يتم استخدام NodeList بشكل رئيسي مع طرق مثل `document.querySelectorAll()` و `childNodes`.

### الاستخدام
يمكن للمطورين استخدام NodeList لاسترجاع وتعديل العناصر في DOM. على الرغم من أن NodeList يبدو كأنه مصفوفة، إلا أنه ليس مصفوفة حقيقية، مما يعني أنه لا يدعم جميع وظائف المصفوفات مثل `map` و `forEach` بشكل مباشر.

### التفاصيل
- **إنشاء NodeList**: يمكن إنشاء NodeList باستخدام طرق مثل:
  ```javascript
  const nodeList = document.querySelectorAll('div');
  ```
- **الخصائص**: يحتوي NodeList على خاصية `length` التي تعيد عدد العقد الموجودة.
- **العقدة الفردية**: للوصول إلى عقد معينة، يمكن استخدام الفهرس كما يلي:
  ```javascript
  const firstDiv = nodeList[0];
  ```
- **التحويل إلى مصفوفة**: لتحويل NodeList إلى مصفوفة حقيقية، يمكن استخدام `Array.from()` أو نشر المصفوفة:
  ```javascript
  const divArray = Array.from(nodeList);
  ```

## الأمثلة
### مثال 1: استرجاع جميع العناصر
```javascript
const paragraphs = document.querySelectorAll('p');
console.log(paragraphs.length); // عدد عناصر <p>
```

### مثال 2: الوصول إلى عقد معينة
```javascript
const items = document.querySelectorAll('.item');
console.log(items[1]); // الوصول إلى العنصر الثاني
```

### مثال 3: تحويل NodeList إلى مصفوفة
```javascript
const listItems = document.querySelectorAll('li');
const itemsArray = Array.from(listItems);
itemsArray.forEach(item => {
  console.log(item.textContent); // طباعة نص كل عنصر
});
```

## الشرح
### نقاط يجب الانتباه إليها
- **الاختلاف عن المصفوفات**: تذكر أن NodeList ليس مصفوفة حقيقية، لذا لا يمكن استخدام بعض طرق المصفوفات مباشرة عليه.
- **التحيين التلقائي**: إذا تم تغيير DOM بعد استرجاع NodeList، فقد لا يتم تحديث العناصر تلقائيًا (باستثناء `NodeList` الناتج عن `childNodes`).
- **الأداء**: تجنب تكرار استرجاع NodeList في الحلقات، حيث أن ذلك قد يؤثر على الأداء. بدلاً من ذلك، قم بتخزين النتائج في متغير.

## ملخص جملة واحدة
NodeList في JavaScript هو كائن يمثل مجموعة من العقد في شجرة DOM، مما يسهل التعامل مع العناصر في واجهات المستخدم.