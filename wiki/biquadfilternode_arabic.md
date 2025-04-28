<!--
Meta Description: # BiquadFilterNode في JavaScript: مرشح ترددي ثنائي ## ملخص BiquadFilterNode هو كائن في واجهة برمجة تطبيقات Web Audio في JavaScript، يستخدم لإنشاء مرشح...
Meta Keywords: audiocontext, biquadfilternode, الصوت, التردد, مرشح
-->

# BiquadFilterNode في JavaScript: مرشح ترددي ثنائي

## ملخص
BiquadFilterNode هو كائن في واجهة برمجة تطبيقات Web Audio في JavaScript، يستخدم لإنشاء مرشحات ترددية ثنائية يمكنها معالجة الصوت بطرق متعددة، مثل التصفية من خلال المدى الترددي.

## الوثائق
BiquadFilterNode هو جزء من واجهة Web Audio API، ويستخدم لمعالجة الإشارات الصوتية من خلال تطبيق مرشحات مختلفة مثل مرشح منخفض التردد، مرشح عالي التردد، ومرشح نطاق. يمكن استخدامه في إنشاء تأثيرات صوتية معقدة وتجربة صوتية غامرة.

### الهدف
يهدف BiquadFilterNode إلى توفير طريقة سهلة وفعالة لتصفية الإشارات الصوتية في التطبيقات التي تتطلب معالجة صوتية متقدمة.

### الاستخدام
لاستخدام BiquadFilterNode، يجب أولاً إنشاء كائن AudioContext، ثم إنشاء مرشح باستخدام BiquadFilterNode. يمكن ضبط خصائص المرشح مثل نوع المرشح (lowpass، highpass، bandpass، إلخ) والتردد والجودة. 

### التفاصيل
- **الأنواع**: يمكن ضبط أنواع المرشحات باستخدام الخاصية `type`.
- **التردد**: يتم تعيين التردد باستخدام الخاصية `frequency`.
- **الجودة**: تُحدد جودة المرشح بواسطة الخاصية `Q`.
- **الزيادة**: يمكن استخدام خاصية `gain` لضبط مستوى الصوت.

## أمثلة
### مثال أساسي لإنشاء مرشح ترددي ثنائي

```javascript
// إنشاء كائن AudioContext
const audioContext = new (window.AudioContext || window.webkitAudioContext)();

// إنشاء BiquadFilterNode
const biquadFilter = audioContext.createBiquadFilter();

// ضبط نوع المرشح
biquadFilter.type = 'lowpass'; // مرشح منخفض التردد

// ضبط التردد
biquadFilter.frequency.setValueAtTime(440, audioContext.currentTime); // 440 هرتز

// توصيل المرشح بمصدر الصوت (مثل OscillatorNode)
const oscillator = audioContext.createOscillator();
oscillator.connect(biquadFilter);
biquadFilter.connect(audioContext.destination);

// بدء تشغيل الصوت
oscillator.start();
```

## الشرح
عند استخدام BiquadFilterNode، من المهم الانتباه إلى عدة نقاط:
- تأكد من أن AudioContext في حالة التشغيل قبل بدء تشغيل الصوت.
- ضبط التردد وQ بشكل دقيق يمكن أن يؤثر بشكل كبير على جودة الصوت الناتج.
- بعض المتصفحات قد تحتاج إلى تهيئة AudioContext في حدث تفاعلي، مثل نقرة على زر.

## ملخص جملة واحدة
BiquadFilterNode هو كائن في Web Audio API يستخدم لتطبيق مرشحات ترددية ثنائية على الإشارات الصوتية لتحسين جودة الصوت وتجربة المستخدم.