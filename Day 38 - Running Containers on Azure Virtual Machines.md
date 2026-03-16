## Day 38: Running Containers on Azure Virtual Machines

#### Task Details:
The Nautilus DevOps team needs to set up an Azure Virtual Machine (VM) to interact with an Azure Blob Storage container for storing and retrieving data. The team must create a private storage account, configure Blob Storage, and test the functionality.

1) Azure Virtual Machine Setup: The VM named `nautilus-vm` already exists in the East US region.

2) Create a Private Storage Account and Blob Container:
  - Create a storage account named `nautilusstor7355` in the East US region with Locally-redundant storage (LRS).
  - Create a private Blob container named `nautilus-container7355`

3) Retrieve Storage Account Key:
  - Get the storage account's access key to configure access for the application.

4) Create a Test File:
  - SSH into the VM and create a file named testfile.txt in the /home/azureuser directory with content: "this is a test file".

5) Upload the File to Blob Storage:
  - Upload the testfile.txt file to the Blob container nautilus-container7355 using the Azure CLI command:

#### STEPS:
1. Sign in to the [Azure Portal](https://portal.azure.com/)
2. From the Storage Accounts dashboard, click on create button.

<img width="752" height="334" alt="Screenshot 2026-03-12 184248" src="https://github.com/user-attachments/assets/28e4ee18-17c7-4330-ae70-1263c48f1779" />

3. On the Basics tab, select the existing Resource group, and then enter a name for the Storage account.

<img width="769" height="837" alt="Screenshot 2026-03-12 184347" src="https://github.com/user-attachments/assets/4968a62b-d4bb-47ed-9e92-1997af05a71d" />

4. On the storage account, add a new container (private)

<img width="922" height="765" alt="Screenshot 2026-03-12 184701" src="https://github.com/user-attachments/assets/a0d67150-5887-4419-b364-4eda1ca9fa57" />

5. SSH into the `nautilus-vm` and switch to root user
```
ssh azureuser@<nautilus-vm public-ip>
sudo -i
 ```  
7. Edit the `testfile.txt` add the following `"this is a test file and save"`
```
vi testfile.txt
```
8. Copy the access key and Upload the File to Blob Storage

<img width="957" height="683" alt="Screenshot 2026-03-12 185052" src="https://github.com/user-attachments/assets/15407fb6-8769-4fdb-8665-4e1b1d7712df" />


```
az storage blob upload --account-name nautilusstor7355 --account-key <access-key> --container-name nautilus-container7355 --name testfile.txt --file /home/azureuser/testfile.txt`
