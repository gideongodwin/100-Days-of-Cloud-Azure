## Day 10 - Attach Managed Disk to Azure Virtual Machine

## Task Details:

The Nautilus DevOps team has already set up a virtual machine and allocated a public IP address. The final task is to attach this public IP to the VM's network interface card (NIC)

- An existing VM named `xfusion-vm-pip` and a public IP address named `xfusion-pip` already exist

- Attach the public `xfusion-pip` to the network interface of the VM Hautilus `xfusion-vm-pip`

> Make sure the VM is properly assigned the public IP

## STEPS:

1. Sign in to the [Azure Portal](https://portal.azure.com/)

2. On the virtual network page >  Public IP addresses > select the `xfusion-pip`

   <img width="685" height="316" alt="552730308-4d665cb1-bc09-45ca-89d9-869f38497295" src="https://github.com/user-attachments/assets/1e7988aa-b817-4c4d-9f8f-3b3943913fe4" />

3. Select Associate to attach the `xfusion-pip` address to the virtual machine.

   <img width="1169" height="313" alt="538482456-86df3a29-22f6-4fec-8845-464124ff986e" src="https://github.com/user-attachments/assets/f5b04c97-5889-43ba-a1b9-bfe2854953ff" />

4. Select the Network interface as the resource type

   <img width="1362" height="286" alt="538483117-b79e161b-24e8-4ae5-9e11-f395cc495ca4" src="https://github.com/user-attachments/assets/0012f276-1ee8-406c-be67-5d9bcfeb669c" />

5.  Click on OK

