## Day 29: Working with Azure Container Registry (ACR)

#### Task Details 

The Nautilus DevOps team has been tasked with setting up a containerized application. They need to create a Azure Container Registry (ACR) to store their Docker images. Once the repository is created, they will build a Docker image from a Dockerfile located on the `azure-client` host and push this image to the ACR repository. This process is essential for maintaining and deploying containerized applications in a streamlined manner.

1) Create a ACR repository named `devopsacr21738` under `East US`

2) Pricing plan must be `Basic`

3) Dockerfile already exists under `/root/pyapp` directory on `azure-client` host.

4) Build a Docker image using this Dockerfile and push the same to the newly created ACR repo. The image tag must be `latest` i.e `devopsacr21738:latest`

#### STEPS
- Step 1: Create the Azure Container Registry (ACR)
```
az acr create \
  --name devopsacr21738 \
  --resource-group $(az group list --query '[].name' --output tsv | grep kml) \
  --sku Basic \
  --location eastus
```
- Step 2: Navigate to the Dockerfile Directory
```
cd /root/pyapp
```
- Step 3: Build the Docker image and tag it correctly for ACR.
```
docker build -t devopsacr21738.azurecr.io/devopsacr21738:latest .
```
- Step 4: Login to Azure Container Registry
```
az acr login -n devopsacr21738
```
- Step 5: Push the Image to ACR
```
docker push devopsacr21738.azurecr.io/devopsacr21738:latest
```
- Step 6: Confirm the image was pushed successfully
```
az acr repository show-tags \
  -n devopsacr21738 \
  --repository devopsacr21738
```
