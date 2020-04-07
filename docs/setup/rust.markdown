---
layout: default
title: Rust
nav_order: 1
description: ""
parent: "Starting your API with Rust"
permalink: /setup/rust
---

# Rust

How to add Optic to a Rust API
{: .fs-5 .fw-300 }

{% include_relative shared.markdown %}

---

### Rocket <span class="label label-green">Supported</span> <span class="label label-green">No Code Changes Option</span> <span class="label label-yellow">Requires Code Change Option</span>

If you use `Config::build()`, you can simply modify it to check for Optic's environment variable.

#### Before
```rust
use rocket::config::{Config, Environment};
use std::env;

let config = Config::build(Environment::Staging)
    .port(8000)
    .unwrap();

rocket::custom(config)
    .mount("/", routes![hello])
    .launch();
```

#### After
```rust
use rocket::config::{Config, Environment};
use std::env;

let mut port = 8000;
match env::var("OPTIC_API_PORT") {
    Ok(val) => port = val.parse::<u16>().unwrap(),
    Err(e) => {}
}

let config = Config::build(Environment::Staging)
    .port(port)
    .unwrap();

rocket::custom(config)
    .mount("/", routes![hello])
    .launch();
```

**Note**: If you use `rocket::ignite()`, you can instead modify the start command to set `ROCKET_PORT` to be Optic's environment variable.

#### Alternative Approach

#### Before
```yaml
start:
  command: cargo run
```

#### After
```yaml
start:
  command: export ROCKET_PORT=$OPTIC_API_PORT ; cargo run
```

Now when Optic runs your start command, your API will start on the port Optic assigns it.

### Actix <span class="label label-green">Supported</span> <span class="label label-yellow">Requires Code Change Option</span>

Simply modify your `HttpServer.bind()` call to check for Optic's environment variable.

#### Before
```rust
HttpServer::new(...)
    .bind("127.0.0.1:8000")?
    .run()
    .await
```

#### After
```rust

let port = env::var("OPTIC_API_PORT").unwrap_or_else(|e| {
    return "8000".to_string()
});

HttpServer::new(...)
    .bind(format!("127.0.0.1:{}" , port))?
    .run()
    .await
```

Now when Optic runs your start command, your API will start on the port Optic assigns it.


---

{% include_relative shared-check.markdown %}
