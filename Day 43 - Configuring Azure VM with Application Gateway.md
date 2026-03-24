## Day 43 - Configuring Azure VM with Application Gateway

## Task Details:
The Nautilus Development Team needs to set up a new Azure Virtual Machine (VM) and configure it to run a web server. This VM should be part of an Azure Application Gateway (AGW) setup to ensure high availability and better traffic management. The task involves creating a VM, setting up an AGW, configuring a backend pool, and ensuring the web server is accessible via the AGW public IP.

- Create a Network Security Group (NSG): Create an NSG named `datacenter-nsg` and add an inbound security rule `Allow-HTTP` to allow `TCP` traffic on port `80`

- Create a Virtual Machine: Create a VM named `datacenter-vm` using any available Ubuntu image. Configure the instance with the following settings:
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

14. Copy the output
```
cat .ssh/id_rsa.pub
```





