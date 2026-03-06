## Day 18: Copy Data to an Azure Blob Storage Container

#### Task Details:
The Nautilus DevOps team is presently immersed in data migrations, transferring data from on-premise storage systems to Azure Blob containers. They have recently received some data that they intend to copy to one of the Blob containers.
A Blob container named `datacenter-blob-9136` already exists in the `Central US` region under the storage account `datacenterst665` 
- Copy the file `/tmp/datacenter.txt` to the Blob container `datacenter-blob-9136`

1. Verify the storage account
- az storage account list | grep name

2. Use the Azure CLI to upload the local file to the specified Blob container.
- az storage blob upload --account-name datacenterst665 -c datacenter-blob-9136 -f /tmp/datacenter.txt


