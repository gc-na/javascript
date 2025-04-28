<!--
Meta Description: # إحصائيات مسار الفيديو MediaStreamTrackVideoStats في JavaScript ## ملخص إحصائيات مسار الفيديو MediaStreamTrackVideoStats هي واجهة برمجة تطبيقات في Ja...
Meta Keywords: الفيديو, report, إحصائيات, على, console
-->

# إحصائيات مسار الفيديو MediaStreamTrackVideoStats في JavaScript

## ملخص
إحصائيات مسار الفيديو MediaStreamTrackVideoStats هي واجهة برمجة تطبيقات في JavaScript توفر معلومات مفصلة حول تدفقات الفيديو المستخدمة في تطبيقات الويب. تساعد هذه الإحصائيات المطورين في مراقبة جودة الفيديو وتحليل الأداء.

## الوثائق
تُستخدم MediaStreamTrackVideoStats لجمع إحصائيات حول تدفقات الفيديو في الوقت الفعلي. هذه الإحصائيات تتضمن معلومات مثل الدقة، ومعدل الإطارات، والبيانات المرسلة. 

### الغرض
الغرض من MediaStreamTrackVideoStats هو تمكين المطورين من مراقبة وتحليل الجودة والأداء في تطبيقات الفيديو المباشرة، مما يساعد على تحسين تجربة المستخدم.

### الاستخدام
للحصول على إحصائيات الفيديو، يجب أولاً إنشاء تدفق وسائط (MediaStream) ثم الوصول إلى مسارات الفيديو (MediaStreamTrack) المرتبطة به. بعد ذلك، يمكن استخدام واجهة `getStats()` للحصول على إحصائيات الفيديو.

### التفاصيل
- **الدقة**: يتم الإبلاغ عن دقة الفيديو الحالية (العرض × الطول).
- **معدل الإطارات**: يحدد عدد الإطارات في الثانية (fps) التي يتم عرضها.
- **البيانات المرسلة**: كمية البيانات المرسلة خلال فترة زمنية معينة.

## أمثلة
### مثال 1: الحصول على إحصائيات الفيديو
```javascript
navigator.mediaDevices.getUserMedia({ video: true })
    .then(stream => {
        const videoTrack = stream.getVideoTracks()[0];
        const peerConnection = new RTCPeerConnection();
        peerConnection.addTrack(videoTrack);
        
        peerConnection.getStats(videoTrack).then(stats => {
            stats.forEach(report => {
                if (report.type === 'video') {
                    console.log(`Resolution: ${report.width}x${report.height}`);
                    console.log(`Frame Rate: ${report.framesPerSecond}`);
                    console.log(`Bytes Sent: ${report.bytesSent}`);
                }
            });
        });
    })
    .catch(error => {
        console.error('Error accessing media devices.', error);
    });
```

### مثال 2: تحليل إحصائيات الفيديو
```javascript
function analyzeVideoStats(stats) {
    stats.forEach(report => {
        if (report.type === 'video') {
            console.log(`Video Resolution: ${report.width}x${report.height}`);
            console.log(`Frames Sent: ${report.framesSent}`);
            console.log(`Frames Received: ${report.framesReceived}`);
        }
    });
}

// Assume 'peerConnection' is already established
peerConnection.getStats().then(analyzeVideoStats);
```

## الشرح
### العوائق الشائعة
- **عدم توفر الإحصائيات**: في بعض الأحيان، قد لا تتوفر الإحصائيات بسبب عدم وجود تدفق أو بسبب مشاكل في الاتصال.
- **التأخير في الحصول على البيانات**: قد يكون هناك تأخير في الحصول على الإحصائيات، لذا يُفضل استخدام `setInterval` للحصول على بيانات محدثة بشكل دوري.

### ملاحظات إضافية
- يمكن أن تختلف الإحصائيات بناءً على نوع الجهاز والمستعرض المستخدم.
- تأكد من أن لديك الأذونات اللازمة للوصول إلى الكاميرا أو الميكروفون.

## ملخص جملة واحدة
تُستخدم MediaStreamTrackVideoStats في JavaScript لجمع إحصائيات تفصيلية حول تدفقات الفيديو لتحسين جودة الأداء وتجربة المستخدم.