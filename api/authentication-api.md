---
description: >-
  เป็น package ที่ช่วยในการทำ authentication ด้วย Oauth 2.0 ทำตาม document
  ได้เลย
---

# ทำ Authentication สำหรับ API

## Laravel Passport

{% embed url="https://laravel.com/docs/7.x/passport\#installation" %}

หลังจากติดตั้งเรียบร้อยแล้วควรเรียกใช้ Method `Passport::routes` ภายใน `boot` Method ของไฟล์ AuthServiceProvider

Method นี้จะ register route ที่จำเป็นต้องใช้ token ทั้งหมด



