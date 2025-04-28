<!--
Meta Description: # ResizeObserver في JavaScript: مراقبة تغييرات حجم العناصر ## ملخص ResizeObserver هو واجهة برمجية في JavaScript تُستخدم لمراقبة تغييرات حجم العناصر في...
Meta Keywords: resizeobserver, javascript, يتم, العناصر, تغييرات
-->

# ResizeObserver في JavaScript: مراقبة تغييرات حجم العناصر

## ملخص
ResizeObserver هو واجهة برمجية في JavaScript تُستخدم لمراقبة تغييرات حجم العناصر في صفحة الويب. يمكّن المطورين من تنفيذ إجراءات معينة عند تغيير أبعاد عنصر معين، مما يساعد في تحسين تجربة المستخدم.

## الوثائق
### الغرض
تُستخدم واجهة ResizeObserver لمراقبة تغييرات الحجم (العرض والارتفاع) لعناصر DOM. عند تغيير حجم العنصر، يتم استدعاء دالة رد النداء (callback) المحددة، مما يسمح بتنفيذ وظائف معينة، مثل إعادة رسم العناصر أو تعديل التخطيط.

### الاستخدام
لإنشاء كائن ResizeObserver، يتم استخدام الكود التالي:

```javascript
const observer = new ResizeObserver(callback);
```

#### المعاملات:
- `callback`: دالة يتم استدعاؤها عند تغيير حجم العنصر. تأخذ هذه الدالة معاملين: قائمة من الكائنات `ResizeObserverEntry`، والـ `ResizeObserver` نفسه.

### ملاحظات هامة
- يجب أن يتم تسجيل العناصر التي ترغب في مراقبتها باستخدام `observe`:
```javascript
observer.observe(targetElement);
```
- لإيقاف المراقبة، يمكن استخدام `unobserve`:
```javascript
observer.unobserve(targetElement);
```
- لإزالة المراقبة عن جميع العناصر، يمكن استخدام `disconnect`:
```javascript
observer.disconnect();
```

## الأمثلة
### مثال 1: مراقبة عنصر واحد
```javascript
const box = document.querySelector('.box');

const resizeObserver = new ResizeObserver(entries => {
    for (let entry of entries) {
        console.log('تغير الحجم:', entry.contentRect.width, 'x', entry.contentRect.height);
    }
});

resizeObserver.observe(box);
```

### مثال 2: إيقاف المراقبة
```javascript
resizeObserver.unobserve(box);
```

### مثال 3: إزالة المراقبة بالكامل
```javascript
resizeObserver.disconnect();
```

## الشرح
### الأخطاء الشائعة
- **عدم تسجيل العناصر**: إذا لم يتم استخدام `observe`، فلن يتم مراقبة أي تغييرات.
- **تكرار استدعاء الدالة**: يمكن أن يتم استدعاء دالة رد النداء عدة مرات في وقت قصير، مما قد يؤدي إلى أداء غير مُحسن. من الأفضل استخدام تقنيات مثل `debouncing` أو `throttling` للتحكم في عدد المرات التي يتم فيها تنفيذ الأكواد.
- **التوافق مع المتصفحات**: تأكد من التحقق من توافق المتصفح مع ResizeObserver، حيث أن بعض المتصفحات القديمة قد لا تدعمه.

## ملخص بسيط
ResizeObserver هو أداة قوية في JavaScript لمراقبة تغييرات حجم عناصر DOM، مما يسهل تحسين تجربة المستخدم في التطبيقات التفاعلية.