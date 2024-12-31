[![Lint](https://github.com/CASL0/actions-runner-controller-helmfile/actions/workflows/lint.yaml/badge.svg)](https://github.com/CASL0/actions-runner-controller-helmfile/actions/workflows/lint.yaml)
[![pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit&logoColor=white)](https://github.com/pre-commit/pre-commit)
[![License](https://img.shields.io/badge/license-MIT-blue)](https://opensource.org/license/mit)

# actions-runner-controller-helmfile

Deploy ondemand GitHub Actions self-hosted runners using [actions-runner-controller](https://github.com/actions/actions-runner-controller).

## Prerequisites

- Install [helmfile](https://github.com/helmfile/helmfile)
- Create a pre-define Kubernetes secret `arc-runners-secret` in the namespace `arc-runners` the gha-runner-scale-set is going to deploy with the command below

  ```sh
  kubectl create secret generic arc-runners-secret --namespace=arc-runners --from-literal=github_token='ghp_your_pat'
  ```

## Getting started

```sh
helmfile apply
```

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## Refs

- <https://helmfile.readthedocs.io/en/latest/>
