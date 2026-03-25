## Day 45: Azure Kubernetes Service (AKS) Setup and Management

## Task Details:

The Nautilus DevOps team is tasked with preparing an AKS cluster to deploy a Kubernetes-based application. The team has the following requirements:

- Create an AKS cluster named `devops-aks`
  > The Kubernetes version must be `1.33.0`
  
  > Ensure the cluster is created in the `Central US` region

- Edit the `agentpool` Node pools (delete all other node pool if exists) and configure the cluster with the following properties:

  > Node size: `D2s v3`
  
  > Minimum node count: 1
  
  > Maximum node count: 2

- The AKS cluster endpoint access must be `private`

- Disable the `Container Insights` for now and disable all kind of monitoring as well.

The AKS cluster must be configured with high availability and private endpoint access. Verify that the cluster meets the requirements and is ready for workloads.


## Steps:

1. Sign in to the [Azure Portal](https://portal.azure.com/)

<img width="573" height="223" alt="Screenshot 2026-03-25 114601" src="https://github.com/user-attachments/assets/35fd5e05-be1b-4af2-a5d8-971251076fa6" />

2. From the Kubernetes dashboard, click on create.

<img width="656" height="286" alt="Screenshot 2026-03-25 114635" src="https://github.com/user-attachments/assets/fadd45ec-734a-43ae-9359-013cec3bbd05" />

3. On the basics tab, configure the following:

<img width="563" height="393" alt="Screenshot 2026-03-25 114727" src="https://github.com/user-attachments/assets/a60a0826-be16-48c2-bfc7-370621d44fd8" />

<img width="568" height="143" alt="Screenshot 2026-03-25 114734" src="https://github.com/user-attachments/assets/2a038c97-2138-40aa-b899-1a9a174caeee" />

4. On the node pools tab, delete other node pools except `agentpool`

<img width="567" height="232" alt="Screenshot 2026-03-25 114746" src="https://github.com/user-attachments/assets/be77a04b-567e-4928-9976-dd020274f076" />

5. Edit the `agentpool`, configure the following:

<img width="578" height="325" alt="Screenshot 2026-03-25 114855" src="https://github.com/user-attachments/assets/ed0bbf73-0170-40bd-9bd9-314a1b624939" />

6. On the Networking tab, set cluster access to private

<img width="597" height="247" alt="Screenshot 2026-03-25 114921" src="https://github.com/user-attachments/assets/f8bc5690-f463-4300-a63c-00ed74eee0b9" />

7. On the Monitoring tab, disable all kind of monitoring

<img width="546" height="352" alt="Screenshot 2026-03-25 114948" src="https://github.com/user-attachments/assets/a0e3204d-8528-487b-b04d-40b2d6b063ca" />





