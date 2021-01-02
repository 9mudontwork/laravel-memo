# ตั้งค่า lumen

doc  
[https://lumen.laravel.com/docs/6.x](https://lumen.laravel.com/docs/6.x)  
[https://laravel.com/docs/6.x/](https://laravel.com/docs/6.x/)

create folder

```text
config
```

clone config

```text
cp vendor\laravel\lumen-framework\config\app.php config\app.php

cp vendor\laravel\lumen-framework\config\auth.php config\auth.php

cp vendor\laravel\lumen-framework\config\database.php config\database.php

cp vendor\spatie\laravel-cors\config\cors.php config\cors.php

cp vendor\spatie\laravel-permission\config\permission.php config\permission.php

cp vendor\vinkla\hashids\config\hashids.php config\hashids.php
```

config\setting.php

```text
return [
    'permission' => [
        'role_names' => [
            'system' => 'system',
            'admin' => 'admin',
        ],
        'permission_names' => [
            'view_backend' => 'view backend',
            'manage_authorization' => 'manage authorization',
        ],
    ],

    'api' => [
        'throttle' => [
            'expires' => 1,
            'limit' => 30,
        ],
        'token' => [
            'access_token_expire' => 60 * 24, // 1day
            'refresh_token_expire' => 60 * 24 * 2, // 2days
        ]
    ],

    'formats' => [
        'date' => 'd/m/Y',
        'time_12' => 'h:i:s A',
        'time_24' => 'H:i:s',
        'datetime_12' => 'd/m/Y h:i:s A',
        'datetime_24' => 'd/m/Y H:i:s',
    ],
];
```

bootstrap\app.php

```text
$app->withFacades();
$app->withEloquent();

// dingo api
$app->configure('api');

// lumen passport
$app->configure('auth');

// cors
$app->configure('cors');

// database
$app->configure('database');

// hashids
$app->configure('hashids');

// permission
$app->configure('permission');
$app->alias('cache', \Illuminate\Cache\CacheManager::class);
```

.env config

```text
APP_NAME=Lumen
APP_ENV=local
APP_KEY=
APP_DEBUG=true
APP_URL=http://localhost:8000
APP_TIMEZONE=Asia/Bangkok

LOG_CHANNEL=stack
LOG_SLACK_WEBHOOK_URL=

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=lumen_db
DB_USERNAME=root
DB_PASSWORD=

CACHE_DRIVER=file
QUEUE_CONNECTION=sync
```

