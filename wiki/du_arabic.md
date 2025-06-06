# [نظام التشغيل] C Shell (csh) du الاستخدام: عرض حجم الملفات والمجلدات

## نظرة عامة
أمر `du` (Disk Usage) يُستخدم لعرض حجم الملفات والمجلدات في نظام الملفات. يساعد هذا الأمر المستخدمين في معرفة مقدار المساحة التي تستهلكها الملفات والمجلدات، مما يسهل إدارة التخزين.

## الاستخدام
الصيغة الأساسية للأمر هي:

```
du [الخيارات] [المتغيرات]
```

## الخيارات الشائعة
- `-h`: عرض الحجم بصيغة قابلة للقراءة (مثل KB، MB).
- `-s`: عرض الحجم الإجمالي لمجلد معين فقط.
- `-a`: عرض حجم جميع الملفات والمجلدات.
- `-c`: عرض إجمالي المساحة المستخدمة بعد عرض الأحجام.

## أمثلة شائعة
- لعرض حجم مجلد معين بشكل قابل للقراءة:
  ```bash
  du -h /path/to/directory
  ```

- لعرض الحجم الإجمالي لمجلد:
  ```bash
  du -sh /path/to/directory
  ```

- لعرض حجم جميع الملفات والمجلدات في الدليل الحالي:
  ```bash
  du -ah
  ```

- لعرض الحجم الإجمالي لجميع الملفات والمجلدات في الدليل الحالي:
  ```bash
  du -ch
  ```

## نصائح
- استخدم الخيار `-h` لجعل قراءة الأحجام أسهل، خاصة عند التعامل مع ملفات كبيرة.
- إذا كنت تريد معرفة الحجم الإجمالي لمجلد دون تفاصيل، استخدم الخيار `-s`.
- تأكد من تشغيل الأمر في الدليل الصحيح للحصول على نتائج دقيقة.