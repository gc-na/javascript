<!--
Meta Description: # SubtleCrypto في JavaScript: الأمان والتشفير السري ## ملخص SubtleCrypto هي واجهة برمجية في JavaScript تسمح للمطورين بإجراء عمليات تشفير وفك تشفير موث...
Meta Keywords: subtlecrypto, البيانات, تشفير, const, واجهة
-->

# SubtleCrypto في JavaScript: الأمان والتشفير السري

## ملخص
SubtleCrypto هي واجهة برمجية في JavaScript تسمح للمطورين بإجراء عمليات تشفير وفك تشفير موثوقة من خلال واجهة Web Crypto. تساعد هذه الواجهة في تعزيز الأمان من خلال توفير أدوات للتشفير، التجزئة، وتوليد المفاتيح.

## الوثائق
تُعتبر SubtleCrypto جزءًا من واجهة Web Crypto API، والتي توفر مجموعة من الوظائف الأساسية المتعلقة بالتشفير. هذه الواجهة تُستخدم بشكل رئيسي في التطبيقات التي تتطلب مستويات عالية من الأمان، مثل تطبيقات المصادقة والتوقيع الرقمي.

### الغرض
يهدف SubtleCrypto إلى تمكين المطورين من تنفيذ عمليات التشفير بشكل آمن وسهل. يتم استخدامه لتأمين البيانات الحساسة، مثل كلمات المرور والمعلومات الشخصية.

### الاستخدام
يمكن استخدام SubtleCrypto لإجراء العمليات التالية:
- **تشفير البيانات**: تحويل البيانات إلى شكل غير مقروء لحمايتها.
- **فك تشفير البيانات**: تحويل البيانات المشفرة إلى شكلها الأصلي.
- **توليد مفاتيح جديدة**: إنشاء مفاتيح للتشفير.
- **تجزئة البيانات**: إنتاج تجزئة لمجموعة من البيانات لضمان سلامتها.

### تفاصيل
```javascript
// الوصول إلى واجهة SubtleCrypto
const subtle = window.crypto.subtle;
```

يجب أن يتم استدعاء الوظائف المتاحة في واجهة SubtleCrypto من خلال الكائن `subtle`، والذي يوفر مجموعة من الوظائف مثل `encrypt`, `decrypt`, `digest`, و`generateKey`.

## الأمثلة
### مثال على تشفير وفك تشفير نص
```javascript
async function encryptData(plaintext) {
    const encoder = new TextEncoder();
    const data = encoder.encode(plaintext);
    
    const key = await subtle.generateKey(
        {
            name: "AES-GCM",
            length: 256
        },
        true,
        ["encrypt", "decrypt"]
    );

    const iv = window.crypto.getRandomValues(new Uint8Array(12)); // IV عشوائي

    const ciphertext = await subtle.encrypt(
        {
            name: "AES-GCM",
            iv: iv
        },
        key,
        data
    );

    return { ciphertext, key, iv };
}

async function decryptData(ciphertext, key, iv) {
    const decrypted = await subtle.decrypt(
        {
            name: "AES-GCM",
            iv: iv
        },
        key,
        ciphertext
    );

    const decoder = new TextDecoder();
    return decoder.decode(decrypted);
}
```

## الشرح
### الأخطاء الشائعة
- **عدم استخدام IV بشكل صحيح**: يجب أن يكون الـ IV فريدًا وعشوائيًا لكل عملية تشفير.
- **استخدام خوارزميات غير مدعومة**: تأكد من أن الخوارزمية المطلوبة مدعومة في البيئة التي تعمل بها.
- **عدم التعامل مع الوعود**: نظراً لأن العمليات غير متزامنة، يجب التأكد من استخدام `async/await` أو `then` لمعالجة النتائج بشكل صحيح.

### ملاحظات إضافية
- يتم تنفيذ SubtleCrypto في المتصفحات الحديثة، لذا تأكد من التحقق من التوافق مع المتصفح المستهدف.
- قد تختلف سرعة الأداء حسب الخوارزمية المستخدمة وحجم البيانات.

## ملخص جملة واحدة
SubtleCrypto هو واجهة برمجية في JavaScript توفر أدوات تشفير آمنة وموثوقة لتأمين البيانات الحساسة.