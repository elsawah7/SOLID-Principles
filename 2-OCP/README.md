# OCP — Open/Closed Principle

> الكلاس مفتوح للتمديد، ومغلق للتعديل.

[العودة للمشروع](../README.md)

## الفكرة

إضافة طريقة دفع جديدة يجب أن تتم بكلاس جديد، بدون تعديل كلاس الدفع الأساسي.

| المجلد | المعنى |
|--------|--------|
| `wrong/` | `Payment` يعتمد على `if/elseif` لكل بنك |
| `right/` | الجميع يطبّق `PaymentInterface` |

## الهيكل

```text
2-OCP/
├── index.php
├── wrong/
│   ├── Payment.php
│   ├── Cib.php
│   ├── Alahly.php
│   ├── Paypal.php
│   ├── Qnb.php
│   └── API/
└── right/
    ├── Payment.php
    ├── PaymentInterface.php
    ├── Stripe.php
    ├── Paypal.php
    ├── Cib.php
    ├── Alahly.php
    └── Qnb.php
```

## الخطأ والصحيح

**خطأ:** كل طريقة دفع جديدة تفرض تعديل `Payment`.

```php
public function getPaymentAcount($type)
{
    if ($type == "cib") {
        return new Cib();
    } elseif ($type == "paypal") {
        return new Paypal();
    }
}
```

**صحيح:** الاعتماد على واجهة، ثم حقن التنفيذ.

```php
class Payment
{
    public function __construct(PaymentInterface $account) {}
}
```

لإضافة Stripe أو QNB يكفي كلاس جديد يطبّق `PaymentInterface`.
