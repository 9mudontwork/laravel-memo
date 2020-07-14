---
description: package ช่วยจำกัด url ในการเข้าถึง api (เป็น default อยู่ใน version 7)
---

# Laravel CORS

{% embed url="https://github.com/fruitcake/laravel-cors" %}

ไฟล์ที่เกี่ยวข้องกับ package นี้

```text
config\cors.php
```

```text
app\Http\Kernel.php
```

```php
\Fruitcake\Cors\HandleCors::class,
```

หากต้องการปิด CSRF ปิดที่ app\Http\Kernel.php แล้ว comment โค้ดด้านล่าง

```php
\App\Http\Middleware\VerifyCsrfToken::class,
```

