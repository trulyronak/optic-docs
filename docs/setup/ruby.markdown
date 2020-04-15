---
layout: default
title: Ruby
nav_order: 1
description: ""
parent: "Starting your API with Optic"
permalink: /setup/ruby
---

# Ruby

How to add Optic to a Ruby API
{: .fs-5 .fw-300 }

{% include_relative shared.markdown %}

---

### Rails <span class="label label-green">Supported</span> <span class="label label-green">No Code Changes</span>
If you use the `rails server` command to start your app, you just have to update your start command in your `optic.yml` file:

#### Before
```yaml
start:
  command: rails server # assuming your app is called main.py
```

#### After
```yaml
start:
  command: rails server -p $OPTIC_API_PORT # assuming your app is called main.py
```

Alternatively, if you use `puma` to start your app, you will follow a similar process in modifying your `optic.yml` file

#### Before
```yaml
start:
  command: puma # or, if you use bundler (bundle exec puma)
```

#### After
```yaml
start:
  command: puma -p $OPTIC_API_PORT # or, if you use bundler (bundle exec puma -p $OPTIC_API_PORT)
```


Now when Optic runs your start command, your API will start on the port Optic assigns it.


---

{% include_relative shared-check.markdown %}