## Day 15: Create and Configure Network Security Group (NSG) in Azure

#### Task Details:
The Nautilus DevOps team is strategizing the migration of a portion of their infrastructure to the Azure cloud. Recognizing the scale of this undertaking, they have opted to approach the migration in incremental steps rather than as a single massive transition. To achieve this, they have segmented large tasks into smaller, more manageable units. This granular approach enables the team to execute the migration in gradual phases, ensuring smoother implementation and minimizing disruption to ongoing operations. By breaking down the migration into smaller tasks, the Nautilus DevOps team can systematically progress through each stage, allowing for better control, risk mitigation, and optimization of resources throughout the migration process.

For this task, create a network security group (NSG) with the following requirements:

- Name of the NSG should be `devops-nsg`

- Add an inbound security rule named `Allow-HTTP` for `HTTP` service on port `80`, with the source CIDR range of `0.0.0.0/0`

- Add another inbound security rule named `Allow-SSH` for `SSH` service on port `22`, with the source CIDR range of `0.0.0.0/0`

## Steps:

1. Sign in to the [Azure Portal](https://portal.azure.com/)

2. Search for and select "Network Security Group" in the azure portal search bar.

    <img width="754" height="250" alt="546680576-a995f64e-008d-4775-ad88-8e19a033127a" src="https://github.com/user-attachments/assets/1b366f97-8bc4-4617-9a84-1848ba866465" />

3. Then click on create

    <img width="955" height="421" alt="546680775-1897918c-8711-4a6a-a5aa-060797c11fa9" src="https://github.com/user-attachments/assets/495f63d9-354b-4ad9-a4d0-9897dc35bbe1" />
 
4. On the Basics tab, select the existing resource group and enter a name for the NSG

    <img width="791" height="310" alt="546680997-9cd0ff5f-873c-4ef3-ad93-8506fd5b7d95" src="https://github.com/user-attachments/assets/1958d920-57b5-4bf0-a8ce-83f0ec3e2813" />

5.  Review + Create.

6. From the NSG > Settings > Inbound security rules > + Add

7. Configure the rule with the following values:

    <img width="939" height="755" alt="546682076-e07ad8bb-c2ca-426c-82de-4ef6e15cc677" src="https://github.com/user-attachments/assets/b292ca35-b1f9-4dbd-b837-9dc0fe8054e4" />
    
    <img width="928" height="307" alt="546683242-7d683195-9cc9-41de-a95e-bde107288606" src="https://github.com/user-attachments/assets/233684ee-1d6a-49ad-bed6-0a84d90eac5d" />

8. Select Add to create the rule.

9. Select Add inbound security rule again and configure the rule with the following values:

    <img width="927" height="825" alt="546683339-acc804b7-94cc-4a6a-83ba-0b7c7a5e0896" src="https://github.com/user-attachments/assets/5dde3a5f-3530-4c9c-94b9-68c76718bacb" />
    
    <img width="935" height="305" alt="546683482-4dab0b32-1127-49b3-a3ff-336fe5b03c97" src="https://github.com/user-attachments/assets/a6542e36-8158-49a7-8a43-965a73233e42" />

10. Select Add to create the rule.



