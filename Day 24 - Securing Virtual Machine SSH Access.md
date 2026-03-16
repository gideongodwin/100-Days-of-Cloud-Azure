## Day 24: Day 24: Securing Virtual Machine SSH Access

#### Task Details:
The Nautilus DevOps team needs to set up a new Virtual Machine (VM) on the Azure cloud that can be accessed securely from their landing host (azure-client). Follow the steps below to complete this task:
- Create an SSH Key: On the azure-client host, check if an SSH key already exists. If it doesn’t exist, create a new SSH key on the `azure-client` host that will be used for password-less SSH access.
- Create a Virtual Machine: Use the `Azure Portal` or `Azure CLI` to create a new Virtual Machine named `datacenter-vm` in the `westus` region. Set the VM size to `Standard_B1s` and configure the VM with SSH access for the azureuser account using the newly created SSH key.
- Configure SSH Access: Ensure that the SSH key from the `azure-client` host is added to the azureuser account on datacenter-vm, enabling secure, password-less SSH access from the azure-client host.
- Verify Connectivity: Test the connection from azure-client to datacenter-vm using SSH to confirm that password-less access has been set up correctly

#### STEPS
1. Generate the SSH Key
  `ssh-keygen`
  `cat /root/.ssh/id_rsa.pub`

2. Sign in to the [Azure Portal](https://portal.azure.com/)
3. From the Azure portal dashboard, Click on Virtual Machines and Create.

<img width="679" height="238" alt="Screenshot 2026-02-19 115901" src="https://github.com/user-attachments/assets/8590fa02-ff61-4a6b-a689-4d2bf2b529bf" />

#### CREATE THE VM ON THE AZURE PORTAL

4. On the Basics tab, enter datacenter-vm in the Virtual machine name field

<img width="680" height="399" alt="Screenshot 2026-02-19 120318" src="https://github.com/user-attachments/assets/64d68207-709d-414b-84e9-1c84fb1fe342" />

5. Paste the ssh key, generated on azure client.
<img width="676" height="197" alt="Screenshot 2026-02-19 120210" src="https://github.com/user-attachments/assets/b0f46183-feb6-4426-af6d-d309a156ee9e" />

6. Set the VM size to Standard_B1s

<img width="682" height="252" alt="Screenshot 2026-02-19 120133" src="https://github.com/user-attachments/assets/90eaba80-96d9-419b-a5f8-8d863ebbb3f5" />


