# migrate และ seed

doc  
[Database: Migrations](https://laravel.com/docs/master/migrations)  
[Database: Seeding](https://laravel.com/docs/master/seeding)

migrate users

```text
php artisan make:migration create_users_table
```

database\migrations\2019\_11\_09\_224602\_create\_users\_table.php

```text
Schema::create('users', function (Blueprint $table) {

    $table->increments('id');
    $table->string('username')->unique();
    $table->string('email')->unique();
    $table->string('password');
    
    $table->timestamps();
    $table->softDeletes();
});
```

```text
mkdir database\seeds\auth
mkdir database\seeds\traits

สร้างไฟล์ windows

type nul > database\seeds\auth\AuthSeeder.php
type nul > database\seeds\auth\RolesSeeder.php
type nul > database\seeds\auth\UsersTableSeeder.php
type nul > database\seeds\traits\SeederHelper.php
```

database\seeds\auth\AuthSeeder.php

```text
use Illuminate\Database\Seeder;

class AuthSeeder extends Seeder
{
    public function run()
    {
        $this->call('RolesSeeder');
        $this->call('UsersTableSeeder');
    }
}
```

database\seeds\auth\RolesSeeder.php

```text
use Illuminate\Database\Seeder;

class RolesSeeder extends Seeder
{
    use SeederHelper;

    public function run()
    {
        $roleModel = app(config('permission.models.role'));
        $permissionModel = app(config('permission.models.permission'));

        $viewBackend = $permissionModel::create([
            'name' => config('setting.permission.permission_names.view_backend'),
        ]);

        $manageAuthorization = $permissionModel::create([
            'name' => config('setting.permission.permission_names.manage_authorization'),
        ]);

        foreach (config('setting.permission.role_names') as $roleName) {
            $roleModel::create([
                'name' => $roleName,
            ])->givePermissionTo([
                $viewBackend,
                $manageAuthorization,
            ]);
        }

        $this->seederPermission($roleModel::PERMISSIONS);
        $this->seederPermission($permissionModel::PERMISSIONS);
    }
}
```

database\seeds\auth\UsersTableSeeder.php

```text
use App\Models\Auth\User\User;
use Illuminate\Database\Seeder;

class UsersTableSeeder extends Seeder
{
    use SeederHelper;

    public function run()
    {
        $system = factory(User::class)->create([
            'email' => 'system@system.com',
            'username' => 'system',
            'password' => app('hash')->make('system'),
        ]);

        $admin = factory(User::class)->create([
            'email' => 'admin@admin.com',
            'username' => 'admin',
            'password' => app('hash')->make('admin'),
        ]);

        $user = factory(User::class)->create([
            'email' => 'user@user.com',
            'username' => 'user',
            'password' => app('hash')->make('user'),
        ]);

        $system->assignRole(config('setting.permission.role_names.system'));
        $admin->assignRole(config('setting.permission.role_names.admin'));

        $this->seederPermission(User::PERMISSIONS);
    }
}
```

database\factories\UserFactory.php

```text
use App\Models\Auth\User\User;

$factory->define(User::class, function (Faker\Generator $faker) {
    return [
        'email' => $faker->unique()->email,
        'username' => $faker->unique()->username,
        'password' => app('hash')->make($faker->password),
    ];
});
```

database\seeds\traits\SeederHelper.php

```text
trait SeederHelper
{
    public function seederPermission(array $permissionNames, bool $isAddToAdminRole = true, array $except = [])
    {
        $roleModel = app(config('permission.models.role'));
        $permissionModel = app(config('permission.models.permission'));

        foreach ($permissionNames as $permissionName) {
            $permission = $permissionModel::create([
                'name' => $permissionName,
            ]);
            $roleModel::findByName(config('setting.permission.role_names.system'))->givePermissionTo($permission);
            if ($isAddToAdminRole) {
                if (!in_array($permissionName, $except)) {
                    $roleModel::findByName(config('setting.permission.role_names.admin'))->givePermissionTo($permission);
                }
            }
        }
    }
}
```

database\seeds\DatabaseSeeder.php

```text
use Illuminate\Database\Seeder;

class DatabaseSeeder extends Seeder
{
    /**
     * Run the database seeds.
     *
     * @return void
     */
    public function run()
    {
        $this->call('AuthSeeder');

        app('cache')->flush();
    }
}
```

```text
php artisan migrate

composer dumpautoload

php artisan db:seed
```

