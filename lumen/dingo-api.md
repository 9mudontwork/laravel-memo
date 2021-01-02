# ติดตั้ง dingo api

doc  
[https://github.com/dingo/api/wiki](https://github.com/dingo/api/wiki)

register service provider

bootstrap\app.php

```text
$app->register(Dingo\Api\Provider\LumenServiceProvider::class);
```

clone config

```text
cp vendor\dingo\api\config\api.php config\api.php
```

### สร้าง routes

[Creating API Endpoints](https://github.com/dingo/api/wiki/Creating-API-Endpoints)

bootstrap\app.php

```text
$api = $app[Dingo\Api\Routing\Router::class];

$api->version('v1', [
    'namespace' => 'App\Http\Controllers\V1',
], function ($api) {
    require __DIR__ . '/../routes/v1/api.php';
});
```

routes\v1\api.php

```text
<?php

$api->get('/', function () {
    return [
        'message' => 'api v1',
        'branch' => 'dev-master',
    ];
});
```

ลบโค้ด routes\web.php

ลองเข้า [http://localhost:8000/](http://localhost:8000/)

ถ้าเจอ error  
Unable to boot ApiServiceProvider, configure an API domain or prefix.

config\api.php

```text
'domain' => env('API_DOMAIN', env('APP_URL', 'http://localhost:8000')),
```

