---
layout: default
title: Pistache
nav_order: 1
description: ""
parent: "CPP"
grand_parent: "Starting your API with Optic"
permalink: /setup/cpp/pistache
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