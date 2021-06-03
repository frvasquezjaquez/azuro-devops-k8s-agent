# Azure DevOps Pipeline Agent

## Prerequisites

* Azure DevOps Account 
* [Azure DevOps Access Token with Agent Pool Manage Permissions](https://docs.microsoft.com/en-us/azure/devops/pipelines/agents/v2-linux?view=azure-devops#authenticate-with-a-personal-access-token-pat)
* [Agent Pool Created in Azure DevOps](https://docs.microsoft.com/en-us/azure/devops/pipelines/agents/pools-queues?view=azure-devops)


## Create Docker Image

1. Clone the repo
   ```
   git clone <repository-url>
   ```
2. Build the docker image
   ```
    docker build -t <image-name>:<image-tag> .
   ```

## Deploy locally using docker-compose
1. Create a token file.
    ```
    echo "<azure-devops-agent-token>" > token
    ```
2. Replace env variables in the `docker-compose.yaml`.
3. Start the container.
   ```
   docker-compose up -d
   ```
4. Check status.
   ```
   docker-compose logs -f
   ```

## Deploy in Kubernetes

1. Replace the env variables in the `kube/configMap.yaml`
2. Set the Personal Access Token (PAT) in the `kube/tokenFile.yaml`
3. Apply the Kubernetes Objects
    ```
    kubectl apply -f kube/
    ```

# References:

* [Create Azure DevOps Docker Agents](https://docs.microsoft.com/en-us/azure/devops/pipelines/agents/docker?view=azure-devops)