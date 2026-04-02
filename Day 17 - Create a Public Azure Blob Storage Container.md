## Day 17 - Create a Public Azure Blob Storage Container

## Task Details:

As part of the data migration process, the Nautilus DevOps team is actively creating several storage containers on Azure. They plan to utilize public Blob containers to store the relevant data. Given the ongoing migration of other infrastructure to Azure, it is logical to consolidate data storage within the Azure environment as well.

- Create a new storage account named `devopsst21175` and a `public` Blob container named `devops-blob-1048` within the storage account.

  > Make sure `anonymous read access for containers and blobs` is enabled

## Steps:

1. Sign in to the [Azure Portal](https://portal.azure.com/)

2. From the Azure portal dashboard, select and create storage account

    <img width="762" height="381" alt="546759009-ed83f3ed-6a4b-4162-9b5e-b943f92c5694" src="https://github.com/user-attachments/assets/1458663d-254c-4e39-88b5-3ebbfbca0def" />

4. On the Basics tab, select the existing resource group, and enter the following:

    <img width="587" height="437" alt="547109174-e19b49a2-9000-48bb-a311-c58acf9676c1" src="https://github.com/user-attachments/assets/99f49e7a-7007-4cc2-af95-588e5ee26bc4" />
 
5. Review + create.

6. In the storage account `devopsst21175` > Data storage > Containers > add the Blob container `devops-blob-1048`

    <img width="680" height="562" alt="547118356-cbf55c50-df45-4357-8e14-b1ccab25db6e" src="https://github.com/user-attachments/assets/a23cfc8c-1b25-4c4a-bf28-5e1ae9383547" />
 
7. In the storage account `devopsst21175` > Settings > Configuration, and then enable `Allow Blob Anonymous Access` and clik on Save.

    <img width="623" height="553" alt="547125474-bb83f61f-e4e6-478f-a420-0c8cca4606c0" src="https://github.com/user-attachments/assets/7666d42b-b784-433e-b0f9-64071207ac4f" />

8. In the storage account `devopsst21175` > Data storage > Containers > choose the newly created container, and then select `Change access level`

    <img width="676" height="454" alt="547130773-980e02a2-027c-49f7-b731-d811ed4c4e2a" src="https://github.com/user-attachments/assets/8a01bd0d-23aa-47be-9824-44f8180ef67f" />

9. Select Containers (anonymous read access for containers and blobs)

    <img width="680" height="318" alt="547131926-7df39339-8e30-445a-a778-88c180c69b00" src="https://github.com/user-attachments/assets/a7e6d46f-e033-4205-9910-c7717e66f374" />







