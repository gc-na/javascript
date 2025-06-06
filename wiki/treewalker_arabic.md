<!--
Meta Description: # شجرة العبور (TreeWalker) في JavaScript: دليلك الشامل ## ملخص شجرة العبور (TreeWalker) هي واجهة برمجية في JavaScript تتيح لك التنقل عبر عناصر DOM بشك...
Meta Keywords: شجرة, العبور, treewalker, javascript, العنصر
-->

# شجرة العبور (TreeWalker) في JavaScript: دليلك الشامل 

## ملخص
شجرة العبور (TreeWalker) هي واجهة برمجية في JavaScript تتيح لك التنقل عبر عناصر DOM بشكل فعال ومنظم، مما يسهل التعامل مع بنية المستندات المعقدة.

## الوثائق
### الغرض
تستخدم شجرة العبور (TreeWalker) لتوفير طريقة مرنة للتنقل بين عناصر DOM، مما يسمح للمطورين بمعالجة العناصر بطريقة هرمية. تتيح لك هذه الواجهة استعراض العناصر، النصوص، والخصائص ضمن شجرة المستند.

### الاستخدام
لإنشاء شجرة عبور، يمكنك استخدام الدالة `document.createTreeWalker()`. تأخذ هذه الدالة عدة معلمات، بما في ذلك العنصر الجذر، ونوع العقد التي تريد تضمينها (مثل العناصر، النصوص، وغيرها).

#### بناء الجملة:
```javascript
let walker = document.createTreeWalker(root, whatToShow, filter, entityReferenceExpansion);
```

- **root**: العنصر الجذر الذي ستبدأ منه عملية العبور.
- **whatToShow**: نوع العقد التي ترغب في عرضها (مثل `Node.ELEMENT_NODE` أو `Node.TEXT_NODE`).
- **filter**: كائن يُستخدم لتصفية العقد (اختياري).
- **entityReferenceExpansion**: قيمة منطقية تحدد ما إذا كان يجب توسيع الكيانات المرجعية (اختياري).

### مثال
```javascript
let root = document.getElementById("myElement");
let walker = document.createTreeWalker(root, Node.ELEMENT_NODE);

while (walker.nextNode()) {
    console.log(walker.currentNode.tagName);
}
```
في هذا المثال، نقوم بإنشاء شجرة عبور لعناصر DOM تحت العنصر الذي له المعرف "myElement" ومن ثم نقوم بطباعة أسماء العلامات لكل عنصر.

## الشرح
### الأخطاء الشائعة
- **عدم تحديد العنصر الجذر بشكل صحيح**: تأكد من أن العنصر الجذر الذي تستخدمه موجود في المستند.
- **عدم استخدام نوع العقد بشكل صحيح**: تأكد من استخدام القيم الصحيحة في خاصية `whatToShow` لتجنب تجاهل العقد المهمة.
- **تجاوز حدود الشجرة**: تأكد من التحقق من وجود عقدة قبل محاولة الوصول إليها لتجنب الأخطاء.

### ملاحظات إضافية
- شجرة العبور (TreeWalker) تساعد في تحسين الأداء عند التعامل مع مستندات كبيرة.
- يمكنك استخدام الفلتر لتحديد شروط معينة للعقد التي ترغب في التعامل معها، مما يزيد من كفاءة الكود.

## ملخص جملة واحدة
شجرة العبور (TreeWalker) في JavaScript توفر وسيلة فعالة للتنقل عبر عناصر DOM، مما يسهل معالجة المستندات بشكل هرمي.