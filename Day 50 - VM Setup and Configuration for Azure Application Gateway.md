<img width="629" height="145" alt="Screenshot 2026-04-01 144450" src="https://github.com/user-attachments/assets/950a36da-0165-4970-b2cb-9d34759ad878" /><img width="736" height="272" alt="568640628-9c52e4fe-7657-4af6-ac3b-cb854d5568bc" src="https://github.com/user-attachments/assets/ec9b27c4-5842-40a4-aae1-00e1eb9b8fce" />## Day 50 - VM Setup and Configuration for Azure Application Gateway

## Task Details:

The Nautilus DevOps team needs to set up an Azure Application Gateway to manage traffic for a backend pool of virtual machines. The gateway will serve as a load balancer, distributing traffic across the VMs.

Task:
1) Azure Virtual Network and Subnet:

    - Create a Virtual Network (VNet) named `devops-vnet` in the East US region.
    - Create a Subnet named `devops-subnet` within the VNet for the VMs.
    - Create a Subnet named `devops-apgw-subnet` within the VNet for the Application Gateway.

2) Azure Virtual Machines:

    - Create two VMs named `devops-vm1` and `devops-vm2` in the East US region.
    - Install `Nginx` on both VMs
    - Configure `index.html` on VM1 to display "Welcome to KKE Labs:Version 1".
    - Configure `index.html` on VM2 to display "Welcome to KKE Labs:Version 2".

3) Azure Application Gateway:

    - Create an Application Gateway named `devops-apgw` in the East US region.
    - Assign the `devops-apgw-subnet` to the Application Gateway.
    - Create a frontend IP configuration named `devops-apgw-ip`
    - Add the VMs `devops-vm1` and `devops-vm2` to the backend pool.
    - Configure a basic routing rule to distribute traffic between the VMs.

4) Validation:

    - Verify that the Application Gateway distributes traffic to both VMs.
    - Ensure that accessing the Application Gateway URL displays either "Welcome to KKE Labs:Version 1" or "Welcome to KKE Labs:Version 2" depending on the load balancing.

## Steps:

1. Sign in to the [Azure Portal](https://portal.azure.com/) 

2. Search for and select “Virtual network” in the azure portal search bar

3. From the Virtual Network dashboard, click on create button

    <img width="547" height="221" alt="572104580-1faa5baf-f8a3-4b10-beed-4a78af9e05d5" src="https://github.com/user-attachments/assets/ca42050a-54a2-49a9-88ed-3369f1e49368" />

4. On the Basics tab, configure the following;

    <img width="579" height="291" alt="Screenshot 2026-04-01 143236" src="https://github.com/user-attachments/assets/fd36cd55-877b-4fd3-bfda-266ae7401276" />

5. On the IP addresses tab, add the `devops-subnet` and `devops-apgw-subnet`

    <img width="633" height="341" alt="Screenshot 2026-04-01 143318" src="https://github.com/user-attachments/assets/a8d36272-5aad-4ee6-a2e4-8ca4be48d1b6" />
    
    <img width="639" height="342" alt="Screenshot 2026-04-01 143341" src="https://github.com/user-attachments/assets/97e3847a-2e9b-43ce-9254-7308158f4014" />
    
    <img width="587" height="412" alt="Screenshot 2026-04-01 143347" src="https://github.com/user-attachments/assets/60a09bcc-dab0-4ff1-9fea-27bc18d1e3fa" />

6.  Review + Create

7. From the Azure portal dashboard, select and createthe first vm `devops-vm1`.

8. On the Basics tab, select the existing resource group, and enter the following
    
    <img width="596" height="404" alt="Screenshot 2026-04-01 143714" src="https://github.com/user-attachments/assets/01dcc63e-28eb-4f1a-a545-f8e5753250de" />
 
9. In the Azure CLI, run the following command to create an SSH key:
    ```
    ssh-keygen
    ```

10. Copy the contents of the public key and paste
    ```
    cat .ssh/id_rsa.pub
    ```  
    <img width="604" height="371" alt="Screenshot 2026-04-01 143729" src="https://github.com/user-attachments/assets/fecf0adb-59ec-43f8-8c9f-a2b5080bbfcc" />

11. On the Networking tab, configure the following:
    
    <img width="592" height="424" alt="Screenshot 2026-04-01 143825" src="https://github.com/user-attachments/assets/8c83c44f-cc84-4d6c-91a2-9ca3070f6086" />

12. On the Monitoring tab > Custom data field > Paste the bash script to update the system and install Nginx
    ```
    #!/bin/bash
    
    sudo apt-get update -y
    sudo apt-get install nginx -y
    echo "Welcome to KKE Labs: Version 1" | sudo tee /var/www/html/index.html
    sudo systemctl enable nginx
    sudo systemctl restart nginx
    ```

    <img width="617" height="216" alt="Screenshot 2026-04-01 102600" src="https://github.com/user-attachments/assets/e2dda337-6e16-4ca9-bc5f-5bc43f9a0617" />

13. Review + Create

14. Create the second vm `devops-vm2` repaeating steps 8 and 9

15. 10. On the Monitoring tab > custom data field > paste the bash script to update the system and install Nginx
    ```
    #!/bin/bash
    
    sudo apt-get update -y
    sudo apt-get install nginx -y
    echo "Welcome to KKE Labs: Version 2" | sudo tee /var/www/html/index.html
    sudo systemctl enable nginx
    sudo systemctl restart nginx
    ```

16. Review + Create

17. Search for and select Application Gateway in the azure portal search bar

    <img width="736" height="272" alt="568640628-9c52e4fe-7657-4af6-ac3b-cb854d5568bc" src="https://github.com/user-attachments/assets/493f9a91-929f-486a-96e5-f6762dc96f60" />

18. On the Basics tab, configure the following:

    <img width="622" height="437" alt="Screenshot 2026-04-01 144444" src="https://github.com/user-attachments/assets/7aa057f0-3133-4311-bb86-75d340a0121d" />

    <img width="629" height="145" alt="Screenshot 2026-04-01 144450" src="https://github.com/user-attachments/assets/4947eda5-35bc-4e49-9125-3af53aee8dce" />

19. On the Frontends tab, add a new public ip devops-apgw-ip

    <img width="584" height="383" alt="Screenshot 2026-04-01 144531" src="https://github.com/user-attachments/assets/b5d154fc-0630-4844-805e-ce0dd8daeabd" />

20. On the Backends tab, select Add a backend pool.

21. Add the VMs `devops-vm1` and `devops-vm2` to the backend pool.

    <img width="654" height="366" alt="Screenshot 2026-04-01 144622" src="https://github.com/user-attachments/assets/ffc6e94b-2370-438b-b224-50b3656d7059" />

22. On the configuration tab, add a routing rule

    <img width="888" height="444" alt="568647849-394015c0-25be-4347-bffb-5a85fc301bde" src="https://github.com/user-attachments/assets/9e19afb7-2407-4539-8d79-51b1460c38f8" />

23. On the Listener tab, configure the following:

    <img width="624" height="190" alt="Screenshot 2026-04-01 144708" src="https://github.com/user-attachments/assets/d5f4fdb4-3547-4887-a83d-f7b62bc5cc67" />

24. On the Backend targets tab, add backend settings

    <img width="634" height="170" alt="Screenshot 2026-04-01 144746" src="https://github.com/user-attachments/assets/c0364160-332f-418d-9591-33c468ba04cc" />
    
    <img width="654" height="504" alt="Screenshot 2026-04-01 144736" src="https://github.com/user-attachments/assets/34a69f37-a8fc-4636-a010-0bc7e8cd6699" />

25. Review + Create

26. Navigate to the `devops-apgw` resource

27. Locate the Frontend public IP address on the Overview page.

28. Copy that IP address and paste it into a new web browser tab.

    > You should see the default "Welcome to KKE Labs:Version 1" page, confirming that load balancing is working correctly.




