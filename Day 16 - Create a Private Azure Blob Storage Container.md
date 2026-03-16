## Day 16: Create a Private Azure Blob Storage Container

#### Task Details:
As part of the data migration process, the Nautilus DevOps team is actively creating several storage containers on Azure. They plan to utilize private Blob containers to store the relevant data. Given the ongoing migration of other infrastructure to Azure, it is logical to consolidate data storage within the Azure environment as well.
- Create a new storage account named devopsst6317 and a private Blob container named devops-blob-16273 within the storage account

1. Sign in to the [Azure Portal](https://portal.azure.com/)

2. From the Azure portal dashboard, select Storage accounts
3. Click Create to create a new storage account

<img width="952" height="393" alt="Screenshot 2026-02-08 154051" src="https://github.com/user-attachments/assets/ed83f3ed-6a4b-4162-9b5e-b943f92c5694" />

4. On the Basics tab, select the existing Resource group, and then enter a name for the Storage account.

<img width="958" height="870" alt="Screenshot 2026-02-08 154144" src="https://github.com/user-attachments/assets/8fc45382-9aaf-42d6-b05c-ffe19ffcf9f7" />

5. Select Review + create.

6. After the deployment is complete, select Go to resource

<img width="953" height="185" alt="Screenshot 2026-02-08 154234" src="https://github.com/user-attachments/assets/42cfd542-f08f-4072-a4e1-50438162e38f" />

7. In the storage account, under Data storage, select Containers, and then select + Container
8. Select Add, and then enter a name for the container.

<img width="954" height="871" alt="Screenshot 2026-02-08 154352" src="https://github.com/user-attachments/assets/98e20ba0-0243-485e-b4e2-ad79aa847334" />

9. Click on create

