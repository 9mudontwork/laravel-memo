# จำเป็นสำหรับการ Dev เพื่อให้เป็นมาตรฐานเดียวกัน

## ติดตั้ง Extension ของ vs code

{% embed url="https://marketplace.visualstudio.com/items?itemName=bmewburn.vscode-intelephense-client" %}

## ติดตั้ง laravel-ide-helper

{% embed url="https://github.com/barryvdh/laravel-ide-helper" %}

### generate doc

```text
php artisan ide-helper:generate
```

### ตั้งค่าในไฟล์ composer.json

```text
"scripts": {
    "post-update-cmd": [
        "Illuminate\\Foundation\\ComposerScripts::postUpdate",
        "@php artisan ide-helper:generate",
        "@php artisan ide-helper:meta"
    ]
},
```

