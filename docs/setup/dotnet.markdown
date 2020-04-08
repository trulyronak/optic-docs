---
layout: default
title: .NET
nav_order: 1
description: ""
parent: "Starting your API with Optic"
permalink: /setup/dotnet
---

# .NET

How to add Optic to a .NET API
{: .fs-5 .fw-300 }

{% include_relative shared.markdown %}

---

### .NET <span class="label label-yellow">Finicky</span><span class="label label-yellow">Requires Code Change</span>

Simply modify your `WebBuilder` call to check for Optic's environment variable first!

#### Before
```c#
public static IHostBuilder CreateHostBuilder(string[] args) {
    return Host.CreateDefaultBuilder(args).ConfigureWebHostDefaults(webBuilder =>
    {
        webBuilder.UseStartup<Startup>();
        webBuilder.UseUrls("http://localhost:80/");
    });
}
```

#### After
```c#
public static IHostBuilder CreateHostBuilder(string[] args) {
    var portString = (System.Environment.GetEnvironmentVariable("OPTIC_API_PORT"));
    if (String.IsNullOrEmpty(portString)) {
        portString = "80";
    }

    return Host.CreateDefaultBuilder(args).ConfigureWebHostDefaults(webBuilder =>
    {
        webBuilder.UseStartup<Startup>();
        webBuilder.UseUrls("http://localhost:" + portString + "/");
    });
}
```

Now when Optic runs your start command, your API will start on the port Optic assigns it.


---

{% include_relative shared-check.markdown %}
