---
description: >-
  เป็น package ที่ช่วยในการทำ authentication แบบ Full Oauth 2.0 ทำตาม document
  ได้เลย
---

# ทำ Auth ด้วย Passport

## Laravel Passport

{% embed url="https://laravel.com/docs/7.x/passport\#installation" %}

หลังจากติดตั้งเรียบร้อยแล้วควรเรียกใช้ Method `Passport::routes` ภายใน `boot` Method ของไฟล์ AuthServiceProvider

Method นี้จะ register route ที่จำเป็นต้องใช้ token ทั้งหมด

## ลบ Passport ออกจาก Project

{% embed url="https://stackoverflow.com/questions/47567249/how-to-uninstall-laravel-passport" %}



