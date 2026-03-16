## Day 21: Assigning Public IP to Virtual Machines

##Task Details
The Nautilus DevOps Team has received a new request from the Development Team to set up a new Azure Virtual Machine (VM). This VM will be used to host a new application that requires a stable public IP address. To ensure that the VM has a consistent public IP, a Static Public IP address needs to be associated with it. The VM will be named devops-vm, and the Static Public IP will be named devops-pip. This setup will help the Development Team to have a reliable and consistent access point for their application.
- Create an Azure VM named `devops-vm` using any available Ubuntu image, with the VM size `Standard_B1s`
- Generate an SSH public key on the `azure-client` host and associate it with the VM for SSH access
- Associate a Static Public IP address named `devops-pip` with this VM
- Ensure the VM is accessible via SSH using the generated public key

1. Sign in to the [Azure Portal](https://portal.azure.com/)
2. From the Azure portal dashboard, navigate to Virtual machines, and then select + Create

<img width="677" height="357" alt="Screenshot 2026-02-13 153748" src="https://github.com/user-attachments/assets/289d7993-4775-43de-8c65-60a1e94f8f15" />

3. On the Basics tab, under Project details, select the existing Resource group. Then enter the Virtual machine name and choose Central US as the Region

<img width="679" height="597" alt="Screenshot 2026-02-13 154507" src="https://github.com/user-attachments/assets/cc122b0d-9f58-4023-9688-e86c491d5877" />

4. Select the `Standard_B1s` vm size

<img width="683" height="411" alt="Screenshot 2026-02-13 154602" src="https://github.com/user-attachments/assets/e0d116d0-a686-440c-8e92-f82c749eef53" />

5. Select the use existing public key, Go to the Azure client and run the following commands, then copy and paste the public key into the SSH public key field.

- `ssh keygen`
- `cat /root/.ssh/id_rsa.pub`

<img width="678" height="372" alt="Screenshot 2026-02-13 155102" src="https://github.com/user-attachments/assets/12e78e19-e2cf-4011-81d3-6082970a8ecd" />

6. On the Disks tab, under OS disk, select the appropriate Disk type and configure the required Disk size (GiB) as needed

<img width="682" height="299" alt="Screenshot 2026-02-13 155226" src="https://github.com/user-attachments/assets/62457e21-a650-415c-80e8-668008f9ce29" />

7. On the Networking tab, under Public IP, select Create new, then provide the required details to configure the new public IP address.

<img width="674" height="595" alt="Screenshot 2026-02-13 155402" src="https://github.com/user-attachments/assets/7f1c8bd4-c765-4024-be73-a740e97520e9" />

8. Click on create

<img width="679" height="595" alt="Screenshot 2026-02-13 155434" src="https://github.com/user-attachments/assets/dea8a4be-6fea-4be0-98ef-eb652064e339" />





