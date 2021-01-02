# ติดตั้ง

create project

```text
composer create-project --prefer-dist laravel/lumen api
```

run server

```text
php -S localhost:8000 -t public
```

composer.json

```text
"php": "^7.2",
"dingo/api": "^2.4.0",
"dusterio/lumen-passport": "^0.2.15",
"laravel/lumen-framework": "^6.0",
"spatie/laravel-cors": "^1.6",
"spatie/laravel-permission": "^3.2",
"vinkla/hashids": "^7.0"
```

composer require

```text
composer require dingo/api

composer require dusterio/lumen-passport

composer require spatie/laravel-permission

composer require spatie/laravel-cors

composer require vinkla/hashids

หรือ

composer require dingo/api dusterio/lumen-passport spatie/laravel-permission spatie/laravel-cors vinkla/hashids
```

lumen 6  
[https://lumen.laravel.com/docs/6.x](https://lumen.laravel.com/docs/6.x)

dingo  
[https://github.com/dingo/api/wiki](https://github.com/dingo/api/wiki)

lumen passport  
[https://github.com/dusterio/lumen-passport](https://github.com/dusterio/lumen-passport)  
[https://laravel.com/docs/6.x/passport](https://laravel.com/docs/6.x/passport)

laravel permission  
[https://github.com/spatie/laravel-permission](https://github.com/spatie/laravel-permission)

laravel cors  
[https://github.com/spatie/laravel-cors](https://github.com/spatie/laravel-cors)

hashids  
[https://github.com/vinkla/laravel-hashids](https://github.com/vinkla/laravel-hashids)

