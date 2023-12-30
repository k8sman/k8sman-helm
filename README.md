# k8sman-helm-chart

## Overview
The `k8sman-helm-chart` is a Helm chart for deploying the `k8sman-agent` in a Kubernetes cluster. The `k8sman-agent` is a crucial component of the Kubernetes management system, designed to execute administrative commands in the cluster and communicate with a RabbitMQ server for message passing.

## Prerequisites
- Kubernetes cluster with internet access
- Helm 3 installed
- Knowledge of your Kubernetes cluster's RBAC settings

## Installation

### 1. Add the Helm Repository
```shell
helm repo add k8sman <repository-url>
helm repo update
```

### 2. Install the Chart
```shell
helm install k8sman-agent k8sman/k8sman-helm-chart \
    --set rabbitmq.host: "xxxx" \
    --set rabbitmq.vhost: "xxxx" \
    --set rabbitmq.user: "xxxx" \
    --set rabbitmq.pass: "xxxx"
```

## Configuration

The following table lists the configurable parameters in `values.yaml` and their default values.

| Parameter            | Description                           | Default                        |
|----------------------|---------------------------------------|--------------------------------|
| `replicaCount`       | Number of `k8sman-agent` replicas     | `1`                            |
| `image.repository`   | `k8sman-agent` image repository       | `ovrdoz/k8sman-agent`          |
| `image.pullPolicy`   | Image pull policy                     | `Always`                       |
| `image.tag`          | `k8sman-agent` image tag              | `latest`                       |
| `rabbitmq.host`      | RabbitMQ server host                  | `host`     |
| `rabbitmq.vhost`     | RabbitMQ server virtual host          | `vhost`                     |
| `rabbitmq.user`      | RabbitMQ username                     | `username`                     |
| `rabbitmq.pass`      | RabbitMQ password                     | `<encoded-password>`           |

### RBAC Configuration
The `k8sman-agent` requires extensive permissions to execute administrative commands within the cluster. The provided `rbac.yaml` grants these permissions using a `ClusterRole` with `*` for resources and verbs. This setting can be tailored to specific needs by adjusting the `resources` and `verbs` in the RBAC configuration.

## Security Considerations
- Ensure that the `k8sman-agent` runs with the minimum necessary permissions for your use case.
- Securely manage the access to your RabbitMQ server.

## Contributing
Contributions to the `k8sman-helm-chart` are welcome. Please refer to the contribution guidelines for more information.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
