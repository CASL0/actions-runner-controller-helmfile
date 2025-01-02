[![Lint](https://github.com/CASL0/actions-runner-controller-helmfile/actions/workflows/lint.yaml/badge.svg)](https://github.com/CASL0/actions-runner-controller-helmfile/actions/workflows/lint.yaml)
[![pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit&logoColor=white)](https://github.com/pre-commit/pre-commit)
[![License](https://img.shields.io/badge/license-MIT-blue)](https://opensource.org/license/mit)

# actions-runner-controller-helmfile

Deploy ondemand GitHub Actions auto-scaling runners with [actions-runner-controller](https://github.com/actions/actions-runner-controller).

## Prerequisites

- Install [helmfile](https://github.com/helmfile/helmfile)
- Create a pre-define Kubernetes secret `arc-runners-secret` in the namespace `arc-runners` the gha-runner-scale-set is going to deploy with the command below

  ```sh
  kubectl create secret generic arc-runners-secret \
    --namespace=arc-runners \
    --from-literal=github_token='ghp_your_pat'
  ```

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

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## Refs

- <https://helmfile.readthedocs.io/en/latest/>
