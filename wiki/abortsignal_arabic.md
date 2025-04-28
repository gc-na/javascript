<!--
Meta Description: # AbortSignal في جافا سكريبت: فهم الاستخدامات والإمكانيات ## ملخص تعتبر `AbortSignal` جزءًا من واجهة `AbortController` في جافا سكريبت، وهي تستخدم لإلغ...
Meta Keywords: abortsignal, signal, abortcontroller, العمليات, fetch
-->

# AbortSignal في جافا سكريبت: فهم الاستخدامات والإمكانيات

## ملخص
تعتبر `AbortSignal` جزءًا من واجهة `AbortController` في جافا سكريبت، وهي تستخدم لإلغاء العمليات غير المكتملة، مثل الطلبات الشبكية أو المهام الطويلة، مما يسمح بتحكم أفضل في تدفق العمليات.

## الوثائق
### الغرض
`AbortSignal` يوفر وسيلة لتلقي إشعارات الإلغاء. يتم استخدامه بشكل شائع مع `fetch` لإلغاء الطلبات، ولكن يمكن أيضًا استخدامه مع أي عمليات تدعم الإلغاء.

### الاستخدام
لإنشاء `AbortSignal`، تحتاج أولاً إلى إنشاء كائن `AbortController`. يمكنك استخدام الإشارة من هذا الكائن لإلغاء العمليات عند الحاجة.

#### كيفية الاستخدام:
1. إنشاء كائن `AbortController`.
2. استخدام `signal` الخاص بـ `AbortController` كجزء من الطلب أو العملية.
3. استدعاء `abort()` من `AbortController` لإلغاء العملية.

### التفاصيل
- `signal` هو الكائن الذي يتم تمريره إلى العمليات.
- يمكن استخدام `AbortSignal` في العديد من العمليات، مثل `fetch` و`setTimeout`.
- يمكن أن يتم استدعاء `abort()` في أي وقت لإلغاء العملية، مما يؤدي إلى تنبيه الكائنات المرتبطة.

## الأمثلة
### مثال 1: استخدام `AbortSignal` مع `fetch`
```javascript
const controller = new AbortController();
const signal = controller.signal;

fetch('https://example.com/data', { signal })
  .then(response => {
    if (!response.ok) throw new Error('Network response was not ok');
    return response.json();
  })
  .then(data => console.log(data))
  .catch(err => {
    if (err.name === 'AbortError') {
      console.log('Fetch aborted');
    } else {
      console.error('Fetch error:', err);
    }
  });

// إلغاء الطلب بعد 1 ثانية
setTimeout(() => {
  controller.abort();
}, 1000);
```

### مثال 2: استخدام `AbortSignal` مع `setTimeout`
```javascript
const controller = new AbortController();
const signal = controller.signal;

const timeoutId = setTimeout(() => {
  if (!signal.aborted) {
    console.log('Operation completed');
  }
}, 2000);

signal.addEventListener('abort', () => {
  clearTimeout(timeoutId);
  console.log('Operation aborted');
});

// إلغاء العملية بعد 1.5 ثانية
setTimeout(() => {
  controller.abort();
}, 1500);
```

## الشرح
### الأخطاء الشائعة
- عدم التحقق مما إذا كانت الإشارة قد تم إلغاؤها قبل إتمام العملية قد يؤدي إلى أخطاء غير متوقعة.
- استخدام `AbortSignal` مع عمليات لا تدعم الإلغاء قد يؤدي إلى عدم الفائدة من هذا الكائن.
- التأكد من إضافة مستمعات الأحداث لـ `abort` يمكن أن يكون مفيدًا لتجنب حالات عدم التزامن.

## ملخص جملة واحدة
`AbortSignal` في جافا سكريبت يوفر وسيلة فعالة لإدارة إلغاء العمليات غير المكتملة، مما يحسن من أداء التطبيقات وتجربة المستخدم.