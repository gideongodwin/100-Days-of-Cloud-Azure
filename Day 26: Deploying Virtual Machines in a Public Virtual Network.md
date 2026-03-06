## Day 26: Deploying Virtual Machines in a Public Virtual Network

#### Task Details 
The Nautilus DevOps Team has received a request from the Networking Team to set up a new public-facing services. This VNet will host various resources that need to be accessible over the internet. As part of this setup, you need to ensure the VNet has public subnets with automatic public IP assignment for resources. Additionally, a new VM will be launched within this VNet to host public applications that require SSH access. This setup will enable the Networking Team to deploy and manage public-facing applications.
- Create a public VNet named `datacenter-pub-vnet`, and a subnet named `datacenter-pub-subnet` under the same, make sure public IP is being auto-assigned to resources under this subnet
- Further, create a VM named `datacenter-pub-vm` under this VNet. Make sure SSH `port 22` is open for this instance and accessible over the internet. Use the Azure portal to complete the task and ensure that SSH access is configured correctly.

#### STEPS
1. Sign in to the [Azure Portal](https://portal.azure.com/) 

2. Use the global search bar to search for “Virtual network.” From the results, select “Virtual network.”
3. From the Virtual Network dashboard, click on create button

<img width="593" height="266" alt="Screenshot 2026-02-23 111833" src="https://github.com/user-attachments/assets/ec81721c-2958-4ce1-b637-0cee8279311f" />
<img width="678" height="254" alt="Screenshot 2026-02-23 111905" src="https://github.com/user-attachments/assets/e155f6d2-aec2-42ba-8122-92fe8876e2b2" />

4. On the Basics tab of the Create virtual network page, enter the VM name and select the appropriate region.
 
<img width="681" height="532" alt="Screenshot 2026-02-23 111932" src="https://github.com/user-attachments/assets/79ffcfc2-239f-4d03-ad36-6dd8bdb08d53" />

5. On the IP addresses tab, select Add subnet
<img width="681" height="208" alt="Screenshot 2026-02-23 111957" src="https://github.com/user-attachments/assets/2dfcdea3-115b-48f6-824d-20cc71d9291c" />

6. Enter a name for the subnet.

<img width="681" height="598" alt="Screenshot 2026-02-23 112521" src="https://github.com/user-attachments/assets/eabad531-b36e-402e-b6e4-fa71957fc0f1" />

7. Then, click on create button
<img width="682" height="593" alt="Screenshot 2026-02-23 112104" src="https://github.com/user-attachments/assets/fbc20896-6272-429f-843f-b9534f5f7a85" />

8. Use the global search bar to search for “Virtual machines.” From the results, select “Virtual machines"
9. From the Virtual machines dashboard, click on create button

<img width="574" height="209" alt="Screenshot 2026-02-23 112452" src="https://github.com/user-attachments/assets/dc42d460-31c2-4ac5-959b-e74231019ef5" />
<img width="681" height="268" alt="Screenshot 2026-02-23 112521" src="https://github.com/user-attachments/assets/f5312e06-537c-4625-9783-953d589dda28" />

10. Select the existing resource group, enter the VM name, and choose the region

<img width="663" height="187" alt="Screenshot 2026-02-23 112908" src="https://github.com/user-attachments/assets/ceab9433-93bf-4a00-84fb-8a3c5546160c" />

11. Select Review + Create

<img width="665" height="199" alt="Screenshot 2026-02-23 112940" src="https://github.com/user-attachments/assets/70a36ac8-d7ce-4e04-9f94-71c020b1c1a3" />












 
