# SOLID - Single Responsibility Principle (SRP)

هذا المشروع هو مثال عملي لتوضيح مبدأ Single Responsibility Principle (SRP) من مبادئ SOLID في PHP.

## ما هو الهدف من المشروع؟

المشروع يوضح الفرق بين:

- كلاس يقوم بأكثر من مسؤولية في نفس الوقت.
- كلاس كلّ مسؤوليته واضحة ومحددة، ويغيّر فقط عندما تتغيّر الأسباب المرتبطة بتلك المسؤولية.

الفكرة الأساسية في SRP هي:

> كل كلاس يجب أن يكون له سبب واحد فقط للتغيير.

وذلك يعني أن الكلاس لا يجب أن يتعامل مع أكثر من مسؤولية مستقلة في النظام.

## لماذا هذا المبدأ مهم؟

عندما يضم الكلاس مسؤوليات متعددة، فإن أي تغيير في أحدها قد يؤثر على باقٍ من السلوك، وهذا يجعل التطبيق:

- أصعب في الصيانة.
- أكثر عرضة للأخطاء.
- أصعب في اختبار الوحدات.
- أصعب في التوسيع لاحقًا.

## هيكل المشروع

```text
1-SRP/
├── index.php
├── right/
│   ├── User.php
│   ├── Product.php
│   ├── Order.php
│   ├── Invoice.php
│   └── UploadFile.php
└── wrong/
    ├── User.php
    └── Product.php
```

## مثال على الكلاس الذي يخالف SRP

في مجلد `wrong`، يوجد مثال غير صحيح:

```php
class Product
{
    public function create() {}
    public function store() {}
    public function edit() {}
    public function update() {}
    public function uploadFile() {}
    public function printInvoice() {}
}
```

هذا الكلاس يتعامل مع عدة مسؤوليات في آن واحد:

- إدارة المنتجات
- رفع الملفات
- طباعة الفاتورة

إذا تغيرت منطق رفع الملفات أو طباعة الفواتير، فسيُضطر هذا الكلاس للتغيير، رغم أنه لا علاقة له مباشرة بإدارة المنتجات.

## مثال على الكلاس الذي يلتزم بـ SRP

في مجلد `right`، تم تقسيم المسؤوليات:

```php
class Product
{
    public function create() {}
    public function store() {}
    public function edit() {}
    public function update() {}
}
```

```php
class UploadFile
{
    public function upload() {}
}
```

```php
class Invoice
{
    public function printInvoice($data) {}
}
```

```php
class Order
{
    public function makeOrder($order) {}
}
```

كل كلاس هنا له مسؤولية واحدة واضحة:

- `Product` → إدارة المنتجات
- `UploadFile` → رفع الملفات
- `Invoice` → طباعة الفواتير
- `Order` → إدارة الطلبات

## لماذا هذا مثال جيد؟

لأن كل كلاس له "سبب واحد فقط للتغيير".

مثال:

- إذا تغيرت سياسة رفع الملفات، فالتغيير يخص `UploadFile` فقط.
- إذا تغيرت طريقة عرض الفاتورة، فالتغيير يخص `Invoice` فقط.
- إذا تغيرت منطق الطلبات، فالتغيير يخص `Order` فقط.

هذا يجعل النظام أكثر تنظيمًا وسهولة في التطوير والصيانة.

## الخلاصة

مبدأ Single Responsibility Principle يساعد على كتابة كود:

- أنظف
- أسهل في القراءة
- أسهل في الصيانة
- أقل عرضة للأخطاء
- أسهل في التوسع

## ملاحظة

هذا المشروع مثال تعليمي بسيط يركز فقط على فهم المبدأ، وهو ليس تطبيقًا كاملًا أو مشروعًا تجاريًا، بل أداة لتعليم مبادئ SOLID بشكل عملي.
