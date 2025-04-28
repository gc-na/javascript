<!--
Meta Description: # AbortController في JavaScript: التحكم في عمليات الطلبات ## ملخص `AbortController` هو واجهة في JavaScript تُستخدم للتحكم في عمليات الطلبات، مثل طلبات...
Meta Keywords: abortcontroller, signal, const, error, controller
-->

# AbortController في JavaScript: التحكم في عمليات الطلبات

## ملخص
`AbortController` هو واجهة في JavaScript تُستخدم للتحكم في عمليات الطلبات، مثل طلبات `fetch`. تتيح هذه الواجهة للمطورين إلغاء الطلبات النشطة بفعالية، مما يساعد في تحسين الأداء وتقليل الحمل على الشبكة.

## الوثائق
تُستخدم واجهة `AbortController` لإنشاء كائن يمكنه إلغاء عمليات الطلبات المعلقة. تحتوي على خاصية `signal` التي تُستخدم في الطلبات كجزء من إعدادات `fetch` أو طرق أخرى تدعم الإلغاء.

### الغرض
تساعد `AbortController` في إدارة طلبات الشبكة عن طريق السماح بإلغائها بشكل آمن، مما يُمكن المطورين من التعامل مع مواقف معينة مثل التنقل بين الصفحات دون انتظار اكتمال الطلبات السابقة.

### الاستخدام
لإنشاء كائن `AbortController`، يمكنك استخدام الكود التالي:

```javascript
const controller = new AbortController();
const signal = controller.signal;

fetch('https://example.com/data', { signal })
    .then(response => {
        if (!response.ok) {
            throw new Error('Network response was not ok');
        }
        return response.json();
    })
    .then(data => console.log(data))
    .catch(err => {
        if (err.name === 'AbortError') {
            console.log('طلب تم إلغاؤه');
        } else {
            console.error('حدث خطأ:', err);
        }
    });

// لإلغاء الطلب
controller.abort();
```

## الأمثلة
### مثال 1: إلغاء طلب `fetch`
```javascript
const controller = new AbortController();
const signal = controller.signal;

const fetchData = async () => {
    try {
        const response = await fetch('https://jsonplaceholder.typicode.com/posts', { signal });
        const data = await response.json();
        console.log(data);
    } catch (error) {
        if (error.name === 'AbortError') {
            console.log('تم إلغاء الطلب');
        } else {
            console.error('خطأ في الطلب:', error);
        }
    }
};

fetchData();

// إلغاء الطلب بعد 1 ثانية
setTimeout(() => {
    controller.abort();
}, 1000);
```

### مثال 2: استخدام `AbortController` مع `Promise.race`
```javascript
const controller = new AbortController();
const signal = controller.signal;

const fetchDataWithTimeout = () => {
    return new Promise((resolve, reject) => {
        const timeoutId = setTimeout(() => {
            controller.abort();
            reject(new Error('الطلب تجاوز الوقت المحدد'));
        }, 5000);

        fetch('https://jsonplaceholder.typicode.com/posts', { signal })
            .then(response => response.json())
            .then(data => {
                clearTimeout(timeoutId);
                resolve(data);
            })
            .catch(reject);
    });
};

fetchDataWithTimeout()
    .then(data => console.log(data))
    .catch(error => console.error(error));
```

## الشرح
### العثرات الشائعة
1. **عدم استخدام `signal`**: إذا لم يتم تمرير `signal` عند إجراء الطلب، فلن يكون هناك إمكانية لإلغاء الطلب.
2. **إلغاء الطلب بعد اكتماله**: إذا تم إلغاء الطلب بعد أن تم استلام البيانات بالفعل، فلن يكون لتلك العملية تأثير.
3. **التعامل مع الأخطاء**: يجب التأكد من التعامل مع الأخطاء بشكل صحيح، خاصةً عند إلغاء الطلبات.

### ملاحظات إضافية
- `AbortController` متوافقة مع معظم المتصفحات الحديثة، ولكن يُفضل مراجعة التوافق عبر موقع MDN.
- يمكن استخدام `AbortController` مع مكتبات خارجية مثل Axios، ولكن يتطلب ذلك تكوينًا إضافيًا.

## ملخص في جملة واحدة
`AbortController` في JavaScript هو أداة قوية لإلغاء الطلبات النشطة، مما يحسن الأداء ويزيد من كفاءة إدارة الشبكة.