## Day 50 - VM Setup and Configuration for Azure Application Gateway

## Task Details:
The Nautilus DevOps team needs to set up an Azure Application Gateway to manage traffic for a backend pool of virtual machines. The gateway will serve as a load balancer, distributing traffic across the VMs.

Task:
1) Azure Virtual Network and Subnet:

    - Create a Virtual Network (VNet) named devops-vnet in the East US region.
    - Create a Subnet named devops-subnet within the VNet for the VMs.
    - Create a Subnet named devops-apgw-subnet within the VNet for the Application Gateway.

2) Azure Virtual Machines:

    - Create two VMs named devops-vm1 and devops-vm2 in the East US region.
    - Install Nginx on both VMs.
    - Configure index.html on VM1 to display "Welcome to KKE Labs:Version 1".
    - Configure index.html on VM2 to display "Welcome to KKE Labs:Version 2".

3) Azure Application Gateway:

    - Create an Application Gateway named devops-apgw in the East US region.
    - Assign the devops-apgw-subnet to the Application Gateway.
    - Create a frontend IP configuration named devops-apgw-ip.
    - Add the VMs devops-vm1 and devops-vm2 to the backend pool.
    - Configure a basic routing rule to distribute traffic between the VMs.

4) Validation:

    - Verify that the Application Gateway distributes traffic to both VMs.
    - Ensure that accessing the Application Gateway URL displays either "Welcome to KKE Labs:Version 1" or "Welcome to KKE Labs:Version 2" depending on the load balancing.

## Steps:
