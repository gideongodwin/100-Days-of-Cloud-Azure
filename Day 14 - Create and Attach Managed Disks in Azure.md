## Day 14: Create and Attach Managed Disks in Azure

#### Task Details:
The Nautilus DevOps team is strategizing the migration of a portion of their infrastructure to the Azure cloud. Recognizing the scale of this undertaking, they have opted to approach the migration in incremental steps rather than as a single massive transition. To achieve this, they have segmented large tasks into smaller, more manageable units. This granular approach enables the team to execute the migration in gradual phases, ensuring smoother implementation and minimizing disruption to ongoing operations. By breaking down the migration into smaller tasks, the Nautilus DevOps team can systematically progress through each stage, allowing for better control, risk mitigation, and optimization of resources throughout the migration process.

Create a managed disk with the following requirements:
- Name of the disk should be `devops-disk`
- Disk `type` must be `Standard_LRS`
- Disk `size` must be `2 GiB`

1. Sign in to the [Azure Portal](https://portal.azure.com/)

2. Search for and select Disks.

<img width="683" height="263" alt="Screenshot 2026-02-06 131831" src="https://github.com/user-attachments/assets/0223888d-ad26-4484-8acb-e1d291bf8f6f" />

3. Click on create

<img width="679" height="530" alt="Screenshot 2026-02-06 131917" src="https://github.com/user-attachments/assets/fd349f85-45b8-436a-892d-05b436a400c1" />

4. On the Basics tab, select the existing Resource group, and specify `devops-vm` as the VM name.

<img width="685" height="595" alt="Screenshot 2026-02-06 132036" src="https://github.com/user-attachments/assets/cc0ba856-99a2-4903-900f-b7a63da914d2" />

5. Select Size to change the disk `size` and disk `type`

<img width="685" height="595" alt="Screenshot 2026-02-06 132036" src="https://github.com/user-attachments/assets/8fdcb76c-1434-4082-a6ef-2e1bceea3fa7" />

6 Select `Standard HDD` as the disk type, and set the disk size to `2 GB`

<img width="683" height="601" alt="Screenshot 2026-02-06 132055" src="https://github.com/user-attachments/assets/c92e3848-7888-43ab-aebe-b5404a52a3e5" />
<img width="679" height="597" alt="Screenshot 2026-02-06 132142" src="https://github.com/user-attachments/assets/4c30a2ce-4dde-4dfd-b813-055600b6339f" />

7. On the Review + create tab, review the configuration, and then select Create

<img width="681" height="598" alt="Screenshot 2026-02-06 132221" src="https://github.com/user-attachments/assets/4420899e-da96-4db9-a6b8-679daac3b188" />



