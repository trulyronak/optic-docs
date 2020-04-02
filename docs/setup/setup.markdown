---
layout: default
title: Starting your API with Optic
nav_order: 2
description: ""
has_children: true
permalink: /setup
---

# Starting your API with Optic

Time: 10 minutes
{: .fs-5 .fw-300 }

When you start your API with Optic, it is able to observe the HTTP traffic the API process handles. This real traffic becomes the data set Optic uses to document and test your API.

To get started, you just need to show Optic how to start your API.

#### Before:
```bash
$ <your-api-start-command>
```
#### With Optic's CLI (<span style="text-transform: lowercase">`api`</span>)
```bash
$ api start

> Starting your API with <your-api-start-command>
```

#### Optic CLI in 30 seconds
<div style="position: relative; padding-bottom: 62.5%; height: 0;"><iframe src="https://www.loom.com/embed/b1a1857fa29b4a75935db2ab8d2357dc" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"></iframe></div>

---

## Installing the Optic CLI

First you need to install Optic's CLI. You can download it with Yarn or NPM:

```bash
yarn global add @useoptic/cli
```

```bash
npm install @useoptic/cli -g
```

If you have trouble getting Optic installed, please [open an issue on GitHub](https://github.com/opticdev/optic/issues/new)

## Setting up Optic
Now that you have downloaded the CLI, choose one of the guides below to learn how to setup Optic for your stack:
