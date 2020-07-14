# การทำ route api versioning

แก้ไขที่ไฟล์

```text
app\Providers\RouteServiceProvider.php
```

สร้าง method เอาไว้กำหนด namesapce version

```php
private function getApiNamespace($versionNumber)
{
    return "{$this->namesapce}\Api\V{$versionNumber}";
}
```

สร้าง method สำหรับ map route

```php
protected function mapApiVersionOneRoutes()
{
    Route::prefix('api/v1')
        ->middleware('api.v1')
        ->namespace($this->getApiNamespace(1))
        ->group(base_path('routes/v1/api.php'));
}
```

หลังจากนั้นเรียกใช้ method map route ที่สร้างขึ้น ใน method map\(\)

```php
$this->mapApiVersionOneRoutes();
```

