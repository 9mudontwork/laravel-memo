# จำเป็นสำหรับการ Dev เพื่อให้เป็นมาตรฐานเดียวกัน

## ติดตั้ง Extension ของ vs code

### ตัวช่วย format code + ทำให้ vscode ฉลาดขึ้น

{% embed url="https://marketplace.visualstudio.com/items?itemName=bmewburn.vscode-intelephense-client" %}

### ตัวช่วย import class มันจะเพิ่ม namespace ให้อัตโนมัติ

{% embed url="https://marketplace.visualstudio.com/items?itemName=MehediDracula.php-namespace-resolver" %}

### ตัวช่วย format code กับ blade.php

{% embed url="https://marketplace.visualstudio.com/items?itemName=apility.beautify-blade" %}

สร้างไฟล์ .jsbeautifyrc ไว้ที่ root project

```text
{
    "beautify.config": "string|Object.<string,string|number|boolean>",
    "indent_size": 4,
    "indent_char": " ",
    "css": {
        "indent_size": 2
    },
    "beautify.language": {
        "html": ["blade"]
      }

}
```

### ตัวช่วยทำให้ blade.php แยกสี อ่านง่าย

{% embed url="https://marketplace.visualstudio.com/items?itemName=onecentlin.laravel-blade" %}



## ติดตั้ง laravel-ide-helper \(ตัวช่วยทำให้ vscode รู้จัก class ของ laravel\)

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

