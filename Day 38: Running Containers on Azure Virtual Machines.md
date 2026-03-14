## Day 38: Running Containers on Azure Virtual Machines

#### Task Details:
The Nautilus DevOps team needs to set up an Azure Virtual Machine (VM) to interact with an Azure Blob Storage container for storing and retrieving data. The team must create a private storage account, configure Blob Storage, and test the functionality.

Task:
1) Azure Virtual Machine Setup: The VM named nautilus-vm already exists in the East US region.

2) Create a Private Storage Account and Blob Container:
  - Create a storage account named `nautilusstor7355` in the East US region with Locally-redundant storage (LRS).
  - Create a private Blob container named `nautilus-container7355`

3) Retrieve Storage Account Key:
  - Get the storage account's access key to configure access for the application.

4) Create a Test File:
  - SSH into the VM and create a file named testfile.txt in the /home/azureuser directory with content: "this is a test file".

5) Upload the File to Blob Storage:
  - Upload the testfile.txt file to the Blob container nautilus-container7355 using the Azure CLI command:
  - az storage blob upload --account-name nautilusstor7355 --account-key <access-key> --container-name nautilus-container7355 --name testfile.txt --file /home/azureuser/testfile.txt

#### STEPS:
1. Sign in to the [Azure Portal](https://portal.azure.com/)
2. From the Storage Accounts dashboard, click on create button

