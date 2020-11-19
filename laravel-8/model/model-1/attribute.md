# Attribute

```php
<?php

namespace App\Models\Traits\Attribute;

use Illuminate\Support\Facades\Hash;

/**
 * เอาไว้ set attribute ที่ทำหนดขึ้นเอง
 */
trait UserAttribute
{
    public function getProfileImageAttribute()
    {
        return $this->getAvatar();
    }
}

```

