<!--
Meta Description: # حدث ontransitioncancel في جافا سكريبت: فهم وإدارة التحولات ## ملخص حدث `ontransitioncancel` في جافا سكريبت هو حدث يتم تفعيله عندما يتم إلغاء عملية ا...
Meta Keywords: box, التحول, ontransitioncancel, إلغاء, event
-->

# حدث ontransitioncancel في جافا سكريبت: فهم وإدارة التحولات

## ملخص
حدث `ontransitioncancel` في جافا سكريبت هو حدث يتم تفعيله عندما يتم إلغاء عملية التحول (transition) لعناصر DOM. يُستخدم هذا الحدث لإدارة السلوكيات الخاصة بالعناصر التي تخضع لتأثيرات CSS transition، مما يساعد في تحسين تجربة المستخدم.

## الوثائق
### الغرض
يهدف حدث `ontransitioncancel` إلى تمكين المطورين من الاستجابة لإلغاء التحولات، مما يمكنهم من تنفيذ إجراءات معينة عندما لا تكتمل التحولات كما هو متوقع.

### الاستخدام
يتم استخدام `ontransitioncancel` مع عناصر DOM، ويمكن تعيينه مباشرة على العنصر أو عبر أحداث الناتجة عن إضافة مستمعات الأحداث (event listeners). يتم تفعيل هذا الحدث عندما يتم إلغاء التحول بسبب تغييرات غير متوقعة في الأنماط.

### تفاصيل
- **النوع**: حدث (Event)
- **الخصائص**: 
  - `propertyName`: اسم خاصية CSS التي تم إلغاؤها.
  - `elapsedTime`: الوقت المستغرق قبل إلغاء التحول.
  - `pseudoElement`: العنصر الزائف المرتبط، إن وجد.

### كيفية الاستخدام
```javascript
const element = document.querySelector('.my-element');

element.ontransitioncancel = function(event) {
    console.log(`تم إلغاء التحول للخاصية: ${event.propertyName}`);
};
```

## أمثلة
### مثال بسيط
```javascript
const box = document.querySelector('.box');

box.ontransitioncancel = function(event) {
    alert(`تم إلغاء التحول للخاصية: ${event.propertyName}`);
};

// بدء التحول
box.style.transition = 'opacity 2s';
box.style.opacity = 0;

// إلغاء التحول عن طريق تغيير خاصية أخرى
setTimeout(() => {
    box.style.transform = 'translateX(100px)';
}, 1000);
```

### مثال مع الاستخدام المتقدم
```javascript
const button = document.querySelector('.animate-button');
const box = document.querySelector('.box');

button.addEventListener('click', () => {
    box.style.transition = 'transform 2s';
    box.style.transform = 'rotate(90deg)';
});

// إلغاء التحول
box.ontransitioncancel = function(event) {
    console.error(`التحول تم إلغاؤه للخاصية: ${event.propertyName}`);
};
```

## التفسير
### الأخطاء الشائعة
- **عدم تفعيل الحدث**: تأكد من أن التحولات قيد التنفيذ وأن هناك تغييرًا يؤدي إلى إلغاء التحول.
- **عدم وجود خاصية**: إذا لم تكن الخاصية التي تم إلغاؤها موجودة، قد لا يتم تفعيل الحدث كما هو متوقع.
- **الأداء**: تجنب إضافة الكثير من الأحداث على نفس العنصر، حيث يمكن أن يؤثر ذلك على أداء التطبيق.

## ملخص في جملة واحدة
يعد حدث `ontransitioncancel` في جافا سكريبت أداة قوية لإدارة التحولات الملغاة على عناصر DOM، مما يساعد المطورين على تحسين تفاعل المستخدم.