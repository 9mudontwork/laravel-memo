# ติดตั้ง lumen passport

doc  
[https://github.com/dusterio/lumen-passport](https://github.com/dusterio/lumen-passport)

bootstrap\app.php

```text
$app->register(Laravel\Passport\PassportServiceProvider::class);
$app->register(Dusterio\LumenPassport\PassportServiceProvider::class);
```

config\auth.php

```text
return [
    'defaults' => [
        'guard' => 'api',
        'passwords' => 'users',
    ],

    'guards' => [
        'api' => [
            'driver' => 'passport',
            'provider' => 'users',
        ],
    ],

    'providers' => [
        'users' => [
            'driver' => 'eloquent',
            'model' => \App\User::class
        ]
    ]
];
```

### ตั้งค่า Authentication

\*\*\*\*[Custom Authentication Providers](https://github.com/dingo/api/wiki/Authentication#user-content-custom-authentication-providers)  
ใช้ dingo เป็นตัวกรอง auth

app\Providers\GuardServiceProvider.php

```text
namespace App\Providers;

use Dingo\Api\Auth\Provider\Authorization;
use Dingo\Api\Routing\Route;
use Illuminate\Http\Request;
use Symfony\Component\HttpKernel\Exception\UnauthorizedHttpException;

class GuardServiceProvider extends Authorization
{
    public function authenticate(Request $request, Route $route)
    {
        $this->validateAuthorizationHeader($request);

        if (!$user = app('auth')->user()) {
            throw new UnauthorizedHttpException(
                get_class($this),
                'Unable to authenticate with invalid API key and token.'
            );
        }
        return $user;
    }

    public function getAuthorizationMethod()
    {
        return 'bearer';
    }
}

```

[Configuring Authentication Providers](https://github.com/dingo/api/wiki/Authentication#configuring-authentication-providers)  
ใช้ lumen passport กับ dingo

bootstrap\app.php

```text
$app[Dingo\Api\Auth\Auth::class]->extend('passport', function ($app) {
    return $app[App\Providers\GuardServiceProvider::class];
});
```

[Registering Routes](https://github.com/dusterio/lumen-passport#registering-routes)

app\Providers\AppServiceProvider.php

```text
public function register()
{
    LumenPassport::routes($this->app->router, [
        // 'prefix' => 'v1/oauth',
    ]);
}
```

[Migrate and install Laravel Passport](https://github.com/dusterio/lumen-passport#migrate-and-install-laravel-passport)

สร้าง table สำหรับ passport

```text
php artisan migrate
```

install key และอื่น ๆ ที่จำเป็น

```text
php artisan passport:install
```

[Installed routes](https://github.com/dusterio/lumen-passport#installed-routes)

มีไฟล์เพิ่มเข้ามา

storage\oauth-private.key  
storage\oauth-public.key

ถ้าจะ install ใหม่

```text
php artisan migrate:fresh --force
```

ต่อไปสร้างฐานข้อมูล user

## ถ้าติดปัญหา ให้ดู issue นี้

{% embed url="https://github.com/laravel/passport/issues/1274" %}



{% embed url="https://github.com/dusterio/lumen-passport/issues/136" %}



