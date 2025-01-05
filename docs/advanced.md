# Advanced Configuration

## Configuring the Runner Scale Set Name

The `runs-on` value in your workflow file refers to the runner scale set name.

To configure the runner scale set name, set the `runnerScaleSetName` value in the file [default.values.yaml](../releases/gha-runner-scale-set/config/default.values.yaml) which defaults to `my-arc-runners`.

If you set the `runnerScaleSetName` value to `my-custom-value`, you can assign jobs to run on the deployed runners by using the following example.

```yaml
jobs:
  build:
    runs-on: my-custom-value
    steps:
      - run: echo "Hello world!"
```

## Configuring the Maximum and Minimum Number of Runners

To configure the maximum number of runners that can be scaled up and the minimum number of idle runners, you set the `maxRunners` value and the `minRunners` value in the file [default.values.yaml](../releases/gha-runner-scale-set/config/default.values.yaml).

In the following configuration, the runner scale set will scale up to a maximum of 20 runners and will scale down to 10 runners when the jobs are complete.

```yaml
maxRunners: 20
minRunners: 10
```
