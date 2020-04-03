---
layout: default
title: Python
nav_order: 1
description: ""
parent: "Starting your API with Optic"
permalink: /setup/python
---

# Python

How to add Optic to a Python API
{: .fs-5 .fw-300 }

{% include_relative shared.markdown %}

---

### Flask <span class="label label-green">Supported</span> <span class="label label-yellow">Requires Code Change</span>
All Flask APIs contain a call to `app.run(...)`. Just update this line to pass in Optic's environment variable first:


#### Before
```python
app.run(port=5000)
```

#### After
```python
app.run(port=os.environ['OPTIC_API_PORT'] if 'OPTIC_API_PORT' in os.environ else 5000)
```

**Note**: If you are using [`flask run`](https://flask.palletsprojects.com/en/1.1.x/cli/), simply adjust flask run to pass in the port
#### Before
```bash
flask run
```

#### After
```bash
flask run --port=$OPTIC_API_PORT
```

Now when Optic runs your start command, your API will start on the port Optic assigns it.

### Django <span class="label label-green">Supported</span> <span class="label label-yellow">Requires Code Change</span>
Django runs by its `manage.py` file. To allow for optic, simply adjust it to use the Optic API Port

#### Before
```python
... # other code
def main():
    os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'mysite.settings')
    try:
        from django.core.management import execute_from_command_line
... # other code
```

#### After
```python
... # other code
def main():
    os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'mysite.settings')
    try:
        from django.core.management import execute_from_command_line
        # Add Optic CLI as a port option
        from django.core.management.commands.runserver import Command as runserver
        runserver.default_port = os.environ['OPTIC_API_PORT'] if 'OPTIC_API_PORT' in os.environ else 8080
... # other code
```

Now when Optic runs your start command, your API will start on the port Optic assigns it.

---

{% include_relative shared-check.markdown %}