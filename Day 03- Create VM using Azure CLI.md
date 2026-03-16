## Day 3: Create VM using Azure CLI

#### Task Details:
The Nautilus DevOps team is in the process of migrating some of their workloads to Azure. One of the tasks involves creating a new Virtual Machine (VM) using the Azure CLI. The team does not have access to the Azure portal but can manage Azure resources via the azure-client host (the landing host for this lab).

- Create a new Azure Virtual Machine named xfusion-vw using the Azure CLI.
- Use the Ubuntu2204 Image and set the VM size to Standard_825
- Make sure the admin username is set to azureuser and SSH keys are generated for secure access.
- Use Standard LRS storage account, disk size must be 30GB and ensure the VM xfusion-vm is in the running state after creation.

#### STEPS
1. Check the resource group name using the following command:
   az group list
2. Run the following command:
   
      `az vm create \` \
           `-g $group \` \
           `-n xfusion-vm \` \
           `--image Ubuntu2204 \` \
           `--size Standard_B2s \` \
           `--admin-username azureuser \` \
           `--generate-ssh-keys \` \
           `--storage-sku Standard_LRS \` \
           `--data-disk-sizes-gb 30 `
 
