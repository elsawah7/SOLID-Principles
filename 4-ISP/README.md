# ISP — Interface Segregation Principle

> لا تجبر الكلاس على تنفيذ دوال لا يستخدمها.

[العودة للمشروع](../README.md)

## الفكرة

سيارة بنزين لا تحتاج `electricEngin()`، وسيارة كهربائية لا تحتاج `oileEngin()`. واجهة واحدة ضخمة تجبر الاثنين على تنفيذ ما لا يخصهما.

| المجلد | المعنى |
|--------|--------|
| `wrong/` | `CarInterface` تجمع كل الدوال |
| `right/` | واجهات صغيرة حسب النوع |

## الهيكل

```text
4-ISP/
├── index.php
├── wrong/
│   ├── CarInterface.php
│   ├── Tesla.php
│   └── Toyota.php
└── right/
    ├── CarInterface.php
    ├── ElectricCarInterface.php
    ├── OilCarInterface.php
    ├── Tesla.php
    └── Toyota.php
```

## الخطأ والصحيح

**خطأ:** واجهة واحدة لكل السيارات.

```php
interface CarInterface
{
    public function oileEngin();
    public function electricEngin();
    public function openTheDoor();
    public function fireTheEngin();
}
```

**صحيح:** فصل الواجهات.

- `CarInterface` → الباب وتشغيل المحرك
- `ElectricCarInterface` → المحرك الكهربائي
- `OilCarInterface` → محرك البنزين

كل سيارة تنفّذ ما تحتاجه فقط.
