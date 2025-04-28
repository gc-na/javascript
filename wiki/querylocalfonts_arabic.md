<!--
Meta Description: # استعلام الخطوط المحلية في جافا سكريبت: queryLocalFonts ## ملخص `queryLocalFonts` هي دالة في جافا سكريبت تتيح للمطورين استعلام الخطوط المثبتة محليًا ...
Meta Keywords: الخطوط, querylocalfonts, على, المستخدم, font
-->

# استعلام الخطوط المحلية في جافا سكريبت: queryLocalFonts

## ملخص
`queryLocalFonts` هي دالة في جافا سكريبت تتيح للمطورين استعلام الخطوط المثبتة محليًا على نظام المستخدم. تعتبر هذه الميزة مهمة لتخصيص تجربة المستخدم واستغلال الخطوط المتاحة في تصميم الويب.

## الوثائق
### الغرض
تسهل دالة `queryLocalFonts` عملية الوصول إلى قائمة الخطوط المثبتة على جهاز المستخدم. هذا يمكن أن يساعد المطورين في تحسين واجهات المستخدم وجعلها أكثر توافقًا مع الخطوط التي قد تكون متاحة على أجهزة مختلفة.

### الاستخدام
تُستخدم `queryLocalFonts` لاسترجاع قائمة بجميع الخطوط المتاحة محليًا. تتطلب الدالة تنفيذًا بسيطًا، حيث يمكن استخدامها كالتالي:

```javascript
async function getLocalFonts() {
    const fonts = await queryLocalFonts();
    console.log(fonts);
}
```

### التفاصيل
- **المدخلات**: لا تتطلب `queryLocalFonts` أي مدخلات.
- **المخرجات**: تُرجع Promise تحتوي على مصفوفة من كائنات الخطوط، حيث يمثل كل كائن معلومات عن خط معين، مثل الاسم، الوزن، ونمط الخط.

## أمثلة
### مثال أساسي
```javascript
async function displayLocalFonts() {
    try {
        const fonts = await queryLocalFonts();
        fonts.forEach(font => {
            console.log(`اسم الخط: ${font.family}, الوزن: ${font.weight}, النمط: ${font.style}`);
        });
    } catch (error) {
        console.error("حدث خطأ أثناء استعلام الخطوط المحلية:", error);
    }
}

displayLocalFonts();
```

### مثال آخر
```javascript
async function filterFonts() {
    const fonts = await queryLocalFonts();
    const sansSerifFonts = fonts.filter(font => font.style === 'normal' && font.weight === '400');
    console.log('خطوط Sans Serif العادية:', sansSerifFonts);
}

filterFonts();
```

## الشرح
### الأخطاء الشائعة
- **عدم دعم المتصفح**: تأكد من أن المتصفح الذي تستخدمه يدعم `queryLocalFonts`. قد لا تكون هذه الميزة متاحة في جميع المتصفحات.
- **التعامل مع الوعود**: تأكد من استخدام `await` أو `.then()` عند استدعاء `queryLocalFonts`، حيث أن هذه الدالة تُرجع Promise.

### ملاحظات إضافية
- يمكن استخدام `queryLocalFonts` لتحسين تجربة المستخدم من خلال تكييف الخطوط المعروضة بناءً على الخطوط المتاحة بالفعل على الجهاز.
- تحقق من أذونات المستخدم، إذ قد تتطلب بعض المتصفحات إذنًا خاصًا للوصول إلى الخطوط المثبتة.

## ملخص بجملة واحدة
تعتبر دالة `queryLocalFonts` أداة قوية في جافا سكريبت لاستعلام الخطوط المحلية المتاحة على جهاز المستخدم، مما يعزز تجربة التصميم والتفاعل.