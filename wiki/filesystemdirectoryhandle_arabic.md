<!--
Meta Description: # واجهة FileSystemDirectoryHandle في JavaScript: طريقة فعالة للتعامل مع أنظمة الملفات ## الملخص تتيح واجهة `FileSystemDirectoryHandle` في JavaScript ل...
Meta Keywords: الملفات, filesystemdirectoryhandle, على, const, directoryhandle
-->

# واجهة FileSystemDirectoryHandle في JavaScript: طريقة فعالة للتعامل مع أنظمة الملفات

## الملخص
تتيح واجهة `FileSystemDirectoryHandle` في JavaScript للمطورين التعامل مع الأدلة (المجلدات) على نظام الملفات بشكل مباشر، مما يسهل عمليات القراءة والكتابة وإدارة الملفات.

## التوثيق
تعتبر واجهة `FileSystemDirectoryHandle` جزءًا من واجهة `File System Access API`، وهي تسمح للمستخدمين بالتفاعل مع ملفاتهم ومجلداتهم بشكل آمن من خلال متصفح الويب. توفر هذه الواجهة وظائف لإنشاء، قراءة، وكتابة الملفات داخل الأدلة.

### الهدف
الهدف من `FileSystemDirectoryHandle` هو تمكين المطورين من الوصول إلى نظام الملفات الخاص بالمستخدم بطريقة آمنة وسهلة.

### الاستخدام
للاستخدام الفعلي لـ `FileSystemDirectoryHandle`، يجب أولاً طلب الوصول إلى دليل معين من خلال واجهة المستخدم. بعد الحصول على الإذن، يمكن للمطور استخدام الدوال المتاحة في الواجهة لإدارة الملفات.

### التفاصيل
- **الطرق الرئيسية**:
  - `getFileHandle(name, options)`: للحصول على مقبض ملف داخل الدليل.
  - `getDirectoryHandle(name, options)`: للحصول على مقبض دليل فرعي.
  - `removeEntry(name, options)`: لحذف ملف أو دليل من الدليل.
  - `keys()`: للحصول على قائمة بمقابض الملفات والدلائل الفرعية.

## الأمثلة
### مثال 1: الحصول على مقبض دليل
```javascript
async function getDirectory() {
  const directoryHandle = await window.showDirectoryPicker();
  console.log(directoryHandle);
}
getDirectory();
```

### مثال 2: قراءة الملفات من دليل
```javascript
async function readFilesFromDirectory() {
  const directoryHandle = await window.showDirectoryPicker();
  for await (const entry of directoryHandle.values()) {
    if (entry.kind === 'file') {
      const fileHandle = entry;
      const file = await fileHandle.getFile();
      console.log(file.name);
    }
  }
}
readFilesFromDirectory();
```

### مثال 3: حذف ملف من دليل
```javascript
async function deleteFile() {
  const directoryHandle = await window.showDirectoryPicker();
  const fileHandle = await directoryHandle.getFileHandle('example.txt');
  await directoryHandle.removeEntry('example.txt');
  console.log('File deleted successfully.');
}
deleteFile();
```

## الشرح
عند استخدام `FileSystemDirectoryHandle`، يجب أن تكون واعيًا لبعض النقاط:
- تحتاج إلى التعامل مع الوعود (Promises) لأنها تعتمد على العمليات غير المتزامنة.
- تأكد من أن لديك الأذونات اللازمة للوصول إلى الملفات والدلائل.
- قد يختلف سلوك الواجهة حسب متصفح الويب المستخدم، لذا تأكد من اختبار الكود عبر مختلف المتصفحات.

## ملخص جملة واحدة
تعتبر واجهة `FileSystemDirectoryHandle` في JavaScript أداة قوية تتيح الوصول الآمن والمباشر إلى أنظمة الملفات والتفاعل معها.