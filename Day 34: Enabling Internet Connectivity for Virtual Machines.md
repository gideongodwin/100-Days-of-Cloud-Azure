## Day 34: Enabling Internet Connectivity for Virtual Machines

#### Task Details:
The Nautilus DevOps team has encountered an issue with an Azure VM named datacenter-vm. They are unable to install any packages on this VM due to connectivity issues. The team needs to identify the root cause of the problem and resolve it to restore normal operations.

Investigate the connectivity issue preventing package installation on the Azure VM datacenter-vm.
Implement a solution to resolve the connectivity issue and restore package installation capabilities on the VM.
Note: The SSH key required to access the Azure VM is already created and added to the VM's authorized keys. You can find the SSH key at /root/.ssh/id_rsa on the azure-client host.

#### STEPS:
1. Retrieve the Public IP Address of the VM
```
az vm list-ip-addresses -n datacenter-vm \
-g $(az group list --query '[].name' --output tsv | grep kml)
```
2. SSH into the Azure VM \
   `ssh azureuser@<VM_PUBLIC_IP>`

3. Check if the server can reach the internet \
   `ping 8.8.8.8`

4. Sign in to the [Azure Portal](https://portal.azure.com/)
5. Select Resource Groups from the Azure portal dashboard 

<img width="539" height="174" alt="Screenshot 2026-03-06 093228" src="https://github.com/user-attachments/assets/3a07c630-d0a2-4537-b777-2a2c616d9b19" />

6. Select the existing resource group
<img width="651" height="271" alt="Screenshot 2026-03-06 093239" src="https://github.com/user-attachments/assets/ccca47b0-17f7-4406-97db-4d11fcf9b375" />

7. Select the NSG
<img width="679" height="369" alt="Screenshot 2026-03-06 093255" src="https://github.com/user-attachments/assets/af71f022-0926-4075-801d-c2961714686d" />

8. Delete the rule `Block-All-Outbound` This allows outbound traffic again

<img width="1365" height="600" alt="Screenshot 2026-03-06 093344" src="https://github.com/user-attachments/assets/870ff371-22c5-4176-a1bb-93b9c08c7c60" />

9. Verify Internet Connectivity Again \
    `ping 8.8.8.8`
