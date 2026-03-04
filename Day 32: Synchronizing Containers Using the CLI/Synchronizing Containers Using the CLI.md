## Day 32: Synchronizing Containers Using the CLI

#### Task Details
As part of a data migration project, the team lead has tasked the team with migrating data from an existing Azure Blob container to a new Blob container. 
The existing container contains a substantial amount of data that must be accurately transferred to the new container. The team is responsible for creating the new Blob container and ensuring that all data from the existing container is copied or synced to the new container completely and accurately. It is imperative to perform thorough verification steps to confirm that all data has been successfully transferred to the new container without any loss or corruption.
As a member of the Nautilus DevOps Team, your task is to perform the following:
- Create a New Private Azure Blob Container: Name the container devops-dest-17395 under the storage account devopsst32386.
- Data Migration: Migrate the file devops.txt from the existing devops-source-24632 container to the new devops-dest-17395 container.
- Ensure Data Consistency: Ensure that both containers have the file devops.txt and confirm the file content is identical in both containers.

#### STEPS:
1. Create the new private Blob container under the destination storage account
  `az storage container create --name devops-dest-17395 --account-name devopsst32386`

2. Verify the storage account was created
  `az storage container list --account-name devopsst32386 --output table`
