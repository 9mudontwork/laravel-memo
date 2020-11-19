# Relationship

```php
<?php

namespace App\Models\Traits\Relationship;

use App\Models\Profile;

/**
 * เอาไว้ใช้กับ relation
 */
trait UserRelationship
{
    public function profile()
    {
        return $this->hasOne(Profile::class, 'user_id');
    }
}

```

