# จำเป็นสำหรับการ Dev เพื่อให้เป็นมาตรฐานเดียวกัน

## ติดตั้ง Extension ของ vs code

ตัวช่วย format code + ทำให้ vscode ฉลาดขึ้น

{% embed url="https://marketplace.visualstudio.com/items?itemName=bmewburn.vscode-intelephense-client" %}

ตัวช่วย import class มันจะเพิ่ม namespace ให้อัตโนมัติ

{% embed url="https://marketplace.visualstudio.com/items?itemName=MehediDracula.php-namespace-resolver" %}



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

