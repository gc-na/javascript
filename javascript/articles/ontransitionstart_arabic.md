<!--
Meta Description: # علىTransitionStart في JavaScript: فهم شامل ## ملخص تُستخدم خاصية `ontransitionstart` في JavaScript للتعامل مع الأحداث التي تحدث عند بدء عملية الانتق...
Meta Keywords: الانتقال, ontransitionstart, style, box, button
-->

# علىTransitionStart في JavaScript: فهم شامل

## ملخص
تُستخدم خاصية `ontransitionstart` في JavaScript للتعامل مع الأحداث التي تحدث عند بدء عملية الانتقال (Transition) في CSS. تُعتبر هذه الخاصية مفيدة في تحسين تجربة المستخدم من خلال معالجة التفاعلات بشكل ديناميكي.

## الوثائق
تُعتبر `ontransitionstart` حدثًا يُطلق عندما يبدأ الانتقال في عنصر معين. يُمكن استخدام هذه الخاصية في كود JavaScript لإضافة وظائف أو تغييرات عند بدء الحركة. يُمكن أن تكون الانتقالات في CSS مرتبطة بتغييرات في الخصائص مثل اللون، والحجم، والشفافية، وغيرها.

### الاستخدام
للاستفادة من `ontransitionstart`، يجب تعيين الحدث على عنصر DOM. إليك كيفية القيام بذلك:

```javascript
const element = document.getElementById('myElement');

element.style.transition = 'all 0.5s ease'; // إعداد الانتقال

element.ontransitionstart = function(event) {
    console.log('الانتقال بدأ!');
};
```

### تفاصيل
- **الحدث**: `transitionstart`
- **الخصائص**: توفر كائن الحدث معلومات حول الانتقال، مثل اسم الخاصية التي بدأت في الانتقال، ومدة الانتقال، ووقت البدء.
- **التوافق**: مدعوم في معظم المتصفحات الحديثة، لكن قد تحتاج إلى فحص التوافق مع المتصفحات القديمة.

## الأمثلة
إليك مثال بسيط يوضح كيفية استخدام `ontransitionstart`:

### مثال 1: تغيير لون الخلفية
```html
<div id="box" style="width: 100px; height: 100px; background-color: red;"></div>
<button id="startTransition">ابدأ الانتقال</button>

<script>
    const box = document.getElementById('box');
    const button = document.getElementById('startTransition');

    box.style.transition = 'background-color 1s ease';

    box.ontransitionstart = function() {
        console.log('انتقال لون الخلفية بدأ');
    };

    button.onclick = function() {
        box.style.backgroundColor = 'blue'; // يبدأ الانتقال هنا
    };
</script>
```

### مثال 2: تغيير الحجم
```html
<div id="resizable" style="width: 100px; height: 100px; background-color: green;"></div>
<button id="resizeButton">زيادة الحجم</button>

<script>
    const resizable = document.getElementById('resizable');
    const resizeButton = document.getElementById('resizeButton');

    resizable.style.transition = 'width 0.5s';

    resizable.ontransitionstart = function() {
        console.log('انتقال الحجم بدأ');
    };

    resizeButton.onclick = function() {
        resizable.style.width = '200px'; // يبدأ الانتقال هنا
    };
</script>
```

## الشرح
على الرغم من كون `ontransitionstart` مفيدًا، إلا أن هناك بعض النقاط التي يجب الانتباه إليها:
- تأكد من أن الانتقال قد تم تعيينه بشكل صحيح على العنصر قبل استخدام `ontransitionstart`.
- قد لا تعمل `ontransitionstart` بشكل صحيح إذا كان العنصر غير مرئي أو إذا كانت هناك مشاكل في التوافق مع المتصفح.
- يجب أن تكون حذرًا مع الأحداث المتعددة، حيث يمكن أن تُطلق `ontransitionstart` عدة مرات إذا كانت هناك عدة خصائص في الانتقال.

## ملخص جملة واحدة
`ontransitionstart` هو حدث يُستخدم في JavaScript للإشارة إلى بداية الانتقال في عناصر CSS، مما يُتيح للمطورين إضافة تفاعلات ديناميكية عند بدء هذه العملية.