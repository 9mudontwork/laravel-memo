# Attacth Sync

{% embed url="https://stackoverflow.com/questions/23968415/laravel-eloquent-attach-vs-sync" %}

```php
/**
 * relation แบบ many to many
 * ตาราง users relation กับ ตาราง roles
 * เก็บ id ไว้ที่ตาราง user_role
 * field foreign key ของตาราง user คือ user_id
 * field foreign key ของตาราง role คือ role_id
 */
public function roles()
{
    return $this->belongsToMany(Role::class, 'user_role', 'user_id', 'role_id');
}
```

