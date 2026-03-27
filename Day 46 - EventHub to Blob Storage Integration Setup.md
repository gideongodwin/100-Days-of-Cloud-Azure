## Day 46 - EventHub to Blob Storage Integration Setup

## Task Details:

The Nautilus DevOps team wants to integrate an Azure Virtual Machine with Azure Event Hubs and Azure Blob Storage for centralized log collection and backup. Follow these steps to complete the task:

- Create Azure Event Hubs Namespace:
  
  > Create an Event Hubs namespace named `nautilus-namespace` in the `East US` region.
  
  > Select the `Standard` pricing tier. Make sure to enable `Enable Auto-inflate`

- Create an Event Hub:

   > Within the namespace, create an Event Hub named `nautilus-hub`

- Set Up Azure Blob Storage for Log Backup:

  > Create a Storage Account named `nautilusst1338` in the East US region.
  
  > Create a container named `nautilus-backup-29309` within the Storage Account.
  
  > Ensure the container is `publicly accessible` for read operations.

- Verify the Virtual Machine Configuration:

The client host already has a Python script named `send_logs.py` located under `/root`. This script is used to send logs to the Event Hub.

- Create a Virtual Machine named `nautilus-vm` in the East US region.

- Copy the `send_logs.py` script from the client host to the `/home/azureuser` directory of the nautilus-vm.

- Modify the script on the VM to also back up the logs to the `nautilus-backup-29309` container in the Azure Blob Storage account.

- Verify Logs:

  > Ensure the logs are successfully sent to the Event Hub by checking the Event Hubs metrics in the Azure portal.
  
  > Verify that the logs are backed up to the nautilus-backup-29309 container in the Azure Blob Storage.

## Steps: 

1. Sign in to the [Azure Portal](https://portal.azure.com/)

2. Search for and select Events in the azure portal search bar

<img width="571" height="229" alt="Screenshot 2026-03-26 151328" src="https://github.com/user-attachments/assets/2978bd1b-449f-4ee1-bcfd-8e771fe613e4" />

3. Select + Create

<img width="552" height="182" alt="Screenshot 2026-03-26 151335" src="https://github.com/user-attachments/assets/693e8ce9-6ff8-4d1b-820a-f1943508f6e3" />

4. On the Basics tab, configure the following:

<img width="616" height="418" alt="Screenshot 2026-03-26 151419" src="https://github.com/user-attachments/assets/062b97ae-7f88-4b56-ac12-bc5ca1c9c388" />

5. Select Review + create, then Create

6. On the newly created namespace `nautilus-namespace`, Under Entities, select + Event Hubs.

<img width="653" height="407" alt="Screenshot 2026-03-26 151557" src="https://github.com/user-attachments/assets/186852f6-b8ac-4502-b64a-356dfe7f5651" />

7. On the Basics tab, configure the following:

<img width="615" height="392" alt="Screenshot 2026-03-26 151812" src="https://github.com/user-attachments/assets/cdba1aee-61e0-4154-921f-18a81c5e0f69" />

8. From the Azure portal dashboard, select Storage accounts, then create

<img width="591" height="242" alt="Screenshot 2026-03-26 151846" src="https://github.com/user-attachments/assets/db5f3e7e-3d80-4991-a3c0-f73cf976bb7e" />

9. On the Basics tab, configure the following:
   
<img width="584" height="444" alt="Screenshot 2026-03-26 151958" src="https://github.com/user-attachments/assets/15145a94-3a08-460a-a0bd-1254b4f3656a" />

<img width="634" height="130" alt="Screenshot 2026-03-26 152004" src="https://github.com/user-attachments/assets/66c3dbff-2f02-42a2-afac-7f2f62197025" />

10. On the Advanced tab, configure the following:

<img width="583" height="201" alt="Screenshot 2026-03-26 152027" src="https://github.com/user-attachments/assets/81ded54a-cbcb-46e0-8441-32ba40fdc1ab" />

11. Select Review + create.

12. In the storage account `nautilusst1338`, under Data storage > Containers > select + Container

<img width="661" height="436" alt="Screenshot 2026-03-26 152215" src="https://github.com/user-attachments/assets/2e75e725-22f2-4b42-8606-140bc8aad16e" />

13. From the Azure portal dashboard, select Virtual Machines, then create

<img width="598" height="167" alt="Screenshot 2026-03-26 152248" src="https://github.com/user-attachments/assets/3030b9a3-4955-4355-a058-0e7242f05b0d" />

14. On the Basics tab, configure the following:

<img width="599" height="426" alt="Screenshot 2026-03-26 152548" src="https://github.com/user-attachments/assets/b27dcba1-dad9-4b8d-80c6-4e95b2c78c7c" />

15. In the Azure CLI, run the following command to create an SSH key:
   ```
    ssh-keygen
   ```

16. Copy the contents of the public key and paste
    ```
    cat .ssh/id_rsa.pub
    ```

    <img width="660" height="429" alt="Screenshot 2026-03-26 152617" src="https://github.com/user-attachments/assets/5358d9c1-523c-48e2-ba71-ade7c36c7093" />

17. Select the disk size and type.

<img width="609" height="130" alt="Screenshot 2026-03-26 152636" src="https://github.com/user-attachments/assets/54659896-cf61-40c6-8747-e76742ce480c" />

18. Select Review + create, then create

19.  In the Azure client, copy the `send_logs.py` script from the client host to the `/home/azureuser`.
    ```
    scp send_logs.py azureuser@20.51.156.119:/home/azureuser
    ```

20. ssh into vm `nautilus-vm`
    ```
    ssh azureuser@<vm's-public-ip>
    ```

21. Install Required Python Packages
    ```
    # Install the Python virtual environment tool
        sudo apt update
        sudo apt install python3-venv -y
    
    # Create the new virtual environment (named "env")
        python3 -m venv ~/env
    
    # Activate the virtual environment
        source ~/env/bin/activate
    
    # Install the necessary Azure SDK libraries
        pip install azure-storage-blob azure-eventhub
    ```

22. In the Azure portal, navigate to the Event Hub namespace `nautilus-namespace`
 
23. Under Settings, select Shared access policies → RootManageSharedAccessKey, and copy the Connection string–primary key.

<img width="1365" height="467" alt="Screenshot 2026-03-26 153734" src="https://github.com/user-attachments/assets/88534294-7aef-40b4-a8ac-18614ab51ee1" />


24. In the Azure portal, navigate to the Storage Account `nautilusst1338`

25. Under Security +  Networking > Access Keys, copy the connection string (key1)

<img width="1204" height="385" alt="Screenshot 2026-03-26 154025" src="https://github.com/user-attachments/assets/bd618b80-9203-4693-87bb-2b7794a4ccc1" />


26. Update `send_logs.py` script to send logs to Event Hub + Blob Storage
    ```
    # Open the Script
    vi send_logs.py
    
    # edit the event_hub_conn_str and blob_conn_str
    event_hub_conn_str = "Event Hub Connection String"
    event_hub_name = "nautilus-hub"
    
    # Blob config
    blob_conn_str = "Blob Storage Connection String"
    container_name = "nautilus-backup-29309"
    ```

27. Run the Script, repeat it multiple times
    ```
    python3 send_logs.py
    ```
    > You should see, "Log sent to Event Hub and backed up to Blob Storage"

28. In the Azure portal, navigate to the Storage Account `nautilusst1338` > Containers `nautilus-backup-29309`

29. Verify log files exist

<img width="682" height="292" alt="Screenshot 2026-03-26 160119" src="https://github.com/user-attachments/assets/37a47b8d-0e61-49a8-8dd8-c956c75b9be3" />

