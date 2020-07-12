---
description: >-
  เป็น package ที่ช่วยในการทำ authentication แบบ simple สำหรับ SPA ทำตาม
  document ได้เลย
---

# ทำ Auth ด้วย Sanctum

## Laravel Sanctum

{% embed url="https://laravel.com/docs/7.x/sanctum" %}

หลังจากทำตาม document เรียบร้อยแล้วให้สร้าง seeder ง่ายๆ สำหรับสร้าง user

```text
php artisan make:seeder UsersTableSeeder
```

```text
DB::table('users')->insert([
    'name' => 'admin',
    'email' => 'admin',
    'password' => Hash::make('admin')
]);
```

หลังจากนั้นก็ seed

```text
php artisan db:seed --class=UsersTableSeeder
```

