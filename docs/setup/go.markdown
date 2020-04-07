---
layout: default
title: Go
nav_order: 1
description: ""
parent: "Starting your API with Go"
permalink: /setup/golang
---

# Node

How to add Optic to a Golang API
{: .fs-5 .fw-300 }

{% include_relative shared.markdown %}

---

### Mux <span class="label label-green">Supported</span> <span class="label label-yellow">Requires Code Change</span>
Before your `http` call to `ListenAndServe`, check for the `OPTIC_API_PORT` first.

#### Before
```golang
http.ListenAndServe(":8000", r)
```

#### After
```golang
port := ":8000"

if os.Getenv("OPTIC_API_PORT") != "" {
    port = fmt.Sprintf(":%s", os.Getenv("OPTIC_API_PORT"))
}

http.ListenAndServe(port, r)
```

Now when Optic runs your start command, your API will start on the port Optic assigns it.


---

{% include_relative shared-check.markdown %}
