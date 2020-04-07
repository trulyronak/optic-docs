---
layout: default
title: Java
nav_order: 1
description: ""
parent: "Starting your API with Optic"
permalink: /setup/java
---

# CPP

How to add Optic to a Java API
{: .fs-5 .fw-300 }

{% include_relative shared.markdown %}

---

### Spring <span class="label label-green">Supported</span> <span class="label label-green">No Code Changes</span> 

If you use `./gradlew bootRun` to run your spring app, you just have to update your start command in your `optic.yml` file:

#### Before
```yaml
start:
  command: ./gradlew bootRun
```

#### After
```yaml
start:
  command:  export SERVER_PORT=$OPTIC_API_PORT ; ./gradlew bootRun
```

**Note**: If you use maven to run your app, the same approach will work. Just make sure your optic.yml includes `export SERVER_PORT=$OPTIC_API_PORT ;` so that the port that maven uses is the `OPTIC_API_PORT`.


Now when Optic runs your start command, your API will start on the port Optic assigns it.


---

{% include_relative shared-check.markdown %}
