---
description: >-
  Controller จัดการข้อมูล และติดต่อกับ Model จากนั้นส่งให้ Transformer
  จัดการข้อมูลที่จะ response
---

# controller และ transformer

### Controller หลัก

app\Http\Controllers\Controller.php

```text
namespace App\Http\Controllers;

use App\Traits\Hashable;

use Dingo\Api\Http\Response;
use Dingo\Api\Routing\Helpers;

use Laravel\Lumen\Routing\Controller as BaseController;

class Controller extends BaseController
{
    use Hashable;
    use Helpers;
}
```

### Transformer หลัก

```text
mkdir app\Transformers

type nul > app\Transformers\BaseTransformer.php
```

app\Transformers\BaseTransformer.php

```text
namespace App\Transformers;

use League\Fractal\TransformerAbstract;

abstract class BaseTransformer extends TransformerAbstract
{ }
```





