## Day 28: Troubleshooting Public Virtual Network Configurations

#### Task Details 
The Nautilus DevOps Team deployed an Nginx server on an Azure VM in a public VNet named `xfusion-vnet` However, the server is still inaccessible from the internet.
As a DevOps team member, complete the following tasks:
- Verify VNet Configuration: Ensure `xfusion-vnet` allows internet access.
- Attach Public IP: A public IP named `xfusion-pip` already exists. Attach this public IP to the VM `xfusion-vm` to make it accessible from the internet.
- Ensure Accessibility: Confirm the VM `xfusion-vm` is accessible on `port 80`

#### STEPS
Step 1. Sign in to the [Azure Portal](https://portal.azure.com/) \
Step 2. Verify VNet Configuration
- In the resource group, select the route table resource

<img width="675" height="366" alt="Screenshot 2026-02-26 132301" src="https://github.com/user-attachments/assets/fa25bec1-5445-43a6-8ebc-9da49fc92cb8" />

- Under Settings, select Routes, select the `Block-Internet` route, and then select Delete

<img width="670" height="368" alt="Screenshot 2026-02-26 132406" src="https://github.com/user-attachments/assets/98bc314b-12ff-4643-a50f-06554de24e47" />

- Select Add, and then create a new route named Allow-Internet with the following settings:

<img width="679" height="596" alt="Screenshot 2026-02-26 132528" src="https://github.com/user-attachments/assets/aa71f530-a5b1-49f6-a524-f363106afc94" />

Step 3: Configure Inbound Security Rules

- Select the NSG resource, and then under Settings, select Inbound security rules > Add.

<img width="678" height="466" alt="Screenshot 2026-02-26 130407" src="https://github.com/user-attachments/assets/c0c6ee2c-35cb-4de9-b22f-2c0535ef0272" />

<img width="681" height="583" alt="Screenshot 2026-02-26 130603" src="https://github.com/user-attachments/assets/ca6816b7-7f0b-4b28-ba79-d6738cb64ccd" />

Step 4: Attach the Public IP Address to the VM

- In the resource group, select the public IP address resource

<img width="675" height="342" alt="Screenshot 2026-02-26 130702" src="https://github.com/user-attachments/assets/fcfcd893-42e5-4f2e-b5ec-de4e4fceb0bc" />

- Under Settings, select IP configurations, and then associate the public IP address with the network interface of the virtual machine

<img width="548" height="288" alt="Screenshot 2026-02-26 130739" src="https://github.com/user-attachments/assets/b76297d7-70eb-4efe-b208-36545a96081b" />
<img width="678" height="263" alt="Screenshot 2026-02-26 132154" src="https://github.com/user-attachments/assets/909025b7-f779-498e-b183-3f46be808f62" />

Step 5: Install and Verify Nginx on the VM

```
ssh azureuser@<public-ip>
sudo apt install nginx -y
systemctl status nginx
exit
```

Step 6: Confirm Internet Accessibility on Port 80
- Run the following command to verify that xfusion-vm is accessible from the internet on port 80. Replace <public-ip> with the public IP address of xfusion-vm.

  `curl -Ik <public-ip>` \
  
- Confirm that the response returns `HTTP/1.1 200 OK` indicating that the Nginx server is accessible from the internet.

  






