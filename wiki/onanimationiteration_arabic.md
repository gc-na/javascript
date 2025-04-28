<!--
Meta Description: # onanimationiteration في JavaScript: فهم التفعيل والوظيفة ## ملخص حدث `onanimationiteration` في JavaScript هو حدث يتم إطلاقه في كل مرة تنتهي فيها دور...
Meta Keywords: المتحركة, onanimationiteration, الرسوم, element, javascript
-->

# onanimationiteration في JavaScript: فهم التفعيل والوظيفة

## ملخص
حدث `onanimationiteration` في JavaScript هو حدث يتم إطلاقه في كل مرة تنتهي فيها دورة تكرارية من الرسوم المتحركة CSS. يُستخدم هذا الحدث في الغالب لإجراء تغييرات أو تنفيذ دوال معينة بناءً على تقدم الرسوم المتحركة، مما يوفر تحكمًا أكبر في الرسوم المتحركة الديناميكية.

## الوثائق
### الغرض
`onanimationiteration` هو جزء من واجهة البرمجة لتطبيقات الويب (Web API) والذي يتيح لك الاستجابة للتكرارات المتعددة لرسوم متحركة CSS.

### الاستخدام
يتم تعيين `onanimationiteration` على عنصر HTML، ويُستدعى عند كل تكرار للرسوم المتحركة المرتبطة بهذا العنصر. يمكنك استخدامه لإضافة تفاعلات أو تغييرات بصرية في الوقت المناسب مع دورة الرسوم المتحركة.

### التفاصيل
- **النوع**: حدث
- **الحدث المتعلق**: `animationiteration`
- **البروتوكول**: يستقبل الحدث كائنًا يحتوي على تفاصيل حول الرسوم المتحركة.
- **التوافق**: مدعوم في معظم المتصفحات الحديثة.

## الأمثلة
### مثال أساسي
```javascript
const element = document.getElementById("myElement");

element.style.animation = "myAnimation 2s infinite";

element.onanimationiteration = function() {
    console.log("تمت دورة الرسوم المتحركة.");
};
```

### مثال مع تغيير نمط
```javascript
const element = document.getElementById("myElement");

element.style.animation = "myAnimation 2s infinite";

element.onanimationiteration = function() {
    element.style.backgroundColor = getRandomColor();
};

function getRandomColor() {
    const letters = '0123456789ABCDEF';
    let color = '#';
    for (let i = 0; i < 6; i++) {
        color += letters[Math.floor(Math.random() * 16)];
    }
    return color;
}
```

## الشرح
### الفخاخ الشائعة
- **عدم التوافق**: تأكد من اختبار `onanimationiteration` عبر المتصفحات المختلفة، حيث قد يختلف السلوك في بعض المتصفحات القديمة.
- **تكرار غير متوقع**: في حالة وجود أكثر من رسوم متحركة، تأكد من أنك تحدد الرسوم المتحركة الصحيحة، حيث يمكن أن تؤدي الرسوم المتحركة المتعددة إلى استدعاء الحدث بشكل غير متوقع.
- **الأداء**: استخدام دوال ثقيلة داخل `onanimationiteration` قد يؤثر على الأداء، لذا يُفضل استخدام دوال خفيفة لتحسين الأداء.

## ملخص جملة واحدة
`onanimationiteration` هو حدث في JavaScript يُستخدم للاستجابة لكل تكرار لدورة الرسوم المتحركة في CSS، مما يوفر تحكمًا ديناميكيًا في التفاعلات المرئية.