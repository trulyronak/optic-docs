---
layout: default
title: PHP
nav_order: 1
description: ""
parent: "Starting your API with Optic"
permalink: /setup/php
---

# CPP

How to add Optic to a PHP API
{: .fs-5 .fw-300 }

{% include_relative shared.markdown %}

---

### Laravel <span class="label label-green">Supported</span> <span class="label label-green">No Code Changes</span> 

If you use `artisan serve` to run your laravel app, you just have to update your start command in your `optic.yml` file:

#### Before
```yaml
start:
  command: php artisan serve
```

#### After
```yaml
start:
  command:  php artisan serve --port=$OPTIC_API_PORT
```

Now when Optic runs your start command, your API will start on the port Optic assigns it.


---

{% include_relative shared-check.markdown %}
