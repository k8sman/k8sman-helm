# k8sman-agent Installation Guide

This guide explains how to install the `k8sman-agent` in your Kubernetes cluster using Helm. Follow the steps below to configure the Helm repository and install the agent.

### Step 1: Add the Helm Repository
First, add the `k8sman` Helm repository to your environment. This will allow you to access the official Helm charts.

```sh
helm repo add k8sman https://k8sman.github.io/k8sman-helm
helm repo update
```

- **`helm repo add`**: Adds the `k8sman` repository to your list of Helm repositories.
- **`helm repo update`**: Updates the list of available charts from the configured repositories.

### Step 2: Install the k8sman-agent
Now, you can install the `k8sman-agent` in your Kubernetes cluster with the following command:

```sh
helm install k8sman-agent k8sman/k8sman-helm \
  --set agent.key=YOUR_AGENT_KEY_HERE
```

- **`helm install`**: Installs the `k8sman-agent` in the cluster.
- **`k8sman-agent`**: Helm release name (can be customized as desired).
- **`k8sman/k8sman-helm`**: Name of the chart in the `k8sman` repository.
- **`--set agent.key`**: Sets the agent authentication key. The key must be obtained via the [k8sman platform](https://k8sman.io). Replace `YOUR_AGENT_KEY_HERE` with the key provided for your environment.

### Additional Tips
- Ensure you have administrative access to your Kubernetes cluster and that Helm is properly configured.
- If you do not have Helm installed, refer to the official Helm documentation at [https://helm.sh/docs/intro/install/](https://helm.sh/docs/intro/install/).
- Keep the agent key secure, as it is used for authentication.

### Full Command
To summarize, the command to add the repository and install the `k8sman-agent` is:

```sh
helm repo add k8sman https://k8sman.github.io/k8sman-helm
helm repo update
helm install k8sman-agent k8sman/k8sman-helm \
  --set agent.key=YOUR_AGENT_KEY_HERE
```

Thus, the `k8sman-agent` will be installed in your cluster and ready to use.

For more information, visit [k8sman.io](https://k8sman.io).