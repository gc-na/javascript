<!--
Meta Description: # واجهة FontFace في JavaScript: استخدامات وأمثلة ## ملخص واجهة FontFace في JavaScript تمكّن المطورين من تحميل الخطوط الخاصة واستخدامها في تطبيقاتهم. ت...
Meta Keywords: error, fontface, javascript, myfont, document
-->

# واجهة FontFace في JavaScript: استخدامات وأمثلة

## ملخص
واجهة FontFace في JavaScript تمكّن المطورين من تحميل الخطوط الخاصة واستخدامها في تطبيقاتهم. تتيح هذه الواجهة إضافة خطوط جديدة إلى الوثيقة بطريقة ديناميكية.

## الوثائق
تُستخدم واجهة FontFace لتعريف، تحميل، وإدارة الخطوط في الويب. يمكن أن تُستخدم هذه الواجهة لتحميل الخطوط من مصادر مختلفة، سواء كانت محلية أو عبر الإنترنت، مما يوفر مرونة أكبر في تصميم واجهات المستخدم.

### الاستخدام
لإنشاء مثيل جديد من FontFace، يمكن استخدام التركيب التالي:
```javascript
let myFont = new FontFace('MyFont', 'url(myfont.woff2)');
```
بعد إنشاء الخط، يجب إضافته إلى مستند الوثيقة باستخدام واجهة `document.fonts`:
```javascript
document.fonts.add(myFont);
```
لتحميل الخط، يجب استخدام دالة `load()`:
```javascript
myFont.load().then(function(loadedFont) {
  console.log('Font loaded:', loadedFont);
}).catch(function(error) {
  console.error('Failed to load font:', error);
});
```

## أمثلة
### مثال 1: تحميل خط بسيط
```javascript
let myFont = new FontFace('MyCustomFont', 'url(/path/to/font.woff)');

myFont.load().then(function(loadedFont) {
  document.fonts.add(loadedFont);
  document.body.style.fontFamily = 'MyCustomFont, sans-serif';
}).catch(function(error) {
  console.error('Error loading font:', error);
});
```

### مثال 2: استخدام عدة خطوط
```javascript
let font1 = new FontFace('FontOne', 'url(font1.woff)');
let font2 = new FontFace('FontTwo', 'url(font2.woff)');

Promise.all([font1.load(), font2.load()]).then(function(loadedFonts) {
  loadedFonts.forEach(font => document.fonts.add(font));
  document.body.style.fontFamily = 'FontOne, FontTwo, sans-serif';
}).catch(function(error) {
  console.error('Error loading fonts:', error);
});
```

## الشرح
- **مخاطر شائعة**: قد يحدث أن الخط المطلوب غير متوفر أو أن URL غير صحيح، مما يؤدي إلى فشل تحميل الخط.
- **نقاط يجب الانتباه لها**: تأكد من إضافة الخط إلى `document.fonts` بعد تحميله. إذا لم تقم بذلك، فلن يظهر الخط في المستند.
- **دعم المتصفحات**: تأكد من أن المتصفح الذي تستخدمه يدعم واجهة FontFace، حيث لا تدعم جميع المتصفحات هذه الواجهة.

## ملخص من جملة واحدة
واجهة FontFace في JavaScript تتيح للمطورين تحميل وإدارة الخطوط بشكل ديناميكي في تطبيقاتهم.