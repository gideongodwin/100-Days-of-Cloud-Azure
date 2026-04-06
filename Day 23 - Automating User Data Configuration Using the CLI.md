## Day 23 - Automating User Data Configuration Using the CLI

## Task Details:
The Nautilus DevOps Team is working on setting up a new virtual machine (VM) to host a web server for a critical application. The team lead has requested you to create an Azure VM that will serve as a web server using Nginx. This VM will be part of the initial infrastructure setup for the Nautilus project. Ensuring that the server is correctly configured and accessible from the internet is crucial for the upcoming deployment phase.

As a member of the Nautilus DevOps Team, your task is to create a VM using Azure CLI with the following specifications:

- Instance Name: The VM must be named `datacenter-vm`

- Image: Use any available Ubuntu image to create this VM

- Custom Script Extension/User Data: Configure the VM to run a custom script during its launch. This script should:

   - Install the `Nginx` package.

   - Start the `Nginx` service.
   
   - Network Security Group (NSG): Ensure that the VM allows `HTTP` traffic on port `80` from the internet.

## Steps:

1. Create the Cloud-Init Script
   ```
   vi user-data.txt
   ```
   Add the following content, then save and exit:
   ```
   #!/bin/bash
   apt update -y && apt install nginx -y
   systemctl start nginx
   ```

2. Create the Deployment Script
   ```
   vi deployment.sh
   ```
      
   Add the following content, then save and exit:
   ```
   #!/bin/bash
   name=$1
   script=$2
   
   rg=$(az group list --query '[].name' --output tsv | grep kml)
   
   az network nsg create \
     --name "${name}-nsg" \
     --resource-group $rg
   
   az network nsg rule create \
     --name Allow80Inbound \
     --resource-group $rg \
     --nsg-name "${name}-nsg" \
     --priority 1010 \
     --access Allow \
     --direction Inbound \
     --source-address-prefixes "*" \
     --source-port-ranges "*" \
     --destination-address-prefixes "*" \
     --destination-port-ranges 80 \
     --protocol Tcp
   
   az vm create \
     --name "${name}-vm" \
     --resource-group $rg \
     --image Ubuntu2404 \
     --admin-username azureuser \
     --generate-ssh-keys \
     --nsg "${name}-nsg" \
     --custom-data "${script}" \
     --size Standard_B1s \
     --storage-sku Standard_LRS
   ```

4. Make Script Executable
   ```
   chmod +x deployment.sh
   ```

5. Run the Script
   ```
   deployment.sh datacenter user-data.txt
   ```



      
