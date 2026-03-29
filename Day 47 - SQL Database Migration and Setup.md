## Day 47: SQL Database Migration and Setup

## Task Details:
The Nautilus DevOps team is strategizing the migration of a portion of their infrastructure to Azure. Recognizing the scale of this undertaking, they have opted to approach the migration in incremental steps rather than as a single massive transition. As part of this migration, they are focusing on setting up and managing Azure SQL Databases, implementing backup processes, and ensuring data recovery. Below are the tasks they require you to perform:

Task 1: Create an Azure SQL Database

- Create a `publicly accessible` Azure SQL Database instance with the following details:
  - Database Name: `nautilus-sqldb`
  - Server Name: `nautilus-server-31595`
  - Location: `West US`
  - Backup Storage Redundancy: `Locally-redundant` backup storage`
  - Hardware Configuration: Basic (For less demanding workloads).
  - Admin Username: `nautilus-admin`
  - Admin Password: Set an appropriate password.
  - Database Size: Set to `2 GiB`
  - Keep all other configurations as `default`
  - Ensure the database is in the `Ready` state.

Task 2: Create a Storage Account

  - Create a Storage Account named `nautilusst16514`
  - Configure a Blob Container named `nautilus-container-19777` within this storage account.

Task 3: Backup the Azure SQL Database
Take a backup of the Azure SQL Database instance `nautilus-sqldb` and store it in the Blob Container:
  - Storage Account: `nautilusst16514`
  - Blob Container: `nautilus-container-19777`
  - Backup File Name: `nautilus-db-backup`
  - Ensure the backup is fully exported to the blob container.

Task 4: Download the Backup

  - Download the backup file from the Blob Container to the `/opt` directory on the azure-client host
  - Ensure the file is accessible and properly named based on its extension.
  - Requirements for Completion
  - Ensure the SQL Database is in the `Ready` state
  - Confirm the backup is stored in the specified Blob Container.
  - Verify the backup file is successfully downloaded to the `/opt` directory on the client host.

## Steps

1. Sign in to the [Azure Portal](https://portal.azure.com/)

2. Search for and select SQL Server in the azure portal search bar

    <img width="762" height="277" alt="Screenshot 2026-03-29 105102" src="https://github.com/user-attachments/assets/07f335e3-457d-4acb-bdfe-afb59222e285" />

3. On the Basics tab, configure the following;

    <img width="926" height="596" alt="Screenshot 2026-03-29 133912" src="https://github.com/user-attachments/assets/1418d3c4-6ce8-45b2-b630-13910f1358d3" />
    
    <img width="907" height="441" alt="Screenshot 2026-03-29 105332" src="https://github.com/user-attachments/assets/d03345f7-be72-4268-a865-025f3ce08724" />

4. On the Networking tab, > Firewall rules > set Allow Azure services and resources to access this server to `Yes`

    <img width="746" height="272" alt="Screenshot 2026-03-29 133925" src="https://github.com/user-attachments/assets/8c462f32-980e-4229-b854-cd8a5ffc6de7" />

5. Review + Create

6. Search for and select SQL databases in the azure portal search bar
7. Select the + Create dropdown button and select SQL database.

    <img width="928" height="387" alt="Screenshot 2026-03-29 134255" src="https://github.com/user-attachments/assets/4873bc97-68f1-462e-9f72-69d5d0d2a341" />

8. On the Basics tab of the Create SQL Database form, under Project details, configure the following:
    
    <img width="891" height="628" alt="Screenshot 2026-03-29 134355" src="https://github.com/user-attachments/assets/b824e09d-efb2-4f41-bf5e-06b3a9e3c548" />
    
    <img width="905" height="296" alt="Screenshot 2026-03-29 134424" src="https://github.com/user-attachments/assets/9055ae8e-d6ac-42cf-af7a-af5d7266d36b" />

9. Review + Create

10. From the Azure portal dashboard, select and create storage account `nautilusst16514`

    <img width="918" height="287" alt="Screenshot 2026-03-29 134623" src="https://github.com/user-attachments/assets/75da7086-ba13-41d1-9c0c-a4abbc8367bb" />

11. On the Basics tab, select the existing Resource group, and enter the following:

    <img width="954" height="770" alt="Screenshot 2026-03-29 135138" src="https://github.com/user-attachments/assets/dca17fc7-9d9f-4838-b2ff-0fbee5b9b495" />

12. Review + Create

13. In the storage account `nautilusst16514`, under Data storage, select Containers, and then add the Blob container `nautilus-container-19777` 

    <img width="941" height="676" alt="Screenshot 2026-03-29 135414" src="https://github.com/user-attachments/assets/2fc4b39f-fca4-49e5-8d0c-348f5d59fb39" />

14. Navigate to SQL Database `nautilus-sqldb`,  then click Export

    <img width="904" height="235" alt="Screenshot 2026-03-29 135510" src="https://github.com/user-attachments/assets/8135a6db-756f-4824-9c2b-1dbd77c2af9d" />

15.  Store it in the Blob Container  `nautilus-container-19777` 
    <img width="938" height="823" alt="Screenshot 2026-03-29 135559" src="https://github.com/user-attachments/assets/fe3bf13b-4bd9-47d5-8b65-1ddeca2c2446" />

16. Navigate to the SQL server to confirm the export has completed before downloading the backup.

    <img width="720" height="610" alt="Screenshot 2026-03-29 140029" src="https://github.com/user-attachments/assets/fcad8c80-891e-4e11-9b3f-68dedfa85370" />

17. Run the following command in the Azure CLI to download the backup.

    ```
    az storage blob download \
      --account-name nautilusst16514 \
      --container-name nautilus-container-19777 \
      --name nautilus-db-backup.bacpac \
      --file /opt/nautilus-db-backup.bacpac \
      --auth-mode login
    ```

18. Verify file exists:

    ```
    ls -l /opt/
    ```

