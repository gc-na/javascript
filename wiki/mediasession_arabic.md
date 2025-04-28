<!--
Meta Description: # MediaSession في JavaScript: التحكم في الوسائط بشكل ذكي ## ملخص تتيح واجهة `MediaSession` في JavaScript التحكم في تشغيل الوسائط وتخصيص واجهة المستخدم...
Meta Keywords: mediasession, الوسائط, navigator, setactionhandler, javascript
-->

# MediaSession في JavaScript: التحكم في الوسائط بشكل ذكي

## ملخص
تتيح واجهة `MediaSession` في JavaScript التحكم في تشغيل الوسائط وتخصيص واجهة المستخدم الخاصة بها، مما يحسن تجربة المستخدم على الأجهزة المختلفة.

## الوثائق
### الغرض
تمكن واجهة `MediaSession` المطورين من التعامل مع تشغيل الوسائط بشكل أكثر كفاءة، سواء كان ذلك في تطبيقات الويب أو المواقع. تساعد هذه الواجهة في تحسين التكامل مع أنظمة التشغيل والأجهزة المحمولة من خلال توفير معلومات عن الوسائط قيد التشغيل، مثل العنوان، الفنان، والغلاف.

### الاستخدام
للبدء باستخدام `MediaSession`، يجب أولاً التحقق مما إذا كانت الواجهة مدعومة في المتصفح. بعد ذلك، يمكن إعداد خصائص الجلسة مثل العنوان، الفنان، والعمليات التي يمكن تنفيذها (مثل التشغيل، الإيقاف المؤقت، أو التخطي).

#### إنشاء MediaSession
```javascript
if ('mediaSession' in navigator) {
    navigator.mediaSession.metadata = new MediaMetadata({
        title: 'اسم الأغنية',
        artist: 'اسم الفنان',
        album: 'اسم الألبوم',
        artwork: [{ src: 'url_to_artwork.jpg', sizes: '512x512', type: 'image/jpeg' }]
    });

    navigator.mediaSession.setActionHandler('play', function() {
        // تشغيل الوسائط
    });

    navigator.mediaSession.setActionHandler('pause', function() {
        // إيقاف الوسائط مؤقتًا
    });
}
```

### التفاصيل
- **الخصائص**: يمكن لمطوري الويب تعيين خصائص مثل `metadata` لتوفير معلومات عن الوسائط.
- **الإجراءات**: يمكن استخدام `setActionHandler` لتحديد الإجراءات المختلفة مثل التشغيل، الإيقاف المؤقت، والتخطي.
- **التخصيص**: يمكن تخصيص واجهة المستخدم الخاصة بالوسائط بناءً على المعلومات المقدمة.

## أمثلة
### مثال بسيط لتشغيل أغنية
```javascript
if ('mediaSession' in navigator) {
    navigator.mediaSession.metadata = new MediaMetadata({
        title: 'أغنية رائعة',
        artist: 'فنان مبدع',
        album: 'ألبوم مميز',
        artwork: [{ src: 'artwork.jpg', sizes: '512x512', type: 'image/jpeg' }]
    });

    navigator.mediaSession.setActionHandler('play', () => {
        console.log('تشغيل الوسائط...');
    });

    navigator.mediaSession.setActionHandler('pause', () => {
        console.log('إيقاف الوسائط مؤقتًا...');
    });
}
```

### مثال لتخصيص الأزرار
```javascript
navigator.mediaSession.setActionHandler('previoustrack', () => {
    // الانتقال إلى الأغنية السابقة
});

navigator.mediaSession.setActionHandler('nexttrack', () => {
    // الانتقال إلى الأغنية التالية
});
```

## الشرح
- **التوافق**: تأكد من أن المتصفح يدعم `MediaSession` قبل استخدامه.
- **المعلومات**: يجب أن تكون المعلومات المقدمة دقيقة لتعزيز تجربة المستخدم.
- **الأزرار**: تأكد من معالجة جميع الأزرار بشكل صحيح لتجنب أي خلل في تجربة المستخدم.

## ملخص جملة واحدة
تتيح واجهة `MediaSession` في JavaScript تحسين تجربة تشغيل الوسائط من خلال تخصيص المعلومات والإجراءات المتعلقة بالوسائط.