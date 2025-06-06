# [لينكس] C Shell (csh) yum الاستخدام: إدارة الحزم

## Overview
يعتبر أمر `yum` أداة قوية لإدارة الحزم في أنظمة التشغيل المعتمدة على لينكس. يتيح للمستخدمين تثبيت، تحديث، وإزالة البرمجيات بسهولة، مع إدارة التبعيات تلقائيًا.

## Usage
تكون الصيغة الأساسية لأمر `yum` كما يلي:

```bash
yum [options] [arguments]
```

## Common Options
- `install`: لتثبيت حزمة جديدة.
- `remove`: لإزالة حزمة مثبتة.
- `update`: لتحديث حزمة موجودة إلى أحدث إصدار.
- `search`: للبحث عن حزم معينة.
- `list`: لعرض قائمة الحزم المثبتة أو المتاحة.

## Common Examples
- لتثبيت حزمة جديدة:
  ```bash
  yum install package_name
  ```

- لإزالة حزمة مثبتة:
  ```bash
  yum remove package_name
  ```

- لتحديث حزمة معينة:
  ```bash
  yum update package_name
  ```

- للبحث عن حزمة:
  ```bash
  yum search package_name
  ```

- لعرض قائمة الحزم المثبتة:
  ```bash
  yum list installed
  ```

## Tips
- تأكد من تحديث قاعدة بيانات الحزم بانتظام باستخدام `yum update`.
- استخدم خيار `-y` لتأكيد جميع العمليات تلقائيًا دون الحاجة لتأكيد يدوي.
- تحقق من التبعيات قبل تثبيت حزمة جديدة لتجنب المشاكل المحتملة.