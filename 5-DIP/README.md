# DIP — Dependency Inversion Principle

> الوحدات العليا تعتمد على تجريد (واجهة)، وليس على تنفيذ مباشر.

[العودة للمشروع](../README.md)

## الفكرة

`ExportFile` لا يجب أن يرتبط بـ `ExportPdf` حصرًا. الاعتماد على `ExportFileInterface` يسمح بتبديل PDF أو CSV أو XML بدون تعديل الكلاس الأساسي. نفس الفكرة مع قاعدة البيانات عبر `DatabaseInterface`.

| المجلد | المعنى |
|--------|--------|
| `wrong/` | `ExportFile` يعتمد على `ExportPdf` مباشرة |
| `right/` | الاعتماد على واجهات للتصدير وقاعدة البيانات |

## الهيكل

```text
5-DIP/
├── index.php
├── wrong/
│   ├── ExportFile.php
│   ├── ExportPdf.php
│   └── ExportCsv.php
└── right/
    ├── ExportFile.php
    ├── ExportFileInterface.php
    ├── ExportPdf.php
    ├── ExportCsv.php
    ├── ExportXml.php
    └── Database/
        ├── DatabaseInterface.php
        ├── DB.php
        ├── MysqlDB.php
        └── SqlliteDB.php
```

## الخطأ والصحيح

**خطأ:** ارتباط بتنفيذ محدد.

```php
class ExportFile
{
    public function __construct(ExportPdf $export) {}
}
```

**صحيح:** الارتباط بواجهة.

```php
class ExportFile
{
    public function __construct(ExportFileInterface $export) {}
}
```

يمكن تمرير أي تنفيذ يطبّق الواجهة: PDF أو CSV أو XML، ونفس الأسلوب مع MySQL أو SQLite.
