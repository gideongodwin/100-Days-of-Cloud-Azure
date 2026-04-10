## Day 35: Configuring Virtual Network Peering

## Task Details:

The Nautilus DevOps team has been tasked with demonstrating the use of VNet Peering to enable communication between two VNets. One VNet will be a private VNet that contains a private Azure VM, while the other will be a public VNet containing a publicly accessible Azure VM.

- Existing Azure Resources:
  - Public VM: `nautilus-pub-vm` is already in the public VNet.
  - Private VNet and VM: `nautilus-priv-vnet` and `nautilus-priv-vm` exist in the private VNet with its subnet: `nautilus-priv-subnet`

- Create VNet Peering:
  - Create a VNet Peering between the Public VNet and Private VNet.
  - VNet Peering Name: `nautilus-pub-to-priv-peering`

- Test the Connection:
  - SSH into the public VM and verify that you can ping the private VM.

## Steps:

1. Sign in to the [Azure Portal](https://portal.azure.com/)

2. Search for and select "Virtual Network" in the azure portal search bar.

    <img width="754" height="300" alt="Screenshot 2026-03-07 112804" src="https://github.com/user-attachments/assets/94702445-3f37-4ab8-bd8c-8e523915ff96" />

3. Select the Public VNet `nautilus-pub-vnet`

    <img width="895" height="433" alt="Screenshot 2026-03-07 112825" src="https://github.com/user-attachments/assets/a7747bc4-d61b-452c-91f9-ea4a04936838" />

4. Under Settings > Peerings, Click `+ Add`

    <img width="739" height="595" alt="559696727-63115636-2297-4d67-a405-d8c167a8c2fc" src="https://github.com/user-attachments/assets/4bc708a7-599a-4008-a535-d53a322952d6" />

5.  Configure the Peering settings:

    <img width="758" height="743" alt="Screenshot 2026-03-07 113021" src="https://github.com/user-attachments/assets/bf2cc26b-a772-4fcf-84b8-e8b0db960583" />
    
    <img width="752" height="496" alt="Screenshot 2026-03-07 113035" src="https://github.com/user-attachments/assets/4171cfcd-fe12-4133-ae47-7c392bcb955f" />

6. Search for and select "Virtual Machines" in the azure portal search bar.

7. Select the `nautilus-pub-vm` and copy its Public IP address

    <img width="858" height="470" alt="Screenshot 2026-03-07 113233" src="https://github.com/user-attachments/assets/07b53ded-dae0-4ca1-bbc7-1d55e44ed150" />

8. In the Azure client, SSH into the Public VM
    ```
    ssh azureuser@<public-vm-ip>
    ```

9. Test connectivity by pinging the Private VM
    ```
    ping <nautilus-priv-vm-private-ip>
    ```







