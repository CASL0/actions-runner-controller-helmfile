# actions-runner-controller-helmfile

Deploy ondemand GitHub Actions self-hosted runners

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
