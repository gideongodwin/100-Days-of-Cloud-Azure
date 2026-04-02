## Day 16: Create a Private Azure Blob Storage Container

## Task Details:

As part of the data migration process, the Nautilus DevOps team is actively creating several storage containers on Azure. They plan to utilize private Blob containers to store the relevant data. Given the ongoing migration of other infrastructure to Azure, it is logical to consolidate data storage within the Azure environment as well.

- Create a new storage account named `devopsst6317` and a private Blob container named `devops-blob-16273` within the storage account

## Steps:

1. Sign in to the [Azure Portal](https://portal.azure.com/)

2. From the Azure portal dashboard, select and create storage account

    <img width="762" height="381" alt="546759009-ed83f3ed-6a4b-4162-9b5e-b943f92c5694" src="https://github.com/user-attachments/assets/5270a17c-9e84-419c-bd51-209d3e31fe40" />

3. On the Basics tab, select the existing resource group, and enter the following:

    <img width="790" height="421" alt="546759359-8fc45382-9aaf-42d6-b05c-ffe19ffcf9f7" src="https://github.com/user-attachments/assets/00a476ca-c5a8-4475-b6c8-121e0d5d6264" />

4. Review + create.

5. In the storage account `devopsst6317` > Data storage > Containers > add the Blob container `devops-blob-16273`

    <img width="954" height="828" alt="546760039-98e20ba0-0243-485e-b4e2-ad79aa847334" src="https://github.com/user-attachments/assets/f0a81842-9a39-4518-8f7f-a9fc5ef5ccef" />

6. Click on create

