# LSP — Liskov Substitution Principle

> الكلاس الفرعي يجب أن يُستخدم مكان الأب دون كسر السلوك المتوقع.

[العودة للمشروع](../README.md)

## الفكرة

إذا دالة تتوقع `File` وتستدعي `write()`، فإن `ReadOnlyFile` لا يجب أن يرمي استثناء عند الكتابة. هذا يكسر عقد الأب.

## الهيكل

```text
3-LSP/
├── index.php
├── File.php
├── ReadOnlyFile.php
└── user/
    ├── Employee.php
    ├── Manager.php
    ├── Supervisor.php
    └── index.php
```

هذا المجلد ليس مقسومًا إلى `wrong/` و `right/`؛ المثال يوضح المخالفة مباشرة.

## المشكلة

`ReadOnlyFile` يرث `File` ثم يخالف عقد `write()`:

```php
class ReadOnlyFile extends File
{
    public function write($data)
    {
        throw new Exception("you can not write into file");
    }
}
```

أي كود يتعامل مع الأب كأنه قابل للكتابة سينكسر عند استبدال الفرع.

**الاتجاه الصحيح:** لا ترث من نوع يعد بالكتابة إن كان الملف للقراءة فقط. استخدم واجهة أضيق (مثل القراءة فقط) بدل وراثة تكسر العقد.

مثال `user/` يوضح علاقات الموظفين بنفس الفكرة: الفرع لا يغيّر معنى سلوك الأب.
