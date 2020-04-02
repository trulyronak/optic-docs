
### Prerequisites

- [Install the Optic CLI](/setup)
- An API project you can run locally
- 10 minutes to get things working

## Add Optic to your API Repo
Optic checks-in a configuration file and the API specification it maintains into your API repository.

1. Change your working directory to the API root
2. Run Optic's api init command
```bash
api init
```

<div style="position: relative; padding-bottom: 33.96739130434783%; height: 0;"><iframe src="https://www.loom.com/embed/8919d322329246d98c523b78906172ab" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"></iframe></div>


## Configure `api start` task

You'll need to provide Optic with the information it needs to start your API. Open the `optic.yml` file in your favorite text editor.

##### `optic.yml`
```yaml
name: Demo API
tasks:
  start:
    command: echo "Setup A Valid Command to Start your API!"
    baseUrl: http://localhost:4000
ignoreRequests:
- OPTIONS *
```

**command** - the command used to start your API server. ie `npm run start-server`
It should:
- Start a long-running process that stays running until exited
- Be runnable from the same directory as the `optic.yml` file w/o any special permissions

**baseUrl** - the URL where you want the API to be accessible locally ie `http://localhost:4000`
For local tasks, it should:
- (probably) be the same URL you use for local development today, that way consumers don't need to be updated.
- Be on a port/hostname that doesn't require special permissions to bind to

---

## Allow Optic to Choose which Port your API Starts on
Finally, Optic needs to be able to choose which port your API starts on. It does this by injecting an environment variable called `$OPTIC_API_PORT` before running your `command`.

This usually requires one of the following:
 - You to update a 1-3 lines of code in your project
 - A flag to be passed into your `command` that sets the port to `$OPTIC_API_PORT`
