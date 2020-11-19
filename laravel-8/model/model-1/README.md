# Model

```php
<?php

namespace App\Models;

use App\Models\Traits\Attribute\UserAttribute;
use App\Models\Traits\Method\UserMethod;
use App\Models\Traits\Relationship\UserRelationship;
use Illuminate\Foundation\Auth\User as Authenticatable;

/**
 * Illuminate\Foundation\Auth\User
 * เป็น class ที่เตรียมทุกอย่างสำหรับทำ auth ไว้ จะมี Illuminate\Database\Eloquent\Model อยู่แล้ว
 */
class User extends Authenticatable
{
    use UserAttribute;
    use UserMethod;
    use UserRelationship;

    public const TYPE_USER = 'member';
    public const TYPE_SITE = 'PARK';
    public const TYPE_ACTIVE = 1;

    const CREATED_AT = 'created_at';
    const UPDATED_AT = 'updated_at';

    protected $table = 'users';

    /**
     * field ที่เปิดใช้งาน
     */
    protected $fillable = [
        'id',
        'username',
        'email',
        'password',
        'access_token',
        'site',
        'active',
        'registration_ip',
        'last_login_at',
        'created_at',
        'updated_at',
    ];

    /**
     * atrribute properties ที่กำหนดเอง
     * ต้องตั้งชื่อเป็น snake_case
     * จะสามารถใช้งานได้หลังจาก login เช่น auth()->user()->profile_image
     * เป็น magic method จะต้องสร้าง method ชื่อ getProfileImageAttribute (มี get นำหน้า Attribite ต่อท้าย มันจะรู้โดยอัตโนมัติ)
     * method จะตั้งเป็น camelCase
     */
    protected $appends = [
        'profile_image',
    ];


    /**
     * ซ่อน field ที่ไม่ต้องการให้แสดงออกไป
     */
    protected $hidden = [
        'password',
        'access_token',
    ];

    /**
     * convert field วันที่ให้อยู่ในรูปแบบที่เป็น instance ของ Carbon
     * Laravel จะใช้ package Carbon ในการจัดการวันที่
     */
    protected $dates = [
        'last_login_at',
        'created_at',
        'updated_at',
    ];

    /**
     * field เหล่านี้ควรจะโยน type ที่ถูกต้องกับใน table ของมัน
     */
    protected $casts = [
        'created_at' => 'datetime',
        'updated_at' => 'datetime',
    ];


    /**
     * กำหนดชื่อ table ที่มี relationship กับ table users
     */
    protected $with = [
        'profile',
    ];
}

```

