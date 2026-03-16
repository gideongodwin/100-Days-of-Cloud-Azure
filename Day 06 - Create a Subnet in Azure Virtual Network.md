## Day 6: Create a Subnet in Azure Virtual Network

#### Task Details:
The Nautilus DevOps team is strategizing the migration of a portion of their infrastructure to the Azure cloud. Recognizing the scale of this undertaking, they have opted to approach the migration in incremental steps rather than as a single massive transition.
- Create a Virtual Network (VNet) named `devops-vnet` and one subnet named `devops-subnet` within the VNet in the `East US` region. Make sure the IPv4 address range is `10.0.0.0/16`

#### STEPS:

1. Sign in to the [Azure Portal](https://portal.azure.com/)

2. Use the global search bar to search for “Virtual network.” From the results, select “Virtual network.”

<img width="1151" height="425" alt="537214353-e8979721-e595-445d-b990-ff309837bbcc" src="https://github.com/user-attachments/assets/f4a680b8-56c0-4bbb-938d-9f0676b5b05d" />

3. From the Virtual Network dashboard, click on create button

<img width="957" height="875" alt="537295738-ae06d70b-3cd2-4400-9dc7-39d15429cd81" src="https://github.com/user-attachments/assets/48ed7850-0d4c-4e7a-8543-b19386d21a0d" />
 
4.On the Basics tab, Enter the VM name and select the appropriate region.

<img width="679" height="498" alt="537734538-091b9b36-5a4d-49a3-82c4-68b1aec6ef74" src="https://github.com/user-attachments/assets/d89f26e4-212e-4121-8c8d-0cca5c5874b6" />
 
5. On the IP address tab, click Next, update the default subnet name to devops-subnet, and then select Save

<img width="678" height="602" alt="Screenshot 2026-01-19 141458" src="https://github.com/user-attachments/assets/d67555b3-977a-4767-b542-f3bf8464f10f" />

6. Then, select Create to complete the process

<img width="683" height="599" alt="Screenshot 2026-01-19 141555" src="https://github.com/user-attachments/assets/aba691cc-2981-4aa6-b3ea-5e075523d1a2" />

