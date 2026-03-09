## Day 36: Managing Storage Lifecycle in Azure

#### Task Details:
The Nautilus DevOps team needs to optimize data retention costs by automating the deletion of old blobs. They plan to implement Blob Lifecycle Management for a specific container in Azure Storage.

Task:
1) Create a Storage Account:

Name the storage account `devopsstor713`
Set the region to East US.
Use Locally-redundant storage (LRS) as the redundancy option.
2) Create a Blob Container:

Name the container `devops-container713`

3) Upload a File to the Container:

Upload the file named `tempfile.txt` to the container. The file is present under `/root` of the client host.
4) Configure Blob Lifecycle Management:

Apply a Lifecycle Management rule named `devops-del-rule` to the container `devops-container713` to delete blobs after `7` days of last modification.
5) Validation: Verify that the Lifecycle Management rule named `devops-del-rule` is correctly applied

#### STEPS:
