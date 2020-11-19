# Scope

```php
<?php
namespace App\Models\Traits\Scope;

/**
 * เอาไว้ใช้กับ การ query เฉพาะ table
 * เวลาเรียก เรียก ->active() ได้เลย
 */
trait UserScope
{
    public function scopeActive($query)
    {
        return $query->where('active', 1);
    }
}

```

