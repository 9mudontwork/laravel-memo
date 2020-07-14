# การทำ route api versioning

## Guide

{% embed url="https://medium.com/parenting-tw/custom-api-versioning-route-file-in-laravel-b65e637dfbaf" %}



แก้ไข route middleware ในตัวแปร $middlewareGroups ที่ไฟล์

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

หลังจากนั้นเรียกใช้ method map route ที่สร้างขึ้น ใน method map\(\)

```php
$this->mapApiVersionOneRoutes();
```

