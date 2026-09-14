# SRP — Single Responsibility Principle

> الكلاس يجب أن يكون له سبب واحد فقط للتغيير.

[العودة للمشروع](../README.md)

## الفكرة

إذا تغيّر رفع الملفات أو طباعة الفاتورة، لا يجب أن يتأثر كلاس المنتج.

| المجلد | المعنى |
|--------|--------|
| `wrong/` | `Product` يدير المنتج ويرفع ملفات ويطبع فاتورة |
| `right/` | كل مسؤولية في كلاس مستقل |

## الهيكل

```text
1-SRP/
├── wrong/
│   ├── Product.php
│   └── User.php
└── right/
    ├── Product.php
    ├── UploadFile.php
    ├── Invoice.php
    ├── Order.php
    └── User.php
```

## الخطأ والصحيح

**خطأ:** كلاس واحد بعدة مسؤوليات.

```php
class Product
{
    public function create() {}
    public function uploadFile() {}
    public function printInvoice() {}
}
```

**صحيح:** تقسيم المسؤوليات.

- `Product` → إدارة المنتج
- `UploadFile` → رفع الملفات
- `Invoice` → الفواتير
- `Order` → الطلبات
