<!--
Meta Description: # WebkitRTCPeerConnection في JavaScript: دليل شامل ## ملخص تُعتبر WebkitRTCPeerConnection واجهة برمجية تستخدم في تطبيقات الويب لإجراء اتصالات الصوت وا...
Meta Keywords: webkitrtcpeerconnection, error, ice, candidate, javascript
-->

# WebkitRTCPeerConnection في JavaScript: دليل شامل

## ملخص
تُعتبر WebkitRTCPeerConnection واجهة برمجية تستخدم في تطبيقات الويب لإجراء اتصالات الصوت والفيديو في الوقت الحقيقي. توفر هذه الواجهة خصائص وطرق لتسهيل تبادل البيانات بين المتصفحات.

## الوثائق
### الغرض
تُستخدم WebkitRTCPeerConnection كجزء من واجهة WebRTC (Web Real-Time Communication)، التي تسمح بتبادل الوسائط المتعددة في الوقت الحقيقي بين المتصفحات بدون الحاجة إلى خادم وسائط. توفر WebkitRTCPeerConnection وظائف لإنشاء اتصالات نظير إلى نظير، مما يتيح لمطوري الويب إنشاء تطبيقات مثل مكالمات الفيديو أو الدردشة الصوتية بطريقة بسيطة وفعالة.

### الاستخدام
لإنشاء مثيل جديد من WebkitRTCPeerConnection، يتم استخدام الكود التالي:

```javascript
const configuration = {
    iceServers: [
        { urls: 'stun:stun.l.google.com:19302' } // خادم STUN
    ]
};

const peerConnection = new webkitRTCPeerConnection(configuration);
```

### التفاصيل
- **الخصائص**: 
  - `iceConnectionState`: حالة الاتصال.
  - `localDescription`: الوصف المحلي للاتصال.
  - `remoteDescription`: الوصف البعيد للاتصال.
  
- **الطرق**:
  - `createOffer()`: لإنشاء عرض اتصال.
  - `createAnswer()`: لإنشاء رد على العرض.
  - `addIceCandidate()`: لإضافة مرشح ICE.

## الأمثلة
### مثال أساسي لإنشاء اتصال
```javascript
const peerConnection = new webkitRTCPeerConnection();

peerConnection.createOffer().then(offer => {
    return peerConnection.setLocalDescription(offer);
}).then(() => {
    // أرسل العرض إلى الطرف الآخر
}).catch(error => {
    console.error('Error creating offer:', error);
});
```

### مثال على إضافة مرشح ICE
```javascript
const candidate = new RTCIceCandidate({
    sdpMLineIndex: 0,
    sdpMid: '0',
    candidate: 'candidate:0 1 UDP 2122252543 192.168.1.2 12345 typ host'
});

peerConnection.addIceCandidate(candidate).then(() => {
    console.log('ICE Candidate added successfully.');
}).catch(error => {
    console.error('Error adding ICE Candidate:', error);
});
```

## الشرح
### المشاكل الشائعة
- **التوافق**: WebkitRTCPeerConnection قد لا يكون مدعومًا في جميع المتصفحات. يُفضل استخدام واجهة RTCPeerConnection القياسية بدلاً منها إذا كان متاحًا.
- **إعداد ICE**: قد تواجه مشكلات في إعداد مرشحات ICE إذا لم يكن هناك خادم STUN أو TURN صحيح.

### ملاحظات إضافية
- تأكد من أن لديك أذونات الوصول إلى الميكروفون والكاميرا قبل بدء الاتصال.
- تتطلب بعض الميزات الاتصالات الآمنة (HTTPS) لتعمل بشكل صحيح.

## ملخص جملة واحدة
WebkitRTCPeerConnection هي واجهة برمجية في JavaScript تسهل إنشاء اتصالات صوت وفيديو في الوقت الحقيقي عبر المتصفحات.