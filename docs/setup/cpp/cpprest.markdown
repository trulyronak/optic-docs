---
layout: default
title: C++ Rest SDK
nav_order: 1
description: ""
parent: "CPP"
grand_parent: "Starting your API with Optic"
permalink: /setup/cpp/restsdk
---

### CppRestSDK <span class="label label-green">Supported</span><span class="label label-yellow">Requires Code Change</span>

Simply modify your `Http::Endpoint` address to check for Optic's environment variable first!

#### Before
```cpp

utility::string_t port = U("5000");

utility::string_t address = U("http://127.0.0.1:");
address.append(port);
on_initialize(address);

```

#### After
```cpp
std::string portStr = "5000";
if (getenv("OPTIC_API_PORT")) {
    portStr =  getenv ("OPTIC_API_PORT");
}
utility::string_t port = U(portStr);

utility::string_t address = U("http://127.0.0.1:");
address.append(port);
```

**Note**: If you've already configured your `cpprestsdk` server to look for an enviornment variable, you can also update your start command in `optic.yml` to use the environment variable `$OPTIC_API_PORT`