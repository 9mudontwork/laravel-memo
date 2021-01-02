# ติดตั้ง laravel cors

doc  
[https://github.com/spatie/laravel-cors](https://github.com/spatie/laravel-cors)

[middleware](https://github.com/spatie/laravel-cors#lumen)

```text
$app->middleware([
    Spatie\Cors\Cors::class,
]);
```

[service provider](https://github.com/spatie/laravel-cors#lumen)

bootstrap\app.php

```text
$app->register(Spatie\Cors\CorsServiceProvider::class);
```

