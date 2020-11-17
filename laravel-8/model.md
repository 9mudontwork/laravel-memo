# ตัวอย่าง Model

```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class User extends Model
{
    use HasFactory;

    protected $table = 'users';

    const CREATED_AT = 'created_at';
    const UPDATED_AT = 'updated_at';

    /**
     * field ที่เปิดใช้งาน
     */
    protected $fillable = ['name'];


    /**
     * ซ่อน field ที่ไม่ต้องการให้แสดงออกไป
     */
    protected $hidden = [
        'password',
        'remember_token',
    ];



    /**
     * convert field วันที่ให้อยู่ในรูปแบบที่เป็น instance ของ Carbon
     * Laravel จะใช้ package Carbon ในการจัดการวันที่
     */
    protected $dates = [
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
}

```

