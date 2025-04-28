<!--
Meta Description: # عنصر HTMLMapElement في جافا سكريبت ## ملخص عنصر HTMLMapElement هو واجهة برمجية في جافا سكريبت تمثل عنصر `<map>` في HTML، والذي يُستخدم لتعريف منطقة ...
Meta Keywords: map, htmlmapelement, area, عنصر, html
-->

# عنصر HTMLMapElement في جافا سكريبت

## ملخص
عنصر HTMLMapElement هو واجهة برمجية في جافا سكريبت تمثل عنصر `<map>` في HTML، والذي يُستخدم لتعريف منطقة تفاعلية في صورة، مما يسمح بإنشاء روابط تشعبية ضمن أجزاء محددة من الصورة.

## الوثائق
### الغرض
HTMLMapElement يُستخدم لتحديد الخرائط التفاعلية للصورة، حيث يمكن للمطورين تحديد مناطق محددة داخل الصورة، وتمكين المستخدمين من النقر على تلك المناطق للوصول إلى روابط معينة.

### الاستخدام
يمكن استخدام HTMLMapElement في جافا سكريبت للتفاعل مع عناصر الخريطة، مثل إضافة، تعديل أو إزالة المناطق. يتم الربط بين عنصر `<map>` وعنصر `<img>` باستخدام خاصية `usemap`.

### التفاصيل
```html
<img src="image.jpg" usemap="#myMap">
<map name="myMap">
    <area shape="rect" coords="34,44,270,350" href="link1.html" alt="Link 1">
    <area shape="circle" coords="337,300,44" href="link2.html" alt="Link 2">
</map>
```
في المثال أعلاه، يتم تعريف خريطة تفاعلية للصورة باستخدام عنصر `<map>`، حيث يحتوي على منطقتين مختلفتين للنقر.

## أمثلة

### مثال 1: استخدام HTMLMapElement
```html
<img src="example.jpg" usemap="#exampleMap">
<map name="exampleMap">
    <area shape="rect" coords="34,44,270,350" href="http://example.com/1" alt="منطقة 1">
    <area shape="circle" coords="337,300,44" href="http://example.com/2" alt="منطقة 2">
</map>
```

### مثال 2: التفاعل مع HTMLMapElement باستخدام جافا سكريبت
```javascript
const map = document.querySelector('map[name="exampleMap"]');
const areas = map.getElementsByTagName('area');

for (let area of areas) {
    area.addEventListener('click', function(event) {
        alert(`تم النقر على ${area.alt}`);
    });
}
```

## الشرح
### الأخطاء الشائعة
- **عدم الربط بشكل صحيح**: تأكد من أن خاصية `usemap` في عنصر `<img>` تتطابق مع اسم الخريطة المحدد في عنصر `<map>`.
- **عدم تحديد الأبعاد**: عند تحديد الأبعاد (coords) للمناطق، تأكد من دقتها لتجنب النقر على مناطق غير صحيحة.
- **توافق المتصفح**: تأكد من اختبار الخريطة التفاعلية على المتصفحات المختلفة حيث قد تختلف بعض السلوكيات.

### ملاحظات إضافية
- يمكن استخدام أشكال متعددة مثل `rect` و `circle` و `poly` لتحديد المناطق.
- تتيح لك HTMLMapElement التحكم الكامل في المناطق التفاعلية باستخدام جافا سكريبت.

## ملخص جملة
HTMLMapElement يسمح بإنشاء خرائط تفاعلية للصورة في HTML، مما يمكّن المستخدمين من التفاعل مع أجزاء محددة من الصورة.