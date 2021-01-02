# ติดตั้ง hashids

doc  
[https://github.com/vinkla/laravel-hashids](https://github.com/vinkla/laravel-hashids)

```text
mkdir app\Traits
```

สร้าง app\Traits\Hashable.php

```text
<?php

namespace App\Traits;

use Symfony\Component\HttpKernel\Exception\BadRequestHttpException;

trait Hashable
{
    public function decodeHash(string $hash)
    {
        $decoded = app('hashids')->decode($hash);

        if (empty($decoded)) {
            throw new BadRequestHttpException('Invalid hashed id.');
        }

        return $decoded[0];
    }

    public function getHashedId(string $key = 'id')
    {
        return app('hashids')->encode($this->{$key});
    }
}

```

service provider

bootstrap\app.php

```text
$app->register(Vinkla\Hashids\HashidsServiceProvider::class);
```

