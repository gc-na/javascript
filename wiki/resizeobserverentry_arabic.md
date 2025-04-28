<!--
Meta Description: # ResizeObserverEntry في JavaScript: مراقبة تغييرات حجم العناصر ## الملخص تُستخدم ResizeObserverEntry في JavaScript لتقديم معلومات مُفصّلة حول تغييرات...
Meta Keywords: resizeobserver, resizeobserverentry, حجم, entry, javascript
-->

# ResizeObserverEntry في JavaScript: مراقبة تغييرات حجم العناصر

## الملخص
تُستخدم ResizeObserverEntry في JavaScript لتقديم معلومات مُفصّلة حول تغييرات حجم العناصر في مستند HTML، مما يتيح للمطورين مراقبة التغييرات في الواجهة بشكل ديناميكي.

## الوثائق
### الغرض
تعتبر ResizeObserverEntry جزءًا من واجهة ResizeObserver، وتُستخدم لتوفير معلومات حول عنصر تم مراقبته عندما يغير حجمه. تحتوي ResizeObserverEntry على خصائص تُخبرنا عن الأبعاد الجديدة للعنصر.

### الاستخدام
تُستخدم ResizeObserverEntry عادةً مع كائن ResizeObserver. عند تسجيل عنصر لمراقبة التغييرات، يتم استدعاء دالة رد النداء (callback) مع مصفوفة من ResizeObserverEntry لكل عنصر تمت مراقبته. 

### الخصائص
- **target**: يُمثل العنصر الذي تم مراقبته.
- **contentRect**: يُمثل مستطيل الأبعاد (أبعاد المحتوى) للعنصر، والذي يتضمن العرض والارتفاع.
- **borderBoxSize**: يُمثل حجم مستطيل الحدود للعنصر، والذي يشمل الحدود.
- **contentBoxSize**: يُمثل حجم مستطيل المحتوى للعنصر، والذي يُظهر الحجم الفعلي للمحتوى.

## الأمثلة
### مثال أساسي
```javascript
const resizeObserver = new ResizeObserver(entries => {
    for (let entry of entries) {
        console.log('تغير حجم العنصر:', entry.target);
        console.log('عرض المحتوى:', entry.contentRect.width);
        console.log('ارتفاع المحتوى:', entry.contentRect.height);
    }
});

// تحديد العنصر المراد مراقبته
const element = document.querySelector('.resize-me');
resizeObserver.observe(element);
```

### مثال مع خاصية borderBoxSize
```javascript
const resizeObserver = new ResizeObserver(entries => {
    for (let entry of entries) {
        console.log('حجم الحدود:', entry.borderBoxSize);
    }
});

// مراقبة عنصر
const element = document.querySelector('.resize-me');
resizeObserver.observe(element);
```

## الشرح
### الأخطاء الشائعة والملاحظات
- **عدم إزالة المراقبة**: إذا كنت تستخدم ResizeObserver، تأكد من استخدام `unobserve` لإزالة المراقبة عن العناصر التي لم تعد تحتاجها، لتفادي تسرب الذاكرة.
- **التأخير في التحديثات**: قد يحدث تأخير طفيف في الإبلاغ عن تغييرات الحجم، لذا يُفضل عدم الاعتماد على النتائج الفورية.
- **التوافق مع المتصفحات**: تحقق من توافق المتصفح مع ResizeObserver، حيث قد لا تتوفر في بعض الإصدارات القديمة من المتصفحات.

## ملخص جملة واحدة
تُستخدم ResizeObserverEntry في JavaScript لتوفير معلومات دقيقة حول تغييرات حجم العناصر في صفحة الويب.