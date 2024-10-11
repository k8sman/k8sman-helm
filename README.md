# k8sman Helm Chart Documentation

## Overview
`k8sman` is a management platform for Kubernetes clusters, designed to facilitate the execution of administrative commands and orchestrate interactions within the cluster. The `k8sman-helm` deploys the `k8sman-agent` into Kubernetes clusters, enabling seamless management of cluster resources.

## Prerequisites
- A Kubernetes cluster with internet access.
- Helm 3 installed on your local environment.

## Adding the Helm Repository
To use the `k8sman-helm`, first add the repository to Helm and update the list of available charts:

```shell
helm repo add k8sman https://k8sman.github.io/k8sman-helm
helm repo update
```

## Installing the Chart
To install the `k8sman-agent` chart in your Kubernetes cluster, run the following command, replacing `YOUR_AGENT_KEY` with the authentication key provided by the k8sman platform:

```shell
helm install k8sman-agent k8sman/k8sman-helm \
  --set agent.key=YOUR_AGENT_KEY
```

To find the latest version of the chart available for installation, use the command:

```shell
helm search repo k8sman
```

## Uninstalling the Chart
To uninstall the `k8sman-agent` chart from your Kubernetes cluster, use the command:

```shell
helm delete k8sman-agent
```

This will remove all resources associated with the `k8sman-agent` release.

## Configuration
The chart can be customized using various parameters defined in the `values.yaml` file. You can also override these parameters via the command line when installing or upgrading the chart.

Below are some of the commonly used parameters:

| Parameter            | Description                                    | Default Value  |
|----------------------|------------------------------------------------|----------------|
| `agent.key`          | Authentication key for the agent              | None (must be set) |

For a complete list of configurable parameters, refer to the `values.yaml` file.

### RBAC Configuration
The `k8sman-agent` requires extensive permissions to manage the Kubernetes cluster effectively. Modify the RBAC settings in the `rbac.yaml` file according to your security policies and needs to ensure a secure deployment.

## Security Considerations
- Ensure that the `k8sman-agent` is running with the necessary but minimal set of permissions to perform its tasks.
- Securely manage access credentials to prevent unauthorized access.


For more information, visit the [k8sman platform](https://k8sman.io).