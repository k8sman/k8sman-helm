# k8sman-helm-chart

## Overview
`k8sman` is a management platform for Kubernetes clusters, designed to facilitate the execution of administrative commands and orchestrate interactions within the cluster. The `k8sman-helm-chart` deploys the `k8sman-agent` in Kubernetes clusters, enabling seamless communication with RabbitMQ for efficient message passing and management tasks.

## Prerequisites
- Kubernetes cluster with internet access.
- Helm 3 installed.

## TLS Certificate Configuration
To enable TLS communication with RabbitMQ, place your TLS certificate and key in the `certs` directory of the chart before installation. The directory structure should look like this:

```
k8sman-helm-chart
└── charts
    └── k8sman-agent
        ├── certs
        │   ├── rabbitmq-cert.crt  # Your RabbitMQ certificate
        │   └── rabbitmq-key.key   # Your RabbitMQ key
        └── ... # Other chart files
```

## Adding the Helm Repository
To use the `k8sman-helm-chart`, you need to add the repository to Helm:

```shell
helm repo add k8sman https://ovrdoz.github.io/k8sman-helm-chart
helm repo update
```

## Installing the Chart
Install the `k8sman-agent` chart with the following command, replacing `xxxx` with your RabbitMQ configuration:

```shell
helm install k8sman-agent k8sman/k8sman-agent \
    --set rabbitmq.host="xxxx" \
    --set rabbitmq.vhost="xxxx" \
    --set rabbitmq.user="xxxx" \
    --set rabbitmq.pass="xxxx" \
    --set rabbitmq.useTLS=true \
    --set rabbitmq.certPath="path/to/cert.crt" \ # sample
    --set rabbitmq.keyPath="path/to/key.key" # sample
```

To find the latest version of the chart, use:

```shell
helm search repo k8sman
```

## Uninstalling the Chart
To uninstall the `k8sman-agent` chart:

```shell
helm delete k8sman-agent
```

## Configuration
The chart can be customized using various parameters. These are specified in the `values.yaml` file or can be overridden via the command line.

| Parameter            | Description                           | Default Value                  |
|----------------------|---------------------------------------|--------------------------------|
| `replicaCount`       | Number of `k8sman-agent` replicas     | `1`                            |
| `image.repository`   | `k8sman-agent` image repository       | `ovrdoz/k8sman-agent`          |
| `image.pullPolicy`   | Image pull policy                     | `Always`                       |
| `image.tag`          | `k8sman-agent` image tag              | `latest`                       |
| `rabbitmq.host`      | RabbitMQ server host                  | `<host>`                       |
| `rabbitmq.vhost`     | RabbitMQ server virtual host          | `<vhost>`                      |
| `rabbitmq.user`      | RabbitMQ username                     | `<username>`                   |
| `rabbitmq.pass`      | RabbitMQ password                     | `<encoded-password>`           |
| `rabbitmq.useTLS`    | Enable TLS communication              | `false`                        |
| `rabbitmq.certPath`  | Path to RabbitMQ TLS certificate      | `path/to/cert.pem`             |
| `rabbitmq.keyPath`   | Path to RabbitMQ TLS key              | `path/to/key.pem`              |

### RBAC Configuration
`k8sman-agent` requires extensive permissions to manage the Kubernetes cluster. Modify the RBAC settings in `rbac.yaml` according to your security policies and needs.

## Security Considerations
Ensure the `k8sman-agent` runs with necessary permissions and manage RabbitMQ server access securely.

## Contributing
Contributions are welcome. Please refer to the contribution guidelines for more information.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
