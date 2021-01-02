# ติดตั้ง laravel permission

doc  
[https://docs.spatie.be/laravel-permission/v3/introduction/](https://docs.spatie.be/laravel-permission/v3/introduction/)

[Copy the required files](https://docs.spatie.be/laravel-permission/v3/installation-lumen/)

```text
cp vendor/spatie/laravel-permission/database/migrations/create_permission_tables.php.stub database/migrations/2018_01_01_000000_create_permission_tables.php
```

[register the middlewares](https://docs.spatie.be/laravel-permission/v3/installation-lumen/)

bootstrap\app.php

```text
$app->routeMiddleware([
    'permission' => Spatie\Permission\Middlewares\PermissionMiddleware::class,
    'role' => Spatie\Permission\Middlewares\RoleMiddleware::class,
]);
```

[service provider](https://docs.spatie.be/laravel-permission/v3/installation-lumen/)

bootstrap\app.php

```text
$app->register(Spatie\Permission\PermissionServiceProvider::class);
```

run your migrations

```text
php artisan migrate
```

