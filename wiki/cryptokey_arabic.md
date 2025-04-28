<!--
Meta Description: # مفتاح التشفير (CryptoKey) في جافا سكريبت: تحليل شامل ## ملخص مفتاح التشفير (CryptoKey) هو كائن يُستخدم في واجهة برمجة التطبيقات الخاصة بالتشفير في ج...
Meta Keywords: التشفير, المفاتيح, المفتاح, cryptokey, يمكن
-->

# مفتاح التشفير (CryptoKey) في جافا سكريبت: تحليل شامل

## ملخص
مفتاح التشفير (CryptoKey) هو كائن يُستخدم في واجهة برمجة التطبيقات الخاصة بالتشفير في جافا سكريبت، مما يسهل عملية تشفير وفك تشفير البيانات بشكل آمن.

## الوثائق
### الغرض
تم تصميم كائن CryptoKey لتوفير واجهة موحدة للتعامل مع المفاتيح المستخدمة في خوارزميات التشفير المختلفة. يمكن استخدامه في عمليات مثل التشفير، فك التشفير، وإنتاج التوقيعات الرقمية.

### الاستخدام
يمكن إنشاء كائن CryptoKey من خلال واجهات برمجة التطبيقات مثل `SubtleCrypto.generateKey()` أو `SubtleCrypto.importKey()`. تُستخدم المفاتيح المولدة أو المستوردة في العمليات المختلفة مثل التشفير باستخدام خوارزمية AES أو التوقيع باستخدام خوارزمية RSA.

#### مثال على إنشاء مفتاح تشفير:
```javascript
const algorithm = { name: "AES-GCM", length: 256 };
const keyUsage = ["encrypt", "decrypt"];

crypto.subtle.generateKey(algorithm, true, keyUsage)
    .then(function(key) {
        console.log("تم إنشاء المفتاح:", key);
    })
    .catch(function(err) {
        console.error("خطأ في إنشاء المفتاح:", err);
    });
```

### التفاصيل
- **توليد المفاتيح**: يمكن استخدام `generateKey` لتوليد مفاتيح جديدة.
- **استيراد المفاتيح**: باستخدام `importKey`، يمكن استيراد المفاتيح من صيغ مختلفة مثل PEM أو DER.
- **تصدير المفاتيح**: يمكن استخدام `exportKey` لتصدير المفتاح لاستخدامه في أنظمة أخرى.
- **الاستخدامات**: يمكن استخدام كائنات CryptoKey في عمليات التشفير مثل `encrypt` و `decrypt` و `sign` و `verify`.

## أمثلة
### مثال على استيراد مفتاح:
```javascript
const rawKey = new Uint8Array([/* bytes of the key */]);
crypto.subtle.importKey("raw", rawKey, algorithm, true, keyUsage)
    .then(function(key) {
        console.log("تم استيراد المفتاح:", key);
    })
    .catch(function(err) {
        console.error("خطأ في استيراد المفتاح:", err);
    });
```

### مثال على استخدام المفتاح للتشفير:
```javascript
const data = new TextEncoder().encode("نص سري");
const iv = crypto.getRandomValues(new Uint8Array(12));

crypto.subtle.encrypt({ name: "AES-GCM", iv: iv }, key, data)
    .then(function(encrypted) {
        console.log("النص المشفر:", new Uint8Array(encrypted));
    })
    .catch(function(err) {
        console.error("خطأ في التشفير:", err);
    });
```

## الشرح
- **التحذيرات الشائعة**: يجب التأكد من استخدام نفس إعدادات التشفير عند استيراد المفاتيح. عدم توافق إعدادات الخوارزمية قد يؤدي إلى أخطاء.
- **السرية**: المفتاح يجب أن يُحفظ بسرية، حيث أن تسربه يعني فقدان أمان البيانات المشفرة.
- **التوافق**: التأكد من دعم المتصفح للواجهات المستخدمة يعد أمرًا مهمًا، حيث أن بعض الميزات قد لا تكون مدعومة في جميع المتصفحات.

## ملخص جملة واحدة
مفتاح التشفير (CryptoKey) في جافا سكريبت هو كائن يُستخدم لتسهيل عمليات التشفير وفك التشفير بطريقة آمنة وموحدة.