<!--
Meta Description: # حدث onended في JavaScript: الشرح والاستخدام ## ملخص حدث `onended` في JavaScript هو حدث يُستخدم في واجهة برمجة التطبيقات الخاصة بالوسائط (Media API) ...
Meta Keywords: onended, حدث, تشغيل, الحدث, استخدام
-->

# حدث onended في JavaScript: الشرح والاستخدام

## ملخص
حدث `onended` في JavaScript هو حدث يُستخدم في واجهة برمجة التطبيقات الخاصة بالوسائط (Media API) للإشارة إلى انتهاء تشغيل وسائط متعددة مثل الفيديو أو الصوت. يُعتبر هذا الحدث أداة قوية للمطورين للتفاعل مع نهاية المحتوى الصوتي أو المرئي.

## الوثائق
### الغرض
يهدف حدث `onended` إلى إبلاغ المطورين عندما تنتهي الوسائط من التشغيل، مما يتيح لهم تنفيذ إجراءات معينة في تلك اللحظة، مثل إعادة تشغيل الوسائط، أو تحميل محتوى جديد، أو تحديث واجهة المستخدم.

### الاستخدام
يمكن استخدام `onended` مع كائنات مثل `<audio>` أو `<video>` في HTML. يمكن للمطورين تعيين وظيفة callback تتعامل مع الحدث عندما يحدث.

### التفاصيل
لتعيين حدث `onended`، يمكن استخدام خاصية `onended` أو استخدام طريقة `addEventListener`. إليك كيفية القيام بذلك:

```javascript
const audioElement = document.getElementById('myAudio');

// باستخدام خاصية onended
audioElement.onended = function() {
    console.log('تم انتهاء التشغيل!');
};

// باستخدام addEventListener
audioElement.addEventListener('ended', function() {
    console.log('انتهى التشغيل باستخدام addEventListener!');
});
```

## الأمثلة
### مثال 1: استخدام onended مع عنصر صوت
```html
<audio id="myAudio" controls>
    <source src="audio.mp3" type="audio/mpeg">
    متصفحك لا يدعم عنصر الصوت.
</audio>

<script>
const audioElement = document.getElementById('myAudio');

audioElement.onended = function() {
    alert('لقد انتهى تشغيل الصوت!');
};
</script>
```

### مثال 2: استخدام onended مع عنصر فيديو
```html
<video id="myVideo" width="320" height="240" controls>
    <source src="movie.mp4" type="video/mp4">
    متصفحك لا يدعم عنصر الفيديو.
</video>

<script>
const videoElement = document.getElementById('myVideo');

videoElement.onended = function() {
    console.log('انتهى تشغيل الفيديو!');
};
</script>
```

## الشرح
### الأخطاء الشائعة
- **عدم تفعيل الحدث**: تأكد من أنك قمت بربط الحدث بشكل صحيح بالعنصر. إذا لم يكن الكائن موجودًا في DOM، فلن يعمل الحدث.
- **عدم التعامل مع الأحداث المتعددة**: إذا كنت ترغب في التعامل مع أحداث متعددة، استخدم `addEventListener` بدلاً من تعيين `onended` مباشرة.
- **مشكلات التوافق**: تأكد من اختبار كودك في متصفحات متعددة، حيث قد تختلف سلوكيات الأحداث بين المتصفحات.

## ملخص جملة واحدة
حدث `onended` في JavaScript يُستخدم للإشارة إلى انتهاء تشغيل الوسائط، مما يسمح بتنفيذ إجراءات معينة عند انتهاء المحتوى الصوتي أو المرئي.