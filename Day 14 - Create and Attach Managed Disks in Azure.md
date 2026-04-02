## Day 14 - Create and Attach Managed Disks in Azure

## Task Details:

The Nautilus DevOps team is strategizing the migration of a portion of their infrastructure to the Azure cloud. Recognizing the scale of this undertaking, they have opted to approach the migration in incremental steps rather than as a single massive transition. To achieve this, they have segmented large tasks into smaller, more manageable units. This granular approach enables the team to execute the migration in gradual phases, ensuring smoother implementation and minimizing disruption to ongoing operations. By breaking down the migration into smaller tasks, the Nautilus DevOps team can systematically progress through each stage, allowing for better control, risk mitigation, and optimization of resources throughout the migration process.

- Create a managed disk with the following requirements:
   
    - Name of the disk should be `devops-disk`
   
    - Disk `type` must be `Standard_LRS`
    
    - Disk `size` must be `2 GiB`

## Steps:

1. Sign in to the [Azure Portal](https://portal.azure.com/)

2. Search for and select Disks in the Azure portal search bar

  <img width="580" height="215" alt="546178651-0223888d-ad26-4484-8acb-e1d291bf8f6f" src="https://github.com/user-attachments/assets/75cd4ea6-531b-4014-9d24-68dd799c0f5f" />

3. Click on create

  <img width="679" height="217" alt="546180625-fd349f85-45b8-436a-892d-05b436a400c1" src="https://github.com/user-attachments/assets/18d2457c-5d71-4352-92f2-c51084082141" />
 
4. On the Basics tab, select the existing Resource group, and enter the following

  <img width="586" height="358" alt="546183711-cc0ba856-99a2-4903-900f-b7a63da914d2" src="https://github.com/user-attachments/assets/2b90704f-18cf-4abc-8a55-5fdd54d7eda4" />
 
5. Select Size to change the disk `size` and disk `type`

  <img width="666" height="85" alt="546184249-8fdcb76c-1434-4082-a6ef-2e1bceea3fa7" src="https://github.com/user-attachments/assets/45220007-d023-4d64-8711-d709ad698f31" />
 
6 Select `Standard HDD` as the disk type, and set the disk size to `2 GB`

  <img width="657" height="522" alt="546193327-c92e3848-7888-43ab-aebe-b5404a52a3e5" src="https://github.com/user-attachments/assets/6a77510b-e65a-469d-ba35-b2e372d32d8c" />
  
  <img width="661" height="565" alt="546193901-4c30a2ce-4dde-4dfd-b813-055600b6339f" src="https://github.com/user-attachments/assets/e43b1945-98f9-49c5-987b-ca1449e109fa" />
   
7. Review + create

<img width="681" height="598" alt="Screenshot 2026-02-06 132221" src="https://github.com/user-attachments/assets/4420899e-da96-4db9-a6b8-679daac3b188" />



