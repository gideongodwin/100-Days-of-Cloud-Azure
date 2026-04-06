## Day 21 - Assigning Public IP to Virtual Machines

## Task Details

The Nautilus DevOps Team has received a new request from the Development Team to set up a new Azure Virtual Machine (VM). This VM will be used to host a new application that requires a stable public IP address. To ensure that the VM has a consistent public IP, a Static Public IP address needs to be associated with it. The VM will be named `devops-vm` and the Static Public IP will be named `devops-pip`
This setup will help the Development Team to have a reliable and consistent access point for their application.

- Create an Azure VM named `devops-vm` using any available Ubuntu image, with the VM size `Standard_B1s`

- Generate an SSH public key on the `azure-client` host and associate it with the VM for SSH access

- Associate a Static Public IP address named `devops-pip` with this VM

- Ensure the VM is accessible via SSH using the generated public key

## STEPS

1. Sign in to the [Azure Portal](https://portal.azure.com/)

2. Select the "Virtual Machines" from the Azure portal  

3. From the Virtual Machines page > Create VM

   <img width="683" height="246" alt="552697394-dc9877bf-7bad-47f4-bbb6-bee818569e71" src="https://github.com/user-attachments/assets/099750e8-697f-4ae5-a31f-8fa66bba01ee" />

4. On the Basics tab, enter the VM name, and choose the appropriate region

   <img width="583" height="371" alt="549899526-cc122b0d-9f58-4023-9688-e86c491d5877" src="https://github.com/user-attachments/assets/5b66223b-a910-418c-b04e-213b11f2db54" />

5. Select the `Standard_B1s` vm size

   <img width="604" height="199" alt="549899697-e0d116d0-a686-440c-8e92-f82c749eef53" src="https://github.com/user-attachments/assets/8d38d1d9-9d68-4949-af30-ddf125aea862" />
 
6. In the Azure CLI, run the following command to create an SSH key:
    ```
    ssh-keygen
    ```

7. Copy the contents of the public key and paste
    ```
    cat .ssh/id_rsa.pub
    ```
    <img width="656" height="318" alt="549899917-12e78e19-e2cf-4011-81d3-6082970a8ecd" src="https://github.com/user-attachments/assets/a8fce56d-575f-4e27-b96a-8413d552fd69" />

8. On the Disks tab, select the appropriate Disk type and configure the required Disk size (GiB) as needed

   <img width="657" height="250" alt="549901144-62457e21-a650-415c-80e8-668008f9ce29" src="https://github.com/user-attachments/assets/bf101db6-be6e-434d-a816-04018253f538" />
 
9. On the Networking tab, under Public IP, select Create new, then provide the required details to configure the new public IP address.

   <img width="674" height="568" alt="549901523-7f1c8bd4-c765-4024-be73-a740e97520e9" src="https://github.com/user-attachments/assets/fa690db4-6049-4579-a15b-93b2cdbbc293" />

10. Review + Create




