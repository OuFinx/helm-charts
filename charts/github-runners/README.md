# Description

This helm chart allows to create `RunnerDeployment` and `HorizontalRunnerAutoscaler` resources for [actions-runner-controller](https://github.com/actions-runner-controller/actions-runner-controller).

This is useful if you want to install these resources via [helm_release](https://registry.terraform.io/providers/hashicorp/helm/latest/docs/resources/release) in the Terraform.

## What need to change

1. You can set both the list of repositories and organization name

```
repositories: ["oufinx/repo1", "oufinx/repo2"]
organization: "oufinx"
```

2. Set label that will be added for runner

```
labels: ["abc-production"]
```

By default it has the next `metrics`

```
metrics:
- type: PercentageRunnersBusy
  scaleUpThreshold: '0.75'    # The percentage of busy runners at which the number of desired runners are re-evaluated to scale up
  scaleDownThreshold: '0.3'   # The percentage of busy runners at which the number of desired runners are re-evaluated to scale down
  scaleUpFactor: '1.4'        # The scale up multiplierез factor applied to desired count
  scaleDownFactor: '0.7'      # The scale down multiplier factor applied to desired count
```

## How to install

1. Add repo

```
helm repo add oufinx https://oufinx.github.io/helm-charts/ 
```

2. Make repo updates

```
helm repo update
```

3. Create `my_values.yaml` and set your changes


4. Install  chart

```
helm install runners oufinx/github-runners -f my_values.yaml
```
