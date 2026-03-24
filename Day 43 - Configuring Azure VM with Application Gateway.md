## Day 43 - Configuring Azure VM with Application Gateway

## Task Details:
The Nautilus Development Team needs to set up a new Azure Virtual Machine (VM) and configure it to run a web server. This VM should be part of an Azure Application Gateway (AGW) setup to ensure high availability and better traffic management. The task involves creating a VM, setting up an AGW, configuring a backend pool, and ensuring the web server is accessible via the AGW public IP.

- Create a Network Security Group (NSG):
  > Create an NSG named `datacenter-nsg`
  > Add an inbound security rule `Allow-HTTP` to allow `TCP` traffic on port `80`

- Create a Virtual Machine:
  > Create a VM named `datacenter-vm` using any available Ubuntu image. Configure the instance with the following settings:
  
  > Size: Choose a lightweight VM size (e.g., `Standard_B1s`).

   > Authentication: Use `SSH public key` authentication. (Please select `use existing public key` option, create public-key locally and paste contents of `~/.ssh/id_rsa.pub`)

- OS Disk: Use a `Standard HDD`

- Networking: Under the Advanced section, attach an existing NSG (e.g., `datacenter-nsg`).

- Additionally, configure the instance to run a user data script during launch that:
  > Install the Nginx package.
  > Start the Nginx service.

- Set up an Application Gateway: Set up an Azure Application Gateway named `datacenter-agw` with the following:
  > Create and Associate it with a public IP address named `datacenter-agw-ip`
  > Attach the backend pool:`datacenter-backendpool` to the VM `datacenter-vm`
  > Select a subnet for the Application Gateway (you can create a new one if needed).
  > Configure HTTP Settings: Create an HTTP setting named `datacenter-http-settings` on port `80`

- Route Traffic: Add a listener named `datacenter-listener` and a routing rule named `datacenter-routing-rule` to route traffic from the AGW frontend to the backend pool:
  > Listener: Frontend IP = public IP, Frontend port = 80, Protocol = HTTP
  > Routing rule: Connects `datacenter-listener` to `datacenter-backendpool` using `datacenter-http-settings`

- NSG Adjustments: Make sure the NSG attached to the VM allows inbound TCP traffic on port 80, so the Nginx server running on `datacenter-vm` is accessible via the Application Gateway public IP.

Note: Wait for the Application Gateway resource to be fully deployed before proceeding with the next steps. Deployment may take several minutes to complete.

## Steps:

1. Sign in to the [Azure Portal](https://portal.azure.com/)
2. Search for and select Network security groups in the azure portal search bar
3. Select + Create

<img width="751" height="188" alt="Screenshot 2026-03-21 122516" src="https://github.com/user-attachments/assets/1afe7ac5-35ce-433c-99ab-19c2b0ab46f4" />

4. On the Basics tab of the Create network security group page, enter these values:

<img width="780" height="401" alt="Screenshot 2026-03-23 195821" src="https://github.com/user-attachments/assets/f8566b5e-56bd-498d-bfcf-a6ede441e7f9" />

5. Select Review + create, then Create

6. Click on `go to resource` or open `datacenter-nsg`.
7. Select Inbound security rules, then + Add
8. Configure the following:

<img width="902" height="787" alt="Screenshot 2026-03-23 200001" src="https://github.com/user-attachments/assets/b88f6042-2cb6-4916-8302-8d2185cb64ea" />

9. Select Add
10. Search for and select Virtual Machines in the azure portal search bar
11. Select + Create
<img width="742" height="379" alt="Screenshot 2026-03-21 123239" src="https://github.com/user-attachments/assets/50f523b6-ef91-4284-b254-795ae60739ca" />

12. On the Basics tab of the Create virtual network page, enter the VM name and select the appropriate region.

<img width="778" height="575" alt="Screenshot 2026-03-23 200807" src="https://github.com/user-attachments/assets/24e22c5b-8bf2-4f95-82fd-721643bb8c59" />
<img width="780" height="103" alt="Screenshot 2026-03-s21 123609" src="https://github.com/user-attachments/assets/a28e2b94-5156-456d-8100-12a21fb4a766" />

13. In the Azure CLI, run the following command to create an SSH key:
    ```
    ssh-keygen
    ```

14. Copy the contents of the public key and paste
    ```
    cat .ssh/id_rsa.pub
    ```
<img width="780" height="432" alt="Screenshot 20fd6-03-21 123609" src="https://github.com/user-attachments/assets/be8206ee-214f-4cc8-8797-7b6d80877cd0" />

15. Select the disk size and type.

<img width="790" height="295" alt="Screenshot 2026-03-23 200914" src="https://github.com/user-attachments/assets/24f93921-e9ed-429f-a05d-d1f50ecadac4" />

16. On the Networking tab, under Advanced, select `datacenter-nsg`

<img width="771" height="506" alt="Screenshot 2026-03-23 200947" src="https://github.com/user-attachments/assets/1c2f6d13-66a8-4419-a0f5-9f0b89ae82c5" />

17. On the Advanced tab, under Custom data, paste the bash script to install and start Nginx automatically
    ```
    #!/bin/bash
         sudo apt-get update
         sudo apt-get install -y nginx
         sudo systemctl start nginx
         sudo systemctl enable nginx
    ```

18. Select Review + create, then Create
 
19. From the Virtual network dashboard, select the existing virtual network `datacenter-vm-vnet`

<img width="878" height="325" alt="Screenshot 2026-03-23 201536" src="https://github.com/user-attachments/assets/ae67e850-52d7-41f2-8572-ac7dbdd9813d" />

20. Add a new subnet for the Application Gateway.

<img width="729" height="198" alt="Screenshot 2026-03-23 201636" src="https://github.com/user-attachments/assets/e59463f0-09b8-43b5-b63c-3d61227c44a5" />

<img width="896" height="830" alt="Screenshot 2026-03-23 201730" src="https://github.com/user-attachments/assets/d8221f43-6e47-4bf6-ae5d-7a6d1680c734" />

21. Search for and select Application Gateway in the azure portal search bar

<img width="736" height="272" alt="Screenshot 2026-03-23 201828" src="https://github.com/user-attachments/assets/9c52e4fe-7657-4af6-ac3b-cb854d5568bc" />

22. Select + Create
23. On the Basics tab, configure the following:

<img width="771" height="802" alt="Screenshot 2026-03-23 202009" src="https://github.com/user-attachments/assets/34a491a4-7a25-4ae2-96a0-79dc6f52e586" />

24. On the Frontends tab, add a new public ip `datacenter-agw-ip`

<img width="760" height="494" alt="Screenshot 2026-03-23 202050" src="https://github.com/user-attachments/assets/0213dc4b-5734-42f5-a21d-bffffedaaef0" />

25. On the Backends tab, select Add a backend pool.
26. In the Add a backend pool window, enter the following:

<img width="916" height="797" alt="Screenshot 2026-03-23 202219" src="https://github.com/user-attachments/assets/b7ab9dad-5dde-46a7-a8e8-5909f74ade95" />

27. On the configuration tab, add a routing rule

<img width="888" height="444" alt="Screenshot 2026-03-23 202242" src="https://github.com/user-attachments/assets/394015c0-25be-4347-bffb-5a85fc301bde" />

28. On the Listener tab, enter the following:

<img width="902" height="544" alt="Screenshot 2026-03-23 202507" src="https://github.com/user-attachments/assets/1b4befce-70dc-45fc-88bd-70c62e87b144" />

30. On the Backend targets tab, enter the following:

<img width="919" height="469" alt="Screenshot 2026-03-23 202651" src="https://github.com/user-attachments/assets/7c7fe19c-91d2-4b4d-ad8e-b4320fd622f9" />

31. Select Review + create, then Create

32. Navigate to the `datacenter-agw` resource
33. Locate the `Frontend public IP address` on the Overview page.
34. Copy that IP address and paste it into a new web browser tab.
35. You should see the default `"Welcome to nginx!` page, confirming that the Application Gateway is successfully routing traffic to your backend VM.













