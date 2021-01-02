# สร้าง model user role permission

ลบ app\User.php

```text
mkdir app\Models\Auth\User
mkdir app\Models\Auth\Role
mkdir app\Models\Auth\Permission
```

model User

app\Models\Auth\User\User.php

```text
namespace App\Models\Auth\User;

use App\Traits\Hashable;
use Illuminate\Auth\Authenticatable;
use Illuminate\Contracts\Auth\Access\Authorizable as AuthorizableContract;
use Illuminate\Contracts\Auth\Authenticatable as AuthenticatableContract;
use Illuminate\Database\Eloquent\Model;
use Illuminate\Database\Eloquent\SoftDeletes;
use Illuminate\Database\Query\Builder;
use Laravel\Lumen\Auth\Authorizable;
use Laravel\Passport\HasApiTokens;
use Spatie\Permission\Traits\HasRoles;

class User extends Model implements AuthenticatableContract, AuthorizableContract
{
    use Authenticatable;
    use Authorizable;
    use HasApiTokens;
    use HasRoles;
    use SoftDeletes;
    use Hashable;

    const PERMISSIONS = [
        'create' => 'user create',
        'read' => 'user read',
        'reads' => 'user reads',
        'update' => 'user update',
        'delete' => 'user delete',
        'restore' => 'user restore',
    ];

    protected $fillable = [
        'email',
        'username',
        'password'
    ];

    protected $hidden = [
        'password',
    ];
}
```

model Role

app\Models\Auth\Role\Role.php

```text
namespace App\Models\Auth\Role;

use App\Traits\Hashable;
use Illuminate\Database\Eloquent\Builder;

class Role extends \Spatie\Permission\Models\Role
{
    use Hashable;

    const PERMISSIONS = [
        'create' => 'role create',
        'read' => 'role read',
        'reads' => 'role reads',
        'update' => 'role update',
        'delete' => 'role delete',
    ];
}
```

model Permission

app\Models\Auth\Role\Permission.php

```text
namespace App\Models\Auth\Permission;

use App\Traits\Hashable;
use Illuminate\Database\Eloquent\Builder;

class Permission extends \Spatie\Permission\Models\Permission
{
    use Hashable;

    const PERMISSIONS = [
        'read' => 'permission read',
        'reads' => 'permission reads',
    ];
}
```

config\permission.php

```text
'permission' => App\Models\Auth\Permission\Permission::class,

'role' => App\Models\Auth\Role\Role::class,
```





