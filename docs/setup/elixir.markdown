---
layout: default
title: Elixir
nav_order: 1
description: ""
parent: "Starting your API with Optic"
permalink: /setup/elixir
---

# Node

How to add Optic to a Elixir API
{: .fs-5 .fw-300 }

{% include_relative shared.markdown %}

---

### Phoenix <span class="label label-green">Supported</span> <span class="label label-yellow">Requires Code Change</span>
In your `./config/dev.exs` file, you need to modify your web endpoint configuration. Whether you are testing with http or https, simply modify the line that specifies the port to check for the `OPTIC_API_PORT` first.

#### Before
```elixir
config :hello, HelloWeb.Endpoint,
http: [port: 4000],
debug_errors: true,
code_reloader: true,
check_origin: false,
watchers: [
  node: [
    "node_modules/webpack/bin/webpack.js",
    "--mode",
    "development",
    "--watch-stdin",
    cd: Path.expand("../assets", __DIR__)
  ]
]
```

#### After
```elixir
config :hello, HelloWeb.Endpoint,
http: [port: System.get_env("OPTIC_API_PORT") || 4000],
debug_errors: true,
code_reloader: true,
check_origin: false,
watchers: [
  node: [
    "node_modules/webpack/bin/webpack.js",
    "--mode",
    "development",
    "--watch-stdin",
    cd: Path.expand("../assets", __DIR__)
  ]
]
```

Now when Optic runs your start command, your API will start on the port Optic assigns it.

### Sails.js <span class="label label-green">Supported</span> <span class="label label-green">No Code Changes</span>
If you use the `sails lift` command to start your Sails app, you just have to update your start command in your `optic.yml` file:

#### Before
```yaml
start:
  command: sails lift
```

#### After
```yaml
start:
  command: sails lift --port $OPTIC_API_PORT
```

Now when Optic runs your start command, your API will start on the port Optic assigns it.

---

{% include_relative shared-check.markdown %}
