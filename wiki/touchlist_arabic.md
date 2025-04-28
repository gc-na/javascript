<!--
Meta Description: # TouchList في JavaScript: دليل شامل ومفصل ## الملخص تعتبر TouchList إحدى الواجهات في JavaScript التي تستخدم للتعامل مع الأحداث اللمسية، حيث توفر مجمو...
Meta Keywords: touchlist, اللمسات, على, javascript, event
-->

# TouchList في JavaScript: دليل شامل ومفصل

## الملخص
تعتبر TouchList إحدى الواجهات في JavaScript التي تستخدم للتعامل مع الأحداث اللمسية، حيث توفر مجموعة من الخصائص المتعلقة بلمسات المستخدم على الشاشة، مما يسهل تطوير تطبيقات الويب التفاعلية.

## الوثائق
### الغرض
يستخدم TouchList لتجميع معلومات حول اللمسات المتعددة على الأجهزة التي تدعم اللمس، مثل الهواتف الذكية والأجهزة اللوحية. يمكن الوصول إلى TouchList من خلال أحداث اللمس مثل `touchstart`، `touchmove`، و `touchend`.

### الاستخدام
يمكن الحصول على TouchList من خلال الحدث اللمسي، حيث يتم تمرير كائن الحدث إلى المعالج. يحتوي TouchList على مجموعة من العناصر التي تمثل اللمسات النشطة في الوقت الحالي.

### التفاصيل
- **الخصائص**:
  - `length`: عدد اللمسات النشطة في TouchList.
  - `item(index)`: دالة تسترجع اللمسة الموجودة في الفهرس المحدد.
  - `forEach(callback)`: دالة تسمح بتنفيذ دالة معينة لكل لمسة في TouchList.

## الأمثلة
### مثال بسيط
```javascript
document.addEventListener('touchstart', function(event) {
    let touches = event.touches; // الحصول على TouchList
    console.log("عدد اللمسات النشطة: " + touches.length); // طباعة عدد اللمسات
});
```

### مثال مع استخدام item
```javascript
document.addEventListener('touchstart', function(event) {
    let touch = event.touches.item(0); // الحصول على أول لمسة
    console.log("إحداثيات اللمسة: (" + touch.clientX + ", " + touch.clientY + ")");
});
```

### مثال باستخدام forEach
```javascript
document.addEventListener('touchstart', function(event) {
    event.touches.forEach(function(touch) {
        console.log("لمسة في: (" + touch.clientX + ", " + touch.clientY + ")");
    });
});
```

## الشرح
من الأخطاء الشائعة التي قد يقع فيها المطورون هو عدم التحقق من عدد اللمسات قبل محاولة الوصول إلى فهرس معين في TouchList. من المهم التأكد من أن الفهرس الذي يتم الوصول إليه هو ضمن النطاق الصحيح لتجنب الأخطاء. 

أيضًا، يجب الانتباه إلى أن TouchList قد يتغير أثناء تفاعل المستخدم مع الشاشة، لذا من الأفضل إعادة التحقق من اللمسات عند كل حدث لمسي.

## ملخص من جملة واحدة
تعد TouchList في JavaScript أداة قوية للتعامل مع اللمسات المتعددة على الأجهزة اللمسية، مما يسهل إنشاء تطبيقات تفاعلية وغنية.