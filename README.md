Note: this is a forked repo from [langma's radiator
view](https://github.com/langma/radiator-view) to support the v3 of the travis
api.

# Simple build status and alarm radiator view

Many continuous integration services lack a nice and simple radiator view / dashboard. This project displays all your projects and selected branches with a beautiful build status based coloring.

Production (or any other) environment monitoring is another good practice. Radiate your alarms as well as builds!

Supported CI backends are [CircleCI](https://circleci.com/), [Travis CI](https://travis-ci.org/), [Jenkins](https://jenkins.io), [Drone](https://drone.io).

For alarm monitoring, [AWS CloudWatch Alarms](https://aws.amazon.com) is supported.

_Pull requests are welcome._

![Circle CI Radiator view](/readme_radiator.png?raw=true 'Circle CI Radiator view')

## Hosted version

https://sampsakuronen.github.io/circleci-radiator-view/

This page will always reflect the newest content of this repository. For security reasons you may decide to fork this repository and have your own version running.

## Setup

|                | Credentials needed                                                                                                                        | Radiator URL                                                                                                    |
| -------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| CicleCI        | API token from [your CircleCI account settings](https://circleci.com/account/api)                                                         | [index.html](https://sampsakuronen.github.io/circleci-radiator-view/index.html)                                 |
| Travis CI      | API token from https://travis-ci.org/profile/<your_profile>                                                                               | [index.html?mode=travis](https://sampsakuronen.github.io/circleci-radiator-view/index.html?mode=travis)         |
| Jenkins        | Create a user and a token for the user in your job settings. Take note of your job endpoint URL (eg. `http://host/jenkins/job/My%20Job`). | [index.html?mode=jenkins](https://sampsakuronen.github.io/circleci-radiator-view/index.html?mode=jenkins)       |
| AWS CloudWatch | Create a monitor user with read-only access in IAM, token is _ACCESSKEY:longsecretkey_                                                    | [index.html?mode=cloudwatch](https://sampsakuronen.github.io/circleci-radiator-view/index.html?mode=cloudwatch) |
| Drone CI       | Create a user and token in admin UI. Use token with optional namespaces: `[ns,ns2:]thetoken`                                              | [index.html?mode=drone](https://sampsakuronen.github.io/circleci-radiator-view/index.html?mode=drone)           |

### Query parameters

All options can be set either with a query parameter or from the setup form. The setup form is shown if any required parameters are missing.

| Parameter      | Description                                                                                                                                                                                   |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `mode`         | The backend system to be used: `circle` (default), `travis` or `jenkins`                                                                                                                      |
| `token`        | The auth token token to be used. **Note:** CircleCI API tokens have read and write access. When you use the query parameter approach the token will be visible in your browser history.       |
| `repositories` | Declare the wanted repositories in a comma-separated format eg. `my-cool-project,helloWorldProject`. By default all repositories will be shown.                                               |
| `branch`       | Select the `branch` to show (from all repos found in the API end point). Useful if your repos contain only a single branch (master, release etc) that should be visible in the radiator view. |
| `url`          | Optional: the Jenkins job URL.                                                                                                                                                                |

#### Examples

| Case                                          | URL                                                                                |
| --------------------------------------------- | ---------------------------------------------------------------------------------- |
| Token is entered separately in the setup form | /?mode=travis&branch=master                                                        |
| Jenkins                                       | /?mode=jenkins&token=REDACTED_TOKEN&url=http://localhost:8080/jenkins/job/My%20Job |
