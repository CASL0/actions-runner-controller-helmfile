[![Lint](https://github.com/CASL0/actions-runner-controller-helmfile/actions/workflows/lint.yaml/badge.svg)](https://github.com/CASL0/actions-runner-controller-helmfile/actions/workflows/lint.yaml)
[![pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit&logoColor=white)](https://github.com/pre-commit/pre-commit)
[![License](https://img.shields.io/badge/license-MIT-blue)](https://opensource.org/license/mit)

# Deploy ondemand GitHub Actions auto-scaling runners with actions-runner-controller

[Actions-runner-controller](https://github.com/actions/actions-runner-controller) can controll GitHub Actions auto-scaling runners.

This helmfile provides quick instructions on Kubernetes environments.

## Prerequisites

- Install [helmfile](https://github.com/helmfile/helmfile).
- Create a pre-define Kubernetes secret `arc-runners-secret` in the namespace `arc-runners` the gha-runner-scale-set is going to deploy to authenticate Actions Runner Controller (ARC) to the GitHub API by using a GitHub App or by using a personal access token (classic). For more information, see [Authenticating to the GitHub API](https://docs.github.com/en/actions/hosting-your-own-runners/managing-self-hosted-runners-with-actions-runner-controller/authenticating-to-the-github-api).

## Getting started

1. Set the `githubConfigUrl` value in the file [default.values.yaml](./releases/gha-runner-scale-set/config/default.values.yaml) to the GitHub url for where you want to configure runners.

   ```yaml
   githubConfigUrl: https://github.com/CASL0/actions-runner-controller-helmfile
   ```

1. Use the following commands to deploy self-hosted runners.

   ```sh
   helmfile apply
   ```

1. Set the `runs-on` value to `my-arc-runners` in your workflows similar to the following.

   ```yaml
   jobs:
     build:
       runs-on: my-arc-runners
       steps:
         - run: echo "Hello world!"
   ```

## Advanced Configuration

See [advanced.md](docs/advanced.md).

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## Refs

- <https://helmfile.readthedocs.io/en/latest/>
