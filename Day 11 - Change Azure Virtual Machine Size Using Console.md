## Day 11: Change Azure Virtual Machine Size Using Console

## Task Details:

The Nautilus Devops team is migrating a portion of their infrastructure to Azure. During the migration, they have created several virtual machines (VMs) in different regions. The team has identified one VM that is underutilized and has decided to change its size to optimize resource usage.

- Change the VM size from `Standard_B1s` to Standard `Standard_B2s` for the virtual machine named `nautilus-vm`

- Ensure the VM is in the `running` state after the size change is complete.

## Steps:

1. Sign in to the [Azure Portal](https://portal.azure.com/)

2. On the virtual machines page, select the available vm `nautilus-vm`

   <img width="679" height="350" alt="538583224-d8307976-f92a-480a-b2e4-8b7f269cbcee" src="https://github.com/user-attachments/assets/2f069948-0db1-43ea-8113-d2a6e27b963f" />

3. Select Size, and then choose `B2s` to replace the current virtual machine size.
      
   <img width="1364" height="599" alt="Screenshot 2026-01-21 120803" src="https://github.com/user-attachments/assets/348aa9dc-6a21-4903-8e54-d15ceac11087" />

4. Click on Resize

   <img width="1365" height="598" alt="Screenshot 2026-01-21 120904" src="https://github.com/user-attachments/assets/90682f2a-be13-477e-a0a0-ec9e52abf69b" />
