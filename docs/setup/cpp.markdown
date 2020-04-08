---
layout: default
title: C++
nav_order: 1
description: ""
parent: "Starting your API with Optic"
permalink: /setup/cpp
---

# C++

How to add Optic to a C++ API
{: .fs-5 .fw-300 }

{% include_relative shared.markdown %}

---

### Pistache.io <span class="label label-green">Supported</span><span class="label label-yellow">Requires Code Change</span>

Simply modify your `Http::Endpoint` address to check for Optic's environment variable first!

#### Before
```cpp
int main() {
    Pistache::Address addr(Pistache::Ipv4::any(), Pistache::Port(8000));
    auto opts = Pistache::Http::Endpoint::options()
        .threads(1);

    Http::Endpoint server(addr);
    server.init(opts);
    server.setHandler(Http::make_handler<HelloHandler>());
    server.serve();
}
```

#### After
```cpp
#include <stdlib.h>
#include <string>
...

int main() {
    int port = 8000;
    if (getenv("OPTIC_API_PORT")) {
            std::string s = getenv ("OPTIC_API_PORT");
            port = std::stoi(s);
    }
    Pistache::Address addr(Pistache::Ipv4::any(), Pistache::Port(port));
    auto opts = Pistache::Http::Endpoint::options()
        .threads(1);

    Http::Endpoint server(addr);
    server.init(opts);
    server.setHandler(Http::make_handler<HelloHandler>());
    server.serve();
}
```

Now when Optic runs your start command, your API will start on the port Optic assigns it.


---

{% include_relative shared-check.markdown %}
