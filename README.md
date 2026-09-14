# SOLID Principles in PHP

أمثلة عملية مبسطة لمبادئ **SOLID** باستخدام PHP، مع مقارنة بين التنفيذ الخاطئ والتنفيذ الصحيح.

[English](#english) · [العربية](#العربية)

---

<a id="العربية"></a>

## الفكرة

SOLID خمس قواعد تصميم تساعد على كتابة كود أوضح، أسهل في الصيانة، وأسهل في التوسعة.

كل مبدأ موجود في مجلد مستقل، وغالبًا يحتوي على:

| المجلد | المعنى |
|--------|--------|
| `wrong/` | المثال الذي يخالف المبدأ |
| `right/` | المثال الذي يطبّق المبدأ |

## المبادئ

| # | المبدأ | المجلد | باختصار |
|---|--------|--------|---------|
| 1 | **S**ingle Responsibility | [`1-SRP`](./1-SRP) | الكلاس له مسؤولية واحدة |
| 2 | **O**pen/Closed | [`2-OCP`](./2-OCP) | مفتوح للتمديد، مغلق للتعديل |
| 3 | **L**iskov Substitution | [`3-LSP`](./3-LSP) | الفرع يمكنه استبدال الأب بأمان |
| 4 | **I**nterface Segregation | [`4-ISP`](./4-ISP) | واجهات صغيرة بدل واجهة ضخمة |
| 5 | **D**ependency Inversion | [`5-DIP`](./5-DIP) | الاعتماد على تجريد وليس تنفيذ مباشر |

تفاصيل كل مبدأ موجودة داخل مجلده (مثل [`1-SRP/README.md`](./1-SRP/README.md)).

## هيكل المشروع

```text
SOLID/
├── 1-SRP/          # مسؤولية واحدة
├── 2-OCP/          # مفتوح للتمديد / مغلق للتعديل
├── 3-LSP/          # قابلية الاستبدال
├── 4-ISP/          # فصل الواجهات
├── 5-DIP/          # عكس الاعتماديات
└── README.md
```

## المتطلبات

- PHP 8+
- خادم محلي مثل [XAMPP](https://www.apachefriends.org/) أو PHP built-in server

## التشغيل

من مجلد المشروع:

```bash
php -S localhost:8000
```

ثم افتح في المتصفح أحد المسارات، مثل:

- [http://localhost:8000/1-SRP/](http://localhost:8000/1-SRP/)
- [http://localhost:8000/2-OCP/](http://localhost:8000/2-OCP/)
- [http://localhost:8000/3-LSP/](http://localhost:8000/3-LSP/)
- [http://localhost:8000/4-ISP/](http://localhost:8000/4-ISP/)
- [http://localhost:8000/5-DIP/](http://localhost:8000/5-DIP/)

مع XAMPP يمكن فتح المشروع عبر `http://localhost/SOLID/`.

## طريقة الاستفادة

1. اقرأ المثال داخل `wrong/` وافهم المشكلة.
2. قارنه بالمثال داخل `right/`.
3. ركّز على التصميم (الواجهات والتقسيم)، وليس على تفاصيل PHP المتقدمة.

هذا مستودع تعليمي، وليس تطبيق إنتاج.

## الترخيص

للاستخدام التعليمي. يمكنك نسخ الأمثلة والتعديل عليها بحرية.

---

<a id="english"></a>

## About

Practical PHP examples for the five **SOLID** design principles. Each principle lives in its own folder, usually with a `wrong/` (anti-pattern) and `right/` (correct) version.

## Principles

1. **SRP** — a class should have one reason to change.
2. **OCP** — open for extension, closed for modification.
3. **LSP** — subclasses must be substitutable for their base types.
4. **ISP** — prefer small, focused interfaces.
5. **DIP** — depend on abstractions, not concrete implementations.

## Requirements

PHP 8+ and a local server (XAMPP or `php -S localhost:8000`).

## License

Educational use. Feel free to copy and adapt the examples.
