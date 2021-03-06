---
layout: default
title: Node
nav_order: 1
description: ""
parent: "Starting your API with Optic"
permalink: /setup/node
---

# Node

How to add Optic to a Node JS API
{: .fs-5 .fw-300 }

{% include_relative shared.markdown %}

---

### Express <span class="label label-green">Supported</span> <span class="label label-yellow">Requires Code Change</span>
All Express APIs contain a call to `app.listen(...)`. Just update this line to look for Optic's environment variable first:

**Note**: If you are using [`express-generator`](https://expressjs.com/en/starter/generator.html), the `app.listen` call is located in `./bin/www`

#### Before
```javascript
app.listen(port || 3000)
```

#### After
```javascript
app.listen(process.env.OPTIC_API_PORT || port || 3000)
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


### Hapi <span class="label label-green">Supported</span> <span class="label label-yellow">Requires Code Change</span>
If you use `Hapi.server()` to start your server, simply configure it to check for Optic's environment variable first.

#### Before
```javascript
const server = Hapi.server({
    port: 3000,
    host: 'localhost'
});
```

#### After
```javascript
const server = Hapi.server({
    port: process.env.OPTIC_API_PORT || 3000,
    host: 'localhost'
});
```

Now when Optic runs your start command, your API will start on the port Optic assigns it.



---

{% include_relative shared-check.markdown %}
