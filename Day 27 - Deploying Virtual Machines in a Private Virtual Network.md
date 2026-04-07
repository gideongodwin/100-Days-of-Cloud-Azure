## Day 27 Deploying Virtual Machines in a Private Virtual Network

## Task Details 

The Nautilus DevOps team is expanding their Azure infrastructure and requires the setup of a private Virtual Network (VNet) along with a subnet. This VNet and subnet configuration will ensure that resources deployed within them remain isolated from external networks and can only communicate within the VNet. Additionally, the team needs to provision a Virtual Machine (VM) under the newly created private VNet. 
This VM should be accessible over SSH from within the VNet only, allowing for secure communication and resource management within the Azure environment.

The name of the VNet must be `nautilus-priv-vnet`

- Create a subnet named nautilus-`priv-subnet` under the same. Further, create a Virtual Machine named `nautilus-priv-vm` under this VNet

- Additionally, create a Network Security Group (NSG) named `nautilus-priv-nsg` and ensure that the NSG rules for the VM allow access only from within the VNet's CIDR block

- Ensure all resources are created in the `Central US` region

## STEPS

1. Sign in to the [Azure Portal](https://portal.azure.com/) 

2. Search for and select "Virtual Network" in the azure portal search bar.

3. On the Virtual Network page, click on create

    <img width="578" height="232" alt="Screenshot 2026-02-24 094524" src="https://github.com/user-attachments/assets/f332f62d-726e-46c3-96fe-93bef0af0d91" />

4. On the Basics tab, configure the following

    <img width="605" height="411" alt="554047238-65d20b5f-102b-4fd3-a28f-df4f85166dc1" src="https://github.com/user-attachments/assets/1f6d0365-1618-4ae8-8393-e90845806b53" />

5. On the IP addresses tab, select + Add subnet. In the Add subnet pane, enter a name for the subnet, and then enable Private subnet.

<img width="678" height="234" alt="Screenshot 2026-02-24 094824" src="https://github.com/user-attachments/assets/695d1749-e203-48a6-afe8-5be33791eb42" />

6. Review + Create

7. Search for and select "Virtual Machines" in the azure portal search bar.

<img width="633" height="238" alt="Screenshot 2026-02-24 095244" src="https://github.com/user-attachments/assets/1f51aef4-bb64-4aed-911a-eda1ad68b8cc" />

8. Create the vm

<img width="678" height="263" alt="Screenshot 2026-02-24 095333" src="https://github.com/user-attachments/assets/6649e652-5ce1-4ed1-bb9f-0d97de1224e8" />

9. On the Basics tab, configure the following:

<img width="590" height="290" alt="554067274-f8d092c0-3220-4c26-850e-621433f049e9" src="https://github.com/user-attachments/assets/4d1cf22b-3534-4441-8e91-d68c75e51f20" />

10. On the Networking tab, create a new Network security group

  <img width="680" height="428" alt="Screenshot 2026-02-24 100630" src="https://github.com/user-attachments/assets/254d0795-6100-4e15-a341-47aefc1547da" />

11.In the left-hand menu of the NSG, under Settings, select Inbound security rules

12. Click + Add

13. Configure the rule to allow `SSH` only from the VNet's CIDR block:
    ```
    Source: IP Addresses.
    
    Source IP addresses/CIDR ranges: 10.0.0.0/16
    
    Destination port ranges: 22
    
    Protocol: TCP
    
    Action: Allow
    
    Priority: 100
    
    Name: Allow-SSH-From-VNet.
    ```

14. Click Add

15. Review + Create


