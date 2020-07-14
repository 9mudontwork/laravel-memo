# การทำ route api versioning เบื้องต้น

## Reference

{% embed url="https://medium.com/parenting-tw/custom-api-versioning-route-file-in-laravel-b65e637dfbaf" %}

{% embed url="https://www.mynotepaper.com/laravel-api-versioning-with-api-key-in-simple-method/" %}



แก้ไข route middleware ในตัวแปร `$middlewareGroups` ที่ไฟล์

```php
app\Http\Kernel.php
```

คัดลอกโค้ด array api ของเก่าแล้วเพิ่มเข้าไป

```php
'api.v1' => [
    'throttle:60,1',
    \Illuminate\Routing\Middleware\SubstituteBindings::class,
],
```

หลังจากนั้นแก้ map route ที่ไฟล์

```text
app\Providers\RouteServiceProvider.php
```

สร้าง method เอาไว้กำหนด namesapce version

```php
private function getApiNamespace($versionNumber)
{
    return "{$this->namespace}\Api\V{$versionNumber}";
}
```

สร้าง method สำหรับ map route

```php
protected function mapApiVersionOneRoutes()
{
    Route::prefix('api/v1')
        ->middleware('api.v1')
        ->namespace($this->getApiNamespace(1))
        ->group(base_path('routes/api/v1.php'));
}
```

หลังจากนั้นเรียกใช้ method map route ที่สร้างขึ้น ใน method `map()`

```php
$this->mapApiVersionOneRoutes();
```

สร้างไฟล์ `v1.php` ที่

```php
routes\api
```

กำหนด route เริ่มต้น

```php
<?php

use Illuminate\Http\Request;
use Illuminate\Support\Facades\Route;

Route::get('/', 'WelcomeController@index');

```

ใช้คำสั่ง `artisan` เพื่อสร้างไฟล์ `controller`

```bash
php artisan make:controller API\V1\WelcomeController
```

```php
<?php

namespace App\Http\Controllers\API\V1;

use App\Http\Controllers\Controller;
use Illuminate\Http\Request;

class WelcomeController extends Controller
{
    public function index()
    {
        $response = [
            'message' => "olomanga API V1",
        ];

        return response()->json($response, 200);
    }
}
```

